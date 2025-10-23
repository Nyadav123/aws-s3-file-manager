🗂️ AWS S3 File Manager

A lightweight and secure web-based file manager built using AWS Lambda, API Gateway, and S3 — allowing users to upload, download, delete, and create folders in an S3 bucket via a simple HTML interface.

---

🚀 Features

* 🔐 Basic Authentication using AWS Secrets Manager
* ☁️ Fully Serverless – Powered by AWS Lambda + API Gateway + S3
* 📤 Upload and create folders directly from the browser
* 📥 Download individual files
* 🗑 Delete files easily from dropdown selection
* 🧾 Real-time file list from S3
* 💡 Simple HTML + JavaScript frontend — no frameworks needed

---

🏗️ Architecture Overview

```
Frontend (index.html)
        |
        ▼
AWS API Gateway  ←→  AWS Lambda (Python)
        |
        ▼
    AWS S3 Bucket
```

* Frontend: HTML/CSS/JS (no dependencies)
* Backend: Python (boto3 for AWS)
* Authentication: AWS Secrets Manager (Basic Auth)

---

 🔧 Backend Setup (Lambda)

1. Create an S3 bucket
   Example:

   ```
   credit-websites-hosting
   ```

2. Create a Secret in AWS Secrets Manager (name: `tests`)
   Example JSON:

   ```json
   {
     "admin": { "password": "Admin@123", "root_folder": "" },
     "user1": { "password": "User@123", "root_folder": "" }
   }
   ```

3. Deploy the Python backend (Lambda):

   ```python
   import boto3, base64, json, io, zipfile
   # ... (use the backend code provided in this repo)
   ```

4. Create an API Gateway with routes:

   ```
   /list          (GET)
   /list-files    (GET)
   /put           (PUT)
   /get           (GET)
   /delete        (DELETE)
   /download-folder (GET)
   /delete-folder (DELETE)
   ```

5. Enable CORS on all endpoints.

---

 🖥️ Frontend Setup

1. Open `index.html`
2. Update your API Gateway endpoint:

   ```js
   const apiBase = "https://your-api-id.execute-api.ap-south-1.amazonaws.com/prod";
   ```
3. Open the file in your browser.
4. Login using credentials stored in AWS Secrets Manager.

---

 🧰 Example Credentials

| Username | Password  |
| -------- | --------- |
| admin    | Admin@123 |
| user1    | User@123  |

---

 🧪 Example Workflow

1. Login with your credentials
2. Upload files to S3
3. List & Download available files
4. Delete unwanted files
5. Create Folders inside your bucket

---

🧱 Tech Stack

| Component | Technology              |
| --------- | ----------------------- |
| Frontend  | HTML, CSS, Vanilla JS   |
| Backend   | AWS Lambda (Python 3.x) |
| Storage   | AWS S3                  |
| Secrets   | AWS Secrets Manager     |
| API Layer | AWS API Gateway         |

---

🛡️ Security

* Each user’s credentials are stored securely in AWS Secrets Manager.
* Authentication uses Basic Auth via HTTPS.
* Optional folder isolation supported via `root_folder` field in secrets.

---

📸 Screenshots

<img width="1920" height="913" alt="s3" src="https://github.com/user-attachments/assets/4e3d858f-f811-4c3c-9b85-2b63a4004386" />


---

 🧑‍💻 Author

Nipun Yadav
💼 DevOps & Cloud Engineer
🌐 [LinkedIn](https://www.linkedin.com/in/nipun-yadav-5bb736178/) | [GitHub](https://github.com/Nyadav123)

---

📄 License

This project is licensed under the MIT License — feel free to use and modify.

---

✅ Future Enhancements

* Multi-user folder isolation
* Drag-and-drop file uploads
* File preview support
* Pagination for large buckets
