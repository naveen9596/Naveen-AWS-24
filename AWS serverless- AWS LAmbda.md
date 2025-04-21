Here’s a **simple AWS Serverless Computing demo project** using **AWS Lambda**, **S3**, and **SNS Notification**, perfect for showcasing how serverless works in real-time.

---

### 🎯 **Project Title: "Image Upload Notification System"**

#### **Use Case**:  
When a user uploads an image to an S3 bucket, an AWS Lambda function is triggered, which then sends a notification (email or SMS) via Amazon SNS.

---

### ✅ **Services Used:**
- **Amazon S3** – File storage bucket  
- **AWS Lambda** – Event-driven compute  
- **Amazon SNS** – Sends notification (email or SMS)  
- **IAM** – Permissions

---

## 🛠️ Step-by-Step Guide

---

### **Step 1: Create an SNS Topic**
1. Go to **Amazon SNS > Topics > Create Topic**
2. Choose **Standard**
3. Name: `ImageUploadNotification`
4. Create the topic
5. Click **“Create subscription”**
   - Protocol: **Email** (or SMS)
   - Endpoint: your email (verify your email from your inbox)

---

### **Step 2: Create an S3 Bucket**
1. Go to **Amazon S3 > Create bucket**
2. Bucket name: `image-upload-demo-<yourname>`
3. Uncheck **Block all public access** if you want to access files later publicly (optional)
4. Create bucket

---

### **Step 3: Create a Lambda Function**
1. Go to **Lambda > Create function**
2. Name: `ImageUploadNotifier`
3. Runtime: **Python 3.12** or **Node.js 18.x**
4. Choose or create a new role with **basic Lambda permissions** + access to SNS

---

### **Step 4: Add Lambda Trigger from S3**
1. Go to **S3 > bucket > Properties**
2. Scroll to **Event notifications > Create event notification**
   - Name: `NotifyOnImageUpload`
   - Event type: **PUT**
   - Prefix: (optional) `images/`
   - Destination: **Lambda function**
   - Choose your `ImageUploadNotifier` Lambda

---

### **Step 5: Lambda Function Code**

#### ✅ For Python:
```python
import json
import boto3

def lambda_handler(event, context):
    sns = boto3.client('sns')
    topic_arn = 'arn:aws:sns:REGION:ACCOUNT_ID:ImageUploadNotification'

    # Get bucket name and file key
    bucket = event['Records'][0]['s3']['bucket']['name']
    key = event['Records'][0]['s3']['object']['key']

    message = f"A new file has been uploaded:\nBucket: {bucket}\nKey: {key}"
    
    response = sns.publish(
        TopicArn=topic_arn,
        Message=message,
        Subject='New Image Uploaded to S3'
    )

    return {
        'statusCode': 200,
        'body': json.dumps('Notification sent!')
    }
```

🔁 Replace the `topic_arn` with your actual SNS topic ARN.

---

### **Step 6: Grant Lambda Permission to Use SNS**
- Go to **IAM > Roles > Your Lambda Role**
- Add **SNS Publish** permissions:
  ```json
  {
    "Effect": "Allow",
    "Action": "sns:Publish",
    "Resource": "arn:aws:sns:REGION:ACCOUNT_ID:ImageUploadNotification"
  }
  ```

---

### **Step 7: Test the Flow**
1. Upload an image to the S3 bucket (e.g., via console or CLI)
2. Within seconds, you’ll get an **email or SMS** saying:
   > “A new file has been uploaded to S3: Bucket: image-upload-demo-name, Key: image.jpg”

---

### 🧾 **Extras for Your Demo**
- Use **CloudWatch Logs** to show Lambda execution logs.
- Add a prefix filter (e.g., only trigger on `images/` folder).
- Time permitting: extend it to send file metadata.

---

Want me to give you a CloudFormation or Terraform script to automate all this?
