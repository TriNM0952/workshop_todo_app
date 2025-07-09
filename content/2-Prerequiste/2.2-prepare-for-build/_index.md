---
title: "Build and Deploy the User Interface"
date: 2025-07-09
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

After completing the serverless backend, the next step is to build and deploy the user interface with React. The UI will connect to the API Gateway using `x-api-key` to perform CRUD operations with Lambda + DynamoDB.

---
## Preparation Steps
## 🖥️ UI Architecture

The user interface (frontend) will be a single-page React application (SPA), **built statically and hosted on S3**, distributed via **CloudFront**, and connected to the backend through **API Gateway**.

---

## 🧰 Tools and Resources Needed

### 1. Development Tools
- Node.js >= 18
- npm or yarn
- React + React DOM
- Code Editor (VS Code)

### 2. Required AWS Resources
- S3 bucket (for static website hosting)
- CloudFront Distribution
- API Gateway endpoint (from backend)
- API Key to secure the endpoint

---

## 📁 Create the UI with React

### 1. Create the project

```bash
npx create-react-app todo-frontend
cd todo-frontend
```
### 2. Project structure

todo-frontend/  
├── public/  
├── src/  
│   ├── components/  
│   │   ├── Header.js  
│   │   ├── TaskForm.js  
│   │   ├── TaskList.js  
│   │   └── EditModal.js  
│   ├── service/API.js  
│   ├── assets/style.css  
│   ├── App.js  
│   └── index.js  

### 3. Connect to API Gateway
- Use the endpoint and API key you obtained from the server
```bash
const API_URL = "https://your-api-id.execute-api.ap-southeast-1.amazonaws.com/dev";
const API_KEY = "your-api-key";

const headers = {
  'Content-Type': 'application/json',
  'x-api-key': API_KEY
};

export const fetchTasks = async () => {
  const res = await fetch(`${API_URL}/todos`, { headers });
  return res.json();
};

// POST, PUT, DELETE are similar
```
### 4. Build the UI
- After building the UI
```bash
npm run build
```
- After running the command, your UI source will be packaged into the _build_ folder, which you will use for the next step
![S3](/images/3.S3/09-S3-Load-data.png)
## 🔗 References
- You can also refer to the project on Git (https://github.com/TriNM0952/Workshop.git)