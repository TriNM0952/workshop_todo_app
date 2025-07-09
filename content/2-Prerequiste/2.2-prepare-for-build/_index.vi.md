---
title: "Xây dựng và triển khai giao diện người dùng"
date: 2025-07-09
weight: 2
chapter: false
pre: " <b> 2.2 </b> "
---

Sau khi hoàn tất việc xây dựng backend serverless, bước tiếp theo là xây dựng và triển khai giao diện người dùng với React. Giao diện sẽ được kết nối với API Gateway sử dụng `x-api-key` để thực hiện các thao tác CRUD với Lambda + DynamoDB.

---
## Các bước chuẩn bị
## 🖥️ Kiến trúc giao diện

Giao diện người dùng (frontend) sẽ là một ứng dụng React đơn trang (SPA), được **build tĩnh và lưu trữ trên S3**, phân phối qua **CloudFront**, và kết nối với backend thông qua **API Gateway**.

---

## 🧰 Công cụ và tài nguyên cần chuẩn bị

### 1. Công cụ phát triển
- Node.js >= 18
- npm hoặc yarn
- React + React DOM
- Code Editor (VS Code)

### 2. Tài nguyên AWS cần thiết
- S3 bucket (hosting static website)
- CloudFront Distribution
- API Gateway endpoint (đã có từ backend)
- API Key bảo mật endpoint

---

## 📁 Tạo giao diện với React

### 1. Tạo project

```bash
npx create-react-app todo-frontend
cd todo-frontend
```
### 2. Cấu trúc thư viện
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
### 3. Kết nối với API Gateway
- Sử dụng đường dẫn và API key bạn có được từ server để sử dụng
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

// POST, PUT, DELETE tương tự
```
### 4. Build giao diện
- Sau khi xây dựng xong giao diện
```bash
npm run build
```
- Sau khi chạy lệnh, source giao diện của bạn sẽ đóng gói lại thành file _build_, bạn sẽ sử dụng file này cho bước tiếp theo
![S3](/images/3.S3/09-S3-Load-data.png)
## 🔗 Tài liệu tham khảo
- Bạn có thể tham khảo thêm tại Git (https://github.com/TriNM0952/Workshop.git)