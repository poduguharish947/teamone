# EduLearn LMS - Learning Management System

A comprehensive Learning Management System built for a 24-hour hackathon with features for both students and faculty.

## 🏆 Hackathon Ranking Achieved: Platinum Level

This project implements all required user stories from Bronze to Platinum levels:

### Bronze Level ✅
- User Registration & Login
- Course Management (Teacher role)
- Course Viewing (Student role)

### Silver Level ✅
- Course Enrollment

### Gold Level ✅
- Assignment Submission

### Platinum Level ✅
- Grading System

## 🚀 Features

### For Students:
- User registration and authentication
- Browse available courses
- Enroll in courses
- View enrolled courses
- Submit assignments
- View grades and feedback

### For Faculty:
- User registration and authentication
- Create and manage courses
- View enrolled students
- Create assignments
- Grade student submissions
- View submission statistics

## 🛠️ Tech Stack

### Frontend:
- **HTML5, CSS3, JavaScript**
- **Bootstrap 5** for responsive design
- **Client-side storage** with localStorage (fallback when backend is not available)

### Backend:
- **Node.js** with Express.js
- **MongoDB** with Mongoose ODM
- **JWT** for authentication
- **Bcrypt.js** for password hashing

## 📁 Project Structure

```
lms/
├── index.html        # Landing page
├── login.html        # Authentication page
├── student.html      # Student dashboard
├── faculty.html      # Faculty dashboard
├── README.md         # Project documentation
└── backend/          # Backend API
    ├── controllers/
    ├── middleware/
    ├── models/
    ├── routes/
    ├── .env
    ├── package.json
    ├── server.js
    └── README.md
```

## ▶️ How to Run

### Option 1: With Backend (Recommended)

1. **Start MongoDB**
   Make sure MongoDB is running on your system. If not installed, download from [MongoDB website](https://www.mongodb.com/try/download/community).

2. **Setup Backend**
   ```bash
   cd backend
   npm install
   ```

3. **Configure Environment**
   Create a `.env` file in the backend directory:
   ```
   PORT=5000
   MONGODB_URI=mongodb://localhost:27017/lms
   JWT_SECRET=your_jwt_secret_key_here
   ```

4. **Start Backend Server**
   ```bash
   npm start
   # or for development with auto-restart
   npm run dev
   ```

5. **Open Frontend**
   Open `index.html` in a web browser and use the application with full backend functionality.

### Option 2: Frontend Only (Static)

1. Open `index.html` in a web browser
2. The application will use localStorage for data persistence
3. Note: Data will not persist between different browsers or devices

## 🌐 Hosting

### Frontend
This application is built with static files and can be hosted on any static hosting service:
- Vercel
- Netlify
- GitHub Pages
- Render
- AWS S3

### Backend
The backend can be deployed to:
- Heroku
- Render
- AWS Elastic Beanstalk
- DigitalOcean App Platform

## 🎯 User Stories Implementation

### User Story 1 – User Registration & Login
- Students and faculty can register with name, email, password, and role
- Secure login functionality with validation
- JWT-based authentication for backend

### User Story 2 – Course Management
- Faculty can create courses with title, description, and duration
- Students can view all available courses
- Courses display with optional YouTube video integration

### User Story 3 – Course Enrollment
- Students can enroll in courses
- Students can view their enrolled courses
- Faculty can see enrollment statistics

### User Story 4 – Assignment Submission
- Faculty can create assignments with due dates
- Students can submit assignments
- Faculty can view all submissions

### User Story 5 – Grading System
- Faculty can grade student assignments with scores and feedback
- Students can view their grades
- Overall performance tracking

## 📸 Screenshots

### Landing Page
![Landing Page](screenshots/landing.png)

### Login/Registration
![Login Page](screenshots/login.png)

### Faculty Dashboard
![Faculty Dashboard](screenshots/faculty.png)

### Student Dashboard
![Student Dashboard](screenshots/student.png)

## 🤝 Team

- [Your Name] - Full Stack Developer

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- Bootstrap for UI components
- Flaticon for icons
- Freepik for images