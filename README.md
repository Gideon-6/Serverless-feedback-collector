# ☁️ Serverless Feedback Collector Application

### 🧑‍💻 Author: Budidha Gideon Joy  
**College:** TKR College of Engineering and Technology  
**Domain:** Cloud Computing and Serverless Architecture  
**Duration:** [Insert Project Duration Here, e.g., 3 Days] Project

---

## 🏗️ Project Overview
This project implements a complete **serverless application** for collecting and displaying user feedback. It utilizes a lightweight, highly-scalable, and cost-effective **AWS stack** to demonstrate core **CRUD (Create & Read)** operations.  

The application consists of a public submission form and a basic admin dashboard for viewing entries.

---

## ⚙️ Architecture Overview

### 🔹 Application Flow
1. **Frontend:** Static HTML/JS pages (`index.html`, `admin.html`) hosted on **AWS S3**.  
2. **Submission (Create):** The form sends a **POST** request to the API Gateway `/feedback` route.  
3. **API Gateway:** Routes the request to the `create-feedback` **Lambda function**.  
4. **Persistence:** The Lambda function saves the entry (with a unique ID and timestamp) to **DynamoDB**.  
5. **Retrieval (Read):** The admin page sends a **GET** request to the API Gateway `/admin/feedback` route.  
6. **Data Display:** A separate `list-feedback` **Lambda function** queries DynamoDB and returns all items to the admin dashboard for display.

### 🧭 Architecture Diagram
[User Browser] ↔ [Static S3 Hosting]     ↓ (POST /feedback) [API Gateway] ↔ [Lambda (create-feedback)] ↔ [DynamoDB Table]     ↑ (GET /admin/feedback) [Admin Page] ↔ [Lambda (list-feedback)]


---

## 🗂️ DynamoDB Schema

| Attribute | Type | Description |
|:---|:---|:---|
| **feedbackId (PK)** | String | Unique identifier for the feedback entry (UUID) |
| **feedbackText** | String | The actual feedback submitted by the user |
| **createdAt** | String | Timestamp of when the entry was created |

---
## 📸 AWS Resource Validation Figures

The following figures validate the successful deployment and integration of the serverless components in the `eu-north-1` (Stockholm) region.

### Figure 1: Styled Feedback Form and Submission Success
![alt text](<Screenshot 2025-10-24 165936.png>)

The user interface is hosted on S3 and confirms a successful POST operation to the API Gateway.

### Figure 2: Admin Dashboard and Data Retrieval
![alt text](<Screenshot 2025-10-24 165951.png>)

The `admin.html` page successfully fetches and displays the data from the backend, confirming the working GET request.

### Figure 3: API Gateway Routes and Integrations
![alt text](<Screenshot 2025-10-24 170115.png>)
![alt text](<Screenshot 2025-10-24 170140.png>)
![alt text](<Screenshot 2025-10-24 170151.png>)

The two primary routes are configured: **POST /feedback** and **GET /admin/feedback**, integrated with their respective Lambda functions (`create-feedback` and `list-feedback`).

### Figure 4: DynamoDB Table Contents
![alt text](<Screenshot 2025-10-24 170025.png>)

The `feedback-table` is online and contains confirmed entries, proving data persistence and successful integration with the Lambda functions.

### Figure 5: AWS Lambda Function - create-feedback
![alt text](<Screenshot 2025-10-24 170241.png>)
![alt text](<Screenshot 2025-10-24 170358.png>)

The `create-feedback` function handles the POST request, processes validation, and writes to DynamoDB. The test status is confirmed successful.

### Figure 6: AWS Lambda Function - list-feedback
![alt text](<Screenshot 2025-10-24 170504.png>)

The `list-feedback` function is integrated with the API Gateway GET route, responsible for querying all data from DynamoDB for the admin page.

## 🚀 Features
- ✅ **Serverless Architecture:** No servers to manage (Lambda, DynamoDB).  
- ✅ **CRUD Operations:** Supports submission (Create) and retrieval (Read).  
- ✅ **CORS Management:** Properly configured in API Gateway to allow S3 hosting.  
- ✅ **Cost-Effective:** Operates almost entirely within AWS Free Tier limits.  
- ✅ **Responsive UI:** Modern, centered design using static HTML/CSS.  

---

## 🧩 AWS Services Used
| Service | Purpose |
|:---|:---|
| **AWS Lambda** | Executes backend logic for handling POST and GET requests. |
| **Amazon API Gateway** | Provides a highly-available REST API for the frontend to interact with. |
| **Amazon DynamoDB** | NoSQL database for scalable and fast storage of feedback entries. |
| **AWS S3** | Hosts the static frontend web application (`index.html`, `admin.html`). |

---

## 🧾 Future Enhancements
- Implement **Cognito Authentication** on the `/admin/feedback` route for security.  
- Add **Delete** and **Update** functionality (making it full CRUD).  
- Integrate **Amazon SES** to send an email notification to an admin after every submission.  
- Migrate the frontend to a modern framework (React/Vue) and host on **Amplify Hosting**.

---

## 🏁 Conclusion
This project successfully demonstrates the fundamental principles of building a completely serverless web application. It is a robust starting point for larger, event-driven, and scalable cloud projects.

---

### 📧 Contact
**Budidha Gideon Joy**  
*TKR College of Engineering and Technology*  
📍 Hyderabad, India  
✉️ gideonjoy612@gmail.com