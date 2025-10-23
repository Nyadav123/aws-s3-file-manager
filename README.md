🗂️ AWS S3 File Manager

A lightweight and secure web-based file manager built using AWS Lambda, API Gateway, and S3 — allowing users to upload, download, delete, and create folders in an S3 bucket via a simple HTML interface.

## 🚀 Features
- 🔐 Basic Authentication using AWS Secrets Manager
- ☁️ Fully Serverless – AWS Lambda + API Gateway + S3
- 📤 Upload and create folders directly from the browser
- 📥 Download individual files
- 🗑 Delete files easily from dropdown selection
- 🧾 Real-time file list from S3
- 💡 Simple HTML + JavaScript frontend — no frameworks needed

## 🏗️ Architecture Overview
Frontend (index.html)
|
▼
AWS CloudFront → API Gateway (with API Key) ←→ AWS Lambda (Python)
|
▼
AWS S3 Bucket

pgsql
Copy code

- Frontend: HTML/CSS/JS
- Backend: Python (boto3 for AWS)
- Authentication: AWS Secrets Manager (Basic Auth)

## 🔧 Backend Setup (Lambda)
1. Create an S3 bucket (e.g., `credit-websites-hosting`)
2. Create a secret in AWS Secrets Manager (example JSON):
```json
{
  "admin": { "password": "Admin@123", "root_folder": "" },
  "user1": { "password": "User@123", "root_folder": "" }
}
Deploy the Python backend Lambda function (use provided backend code)

Create an API Gateway with routes:

/list (GET)

/list-files (GET)

/put (PUT)

/get (GET)

/delete (DELETE)

/download-folder (GET)

/delete-folder (DELETE)

Enable CORS on all endpoints

🖥️ Frontend Setup
Upload index.html to S3

Configure CloudFront behavior:

Route /submit path to API Gateway

Inject API key via CloudFront headers

Open the CloudFront domain in browser

Login using credentials stored in AWS Secrets Manager

🧰 Example Credentials
Username	Password
admin	Admin@123
user1	User@123

🧪 Example Workflow
Login with your credentials

Upload files to S3

List & Download available files

Delete unwanted files

Create folders inside your bucket

🧱 Tech Stack
Component	Technology
Frontend	HTML, CSS, Vanilla JS
Backend	AWS Lambda (Python 3.x)
Storage	AWS S3
Secrets	AWS Secrets Manager
API Layer	AWS API Gateway

🛡️ Security
Credentials stored securely in AWS Secrets Manager

Basic Auth over HTTPS

Optional folder isolation via root_folder in secrets


📸 Screenshots

<img width="1920" height="913" alt="s3" src="https://github.com/user-attachments/assets/4e3d858f-f811-4c3c-9b85-2b63a4004386" />



🧑‍💻 Author
Nipun Yadav 💼 DevOps & Cloud Engineer
🌐 [LinkedIn](https://www.linkedin.com/in/nipun-yadav-5bb736178/) | [GitHub](https://github.com/Nyadav123)

📄 License
MIT License — feel free to use and modify

✅ Future Enhancements
Multi-user folder isolation

Drag-and-drop file uploads

File preview support

Pagination for large buckets
