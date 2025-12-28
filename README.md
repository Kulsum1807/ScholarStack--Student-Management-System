# ScholarStack – Student Management System

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-000000?style=flat&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white)
![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=react&logoColor=black)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

# 📚 ScholarStack – Student Management System

A **secure, role-based Student Management System** built with **Node.js, Express, MongoDB, JWT**, and **React**, focusing on **authentication, authorization (RBAC)**, and **ownership-based access control**.

---

## 📌 Project Overview

**ScholarStack** is designed to demonstrate how real-world backend systems handle:
- Secure user authentication
- Role-based access control (Admin & Student)
- Ownership-based data protection

---

## ✨ Key Features

- Secure JWT-based authentication
- Role-Based Access Control (RBAC)
- Ownership-based authorization
- Admin & Student dashboards
- Course enrollment system
- RESTful API architecture
- MVC-based backend structure
- Postman-tested APIs

---

## 👩‍🎓 Student Module

Students can:
- Sign up and log in securely
- View available courses
- Enroll in courses
- View **only their own enrolled courses**
- Cannot create, update, or delete students/courses
- Dashboard showing course count and details
- Profile information (Name, Age, City, Email)

Ownership is enforced using the student’s ID from JWT

---

Admins can:
- Log in securely
- View all students
- View student enrollments
- Create, edit, and delete courses
- Access system-wide data
- Dashboard analytics:
  - Total students
  - Total courses

Admins **cannot enroll in courses**

---

## 📘 Course Management

- Admin creates and manages courses
- Courses contain:
  - Title
  - Description
- Students can only **view and enroll**
- Course ownership is managed via the Enrollment model

---

## UI / UX

- Clean and modern UI
- Responsive layout
- Split authentication layout
- Floating emoji background for visual appeal
- Reusable UI components (buttons, inputs, cards)
- Role-based dashboards
- Protected routes on frontend
- Simple, intuitive navigation
- Focused on clarity over complexity

---

## Tech Stack (Technologies Used)

**Frontend**

- React
- React Router
- Fetch API
- CSS (custom styling)

### Backend
- Node.js
- Express.js
- MongoDB
- Mongoose
- JWT (jsonwebtoken)
- bcrypt
- dotenv

---

## System Architecture

The ScholarStack system follows a **client–server architecture**:

- **Frontend (React)** communicates with the backend using REST APIs.
- **Backend (Node.js + Express)** handles authentication, authorization, and business logic.
- **MongoDB** stores users, courses, and enrollment data.
- **JWT** is used for stateless authentication.
- **Role-Based Access Control (RBAC)** ensures restricted access for admins and students.

**Flow:**
Frontend → API Request → JWT Verification → Controller → Database → Response

### Why MVC?
- Separation of concerns
- Clean and scalable codebase
- Easy debugging and testing
- Industry-standard design

---

## Project Structure

```
ScholarStack/
│
├── backend/
│ ├── config/
│ │ └── database.js
│ ├── controllers/
│ │ ├── authController.js
│ │ ├── courseController.js
│ │ ├── enrollmentController.js
│ │ └── adminController.js
│ ├── middleware/
│ │ ├── authMiddleware.js
│ │ └── roleMiddleware.js
│ ├── models/
│ │ ├── userModel.js
│ │ ├── courseModel.js
│ │ └── enrollmentModel.js
│ ├── routes/
│ │ ├── authRoutes.js
│ │ ├── courseRoutes.js
│ │ ├── enrollmentRoutes.js
│ │ └── adminRoutes.js
│ ├── server.js
│ └── .env
│
├── frontend/
│ ├── src/
│ │ ├── pages/
│ │ ├── layout/
│ │ ├── api/
│ │ └── styles/
│ └── main.jsx
│
└── README.md

```

### Folder Overview

- **backend/** - Node.js + Express REST API (MVC structure)
- **frontend/** - React (Vite) based user interface
- **.env.example** - Sample environment variables (no secrets exposed)
- **.gitignore** - Prevents sensitive and unnecessary files from being pushed
- **controllers** - Business logic
- **models** - Database schemas
- **routes** - API endpoints
- **middleware** - Security logic
- **config** - Database connection

---

## API Endpoints (Sample)

### Authentication

- `POST /api/auth/signup` – Register student
- `POST /api/auth/login` – Login user

### Student

- `GET /api/student/dashboard`
- `GET /api/student/courses`
- `POST /api/student/enroll/:courseId`

### Admin

- `GET /api/admin/students`
- `POST /api/admin/course`
- `PUT /api/admin/course/:id`
- `DELETE /api/admin/course/:id`

---

## Security Practices

- Passwords are hashed using **bcrypt**
- JWT tokens are signed using a secret stored in environment variables
- Sensitive files (`.env`, `node_modules`) are excluded via `.gitignore`
- Role-based middleware protects admin routes
- Backend secrets are never pushed to GitHub
- Ownership-based queries  
- Protected routes  
- No session storage

---

## Environment Variables

Create a .env file inside the backend folder:

```

PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret

```

**Note:** Replace your_mongodb_connection_string_here with your actual connection link.

- For MongoDB Atlas, use your cluster connection string.
- For MongoDB Compass (local), use something like mongodb://127.0.0.1:27017/studentDB.

---

## How to Run the Project

- Backend

```
cd backend
npm init -y  #creates a package.json file
npm install
npm run dev
```

- Frontend

```
cd frontend
npm init -y  #creates a package.json file
npm install
npm start
```

---

## Deployment

### Backend Deployment (Render)

- Backend deployed as a **Node Web Service**
- Root directory set to `backend`
- Environment variables configured in Render dashboard
- Auto-deployment enabled on GitHub push
- Node.js service
- Environment variables added in Render dashboard
- MongoDB Atlas used

### Frontend Deployment (Optional)

- Frontend can be deployed on **Vercel / Netlify**
- Backend API base URL updated to Render endpoint
- Build using npm run build

---

## Default Roles

1. Student:

- Signup via UI
- Automatically assigned student role

2. Admin

- Must be created manually in MongoDB or seeded
- Role set as "admin"

---

## Database Models

- User
{ name, age, city, email, password(hashed), role(admin/student), timestamps }

- Course
{ title, description }


- Enrollment
{ student, course }

---

## Future Enhancements

- Student profile editing
- Course progress tracking
- Admin analytics dashboard
- Pagination & search
- Password reset functionality
- Attendance tracking
- Marks & grading system
- Teacher role
- Email verification
- Refresh token mechanism
- Audit logs

---

## 🌐 **Live Demo**

- **Backend (Render Hosted)**: []()
  _(This is the live API endpoint — Routes can be directly tested in Postman using this base URL)_

---

## **License**

This project is licensed under the **MIT License** — you are free to use, modify, and distribute it with proper attribution.

---

## **Author**

**Kulsum**

- _ScholarStack-Student Management System — Major Project_
- kulsumsheikh1807@gmail.com
- [GitHub](https://github.com/Kulsum1807)
