# Course Management System

A comprehensive full-stack web application for managing courses, assignments, enrollments, and grading with advanced features for both teachers and students.

## 🌟 Features

### Core Features
- **User Authentication** - Secure registration and login for teachers and students
- **Course Management** - Create, edit, and delete courses (teacher role)
- **Course Enrollment** - Browse and enroll in available courses (student role)
- **Assignment Submission** - Submit assignments with file attachments
- **Grading System** - Grade assignments with feedback and analytics
- **Advanced Features** - Discussions, course materials, notifications, and progress tracking

### User Stories Implemented
1. ✅ **Registration & Login** - User authentication system
2. ✅ **Course Management** - Full CRUD operations for courses
3. ✅ **Course Enrollment (Silver)** - Student enrollment functionality
4. ✅ **Assignment Submission (Gold)** - Assignment workflow
5. ✅ **Grading System (Platinum)** - Comprehensive grading with analytics
6. ✅ **Advanced Features** - Discussions, materials, notifications, and more

## 🚀 Quick Start

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (v4.4 or higher)
- Modern web browser

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/course-management-system.git
cd course-management-system
```

2. **Set up the backend**
```bash
cd backend
npm install
```

3. **Configure environment variables**
Create a `.env` file in the `backend` directory:
```env
PORT=3000
MONGODB_URI=mongodb://localhost:27017/userdb
```

4. **Start MongoDB**
```bash
# Windows
net start MongoDB

# macOS/Linux
sudo systemctl start mongod
```

5. **Start the backend server**
```bash
cd backend
node server.js
```

6. **Access the application**
Open your browser and navigate to:
- **Modern Dashboard (with backend)**: Open `Project-Modern.html`
- **Standalone Version**: Open `Project-Modern-Standalone.html`

## 📁 Project Structure

```
course-management-system/
├── backend/
│   ├── server.js           # Main backend API (36 endpoints, 7 schemas)
│   ├── package.json        # Backend dependencies
│   ├── .env               # Environment configuration
│   └── README.md          # API documentation
├── Project-Modern.html    # Main entry point (backend integration)
├── Project-Modern-Standalone.html  # Standalone version (no backend required)
├── dashboard-modern.html  # Modern UI dashboard
├── dashboard-modern-standalone.js  # Standalone functionality
├── dashboard-advanced.js  # Advanced features logic
├── QUICK_START.md         # Quick start guide
├── COMPLETE_FEATURES_GUIDE.md  # Detailed feature documentation
├── SYSTEM_ARCHITECTURE.md # Technical architecture
└── TESTING_GUIDE.md       # Testing procedures
```

## 🎯 Usage

### For Teachers
1. Register/Login with a teacher account
2. Create courses from the dashboard
3. Add assignments to your courses
4. Add course materials and resources
5. Grade student submissions
6. Participate in course discussions
7. View analytics and student progress

### For Students
1. Register/Login with a student account
2. Browse available courses
3. Enroll in courses
4. Submit assignments
5. View grades and feedback
6. Download course materials
7. Participate in discussions

## 🛠️ Technology Stack

### Backend
- **Node.js** with Express framework
- **MongoDB** with Mongoose ODM
- **bcryptjs** for password hashing
- **CORS** enabled for frontend communication

### Frontend
- **HTML5, CSS3, JavaScript**
- **Responsive Design** with modern UI/UX
- **LocalStorage** for standalone mode
- **Fetch API** for backend communication

## 📚 Documentation

- [Quick Start Guide](QUICK_START.md) - Get started in 5 minutes
- [Complete Features Guide](COMPLETE_FEATURES_GUIDE.md) - All features explained
- [System Architecture](SYSTEM_ARCHITECTURE.md) - Technical design details
- [Testing Guide](TESTING_GUIDE.md) - How to test the application
- [Setup Guide](SETUP_GUIDE.md) - Detailed installation instructions

## 🌐 Deployment Options

### Option 1: Standalone Version (No Backend Required)
Simply open `Project-Modern-Standalone.html` in any modern browser. All data is stored locally using localStorage.

### Option 2: Full-Stack Deployment
1. Deploy backend to services like Heroku, Render, or Railway
2. Update MongoDB connection to cloud database (MongoDB Atlas)
3. Host frontend on GitHub Pages, Netlify, or Vercel
4. Update API endpoints in frontend files

### GitHub Pages Deployment
```bash
# Deploy standalone version to GitHub Pages
git checkout -b gh-pages
git add Project-Modern-Standalone.html
git commit -m "Deploy standalone version"
git push origin gh-pages
```

## 🔧 API Endpoints

The backend provides 36 REST API endpoints across 7 database schemas:

- **Authentication**: `/register`, `/login`
- **Courses**: `/courses` (CRUD operations)
- **Enrollments**: `/enrollments` (enrollment management)
- **Assignments**: `/assignments` (assignment workflow)
- **Submissions**: `/submissions` (submission handling)
- **Grades**: `/grades` (grading system)
- **Advanced**: Discussions, materials, notifications

See [backend/README.md](backend/README.md) for complete API documentation.

## 🧪 Testing

Run the comprehensive test suite:
```bash
# Manual testing with provided test cases
# See TESTING_GUIDE.md for detailed procedures
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👥 Authors

- Harish - Initial work and development

## 🌟 Features Breakdown

### User Story 1: Registration & Login ✅
- Secure user authentication with bcrypt password hashing
- Role-based access (Teacher/Student)
- Session management
- Form validation

### User Story 2: Course Management ✅
- CRUD operations for courses
- Course details (title, description, schedule)
- Teacher-only access control
- Course listing and search

### User Story 3: Course Enrollment (Silver) ✅
- Student enrollment system
- Available courses browsing
- Enrollment tracking
- "My Courses" view

### User Story 4: Assignment Submission (Gold) ✅
- Create and manage assignments
- File submission support
- Due date tracking
- Submission history

### User Story 5: Grading System (Platinum) ✅
- Grade assignments with scores and feedback
- Grade analytics and statistics
- Performance tracking
- Grade distribution charts

### User Story 6: Advanced Features ✅
- **Discussions**: Course-specific discussion boards
- **Materials**: Upload and share course materials
- **Notifications**: Real-time activity notifications
- **Progress Tracking**: Visual progress indicators
- **Analytics Dashboard**: Comprehensive statistics

## 🙏 Acknowledgments

- Built as part of a web development course project
- Implements best practices for full-stack development
- Progressive enhancement approach with standalone fallback

## 📞 Support

For issues, questions, or contributions:
- Open an issue on GitHub
- Check the documentation in the `/docs` folder
- Review the testing guide for troubleshooting

---

**Note**: This project includes both a full-stack version (with backend API) and a standalone version (using localStorage) to ensure maximum accessibility and ease of testing.
