# 🏗️ System Architecture - Course Management System

## 📊 Complete System Overview

```
┌─────────────────────────────────────────────────────────────┐
│                     USER INTERFACE LAYER                     │
├─────────────────────────────────────────────────────────────┤
│                                                               │
│   ┌─────────────────┐           ┌─────────────────┐         │
│   │  Teacher View   │           │  Student View   │         │
│   ├─────────────────┤           ├─────────────────┤         │
│   │ • My Courses    │           │ • Available     │         │
│   │ • Create Course │           │ • My Courses    │         │
│   │ • Assignments   │           │ • Assignments   │         │
│   │ • Submissions   │           │ • My Grades     │         │
│   │ • Analytics     │           │                 │         │
│   └─────────────────┘           └─────────────────┘         │
│                                                               │
└───────────────────────────┬─────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                    APPLICATION LAYER                         │
├─────────────────────────────────────────────────────────────┤
│                                                               │
│   ┌──────────────────────────────────────────────┐          │
│   │         dashboard-advanced.js                │          │
│   │         (828 lines of logic)                 │          │
│   ├──────────────────────────────────────────────┤          │
│   │ • Authentication Management                  │          │
│   │ • Course Operations                          │          │
│   │ • Assignment Handling                        │          │
│   │ • Submission Processing                      │          │
│   │ • Grade Calculation                          │          │
│   │ • Analytics Generation                       │          │
│   └──────────────────────────────────────────────┘          │
│                                                               │
└───────────────────────────┬─────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                       API LAYER (REST)                       │
├─────────────────────────────────────────────────────────────┤
│                                                               │
│   ┌────────────┐  ┌────────────┐  ┌────────────┐           │
│   │   Users    │  │  Courses   │  │Assignments │           │
│   ├────────────┤  ├────────────┤  ├────────────┤           │
│   │ Register   │  │ Create     │  │ Create     │           │
│   │ Login      │  │ Read       │  │ Read       │           │
│   │ Get All    │  │ Update     │  │ Delete     │           │
│   │ Delete     │  │ Delete     │  │ Get by     │           │
│   │            │  │ Enroll     │  │ Course     │           │
│   │            │  │ Students   │  │            │           │
│   └────────────┘  └────────────┘  └────────────┘           │
│                                                               │
│   ┌────────────┐  ┌────────────┐                            │
│   │Submissions │  │  Grading   │                            │
│   ├────────────┤  ├────────────┤                            │
│   │ Submit     │  │ Grade      │                            │
│   │ Get All    │  │ Feedback   │                            │
│   │ By Student │  │ Performance│                            │
│   │ By Course  │  │ Analytics  │                            │
│   └────────────┘  └────────────┘                            │
│                                                               │
│              Total: 23+ API Endpoints                        │
└───────────────────────────┬─────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                    BUSINESS LOGIC LAYER                      │
├─────────────────────────────────────────────────────────────┤
│                                                               │
│   ┌──────────────────────────────────────────────┐          │
│   │         server.js (640+ lines)               │          │
│   ├──────────────────────────────────────────────┤          │
│   │ • Input Validation                           │          │
│   │ • Authentication Logic                       │          │
│   │ • Authorization Checks                       │          │
│   │ • Business Rules Enforcement                 │          │
│   │ • Grade Calculation Algorithm                │          │
│   │ • Performance Analytics                      │          │
│   └──────────────────────────────────────────────┘          │
│                                                               │
└───────────────────────────┬─────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                     DATA ACCESS LAYER                        │
├─────────────────────────────────────────────────────────────┤
│                                                               │
│   ┌──────────────────────────────────────────────┐          │
│   │            Mongoose ODM                      │          │
│   ├──────────────────────────────────────────────┤          │
│   │ • Schema Definitions                         │          │
│   │ • Model Operations                           │          │
│   │ • Query Building                             │          │
│   │ • Relationship Management                    │          │
│   └──────────────────────────────────────────────┘          │
│                                                               │
└───────────────────────────┬─────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────┐
│                     DATABASE LAYER                           │
├─────────────────────────────────────────────────────────────┤
│                                                               │
│   ┌──────────┐  ┌──────────┐  ┌────────────┐               │
│   │  Users   │  │ Courses  │  │Assignments │               │
│   ├──────────┤  ├──────────┤  ├────────────┤               │
│   │ _id      │  │ _id      │  │ _id        │               │
│   │ name     │  │ title    │  │ title      │               │
│   │ email    │  │ desc     │  │ desc       │               │
│   │ password │  │ duration │  │ courseId   │               │
│   │ role     │  │ teacherId│  │ teacherId  │               │
│   │ createdAt│  │ enrolled │  │ dueDate    │               │
│   │          │  │  []      │  │ maxPoints  │               │
│   └──────────┘  └──────────┘  └────────────┘               │
│                                                               │
│   ┌─────────────────────────────┐                           │
│   │      Submissions            │                           │
│   ├─────────────────────────────┤                           │
│   │ _id                         │                           │
│   │ assignmentId                │                           │
│   │ studentId                   │                           │
│   │ courseId                    │                           │
│   │ content                     │                           │
│   │ fileUrl                     │                           │
│   │ grade                       │                           │
│   │ feedback                    │                           │
│   │ status                      │                           │
│   │ submittedAt                 │                           │
│   │ gradedAt                    │                           │
│   └─────────────────────────────┘                           │
│                                                               │
│                  MongoDB Database                            │
└─────────────────────────────────────────────────────────────┘
```

---

## 🔄 Data Flow Diagrams

### 1. User Registration Flow

```
┌────────┐      ┌──────────┐      ┌────────┐      ┌──────────┐
│ User   │─────>│ Frontend │─────>│   API  │─────>│ Database │
│ Input  │      │Validation│      │ /register      │  Users   │
└────────┘      └──────────┘      └────────┘      └──────────┘
                                       │
                                       │ Hash Password
                                       │ (bcrypt)
                                       ▼
                                  Save to DB
                                       │
                                       ▼
┌────────┐      ┌──────────┐      ┌────────┐
│Success │<─────│ Response │<─────│  User  │
│Message │      │  JSON    │      │Created │
└────────┘      └──────────┘      └────────┘
```

### 2. Course Enrollment Flow (Silver Level)

```
┌─────────┐     ┌──────────┐     ┌────────────┐     ┌──────────┐
│Student  │────>│ Enroll   │────>│Check if    │────>│Update    │
│Clicks   │     │ Button   │     │Already     │     │Course    │
│"Enroll" │     │          │     │Enrolled    │     │Document  │
└─────────┘     └──────────┘     └────────────┘     └──────────┘
                                       │                   │
                                       │ Not Enrolled      │
                                       ▼                   ▼
                                  POST /enroll      Push to Array
                                       │                   │
                                       ▼                   ▼
                              ┌────────────────┐   ┌──────────┐
                              │enrolledStudents│   │ Save to  │
                              │   studentId    │   │    DB    │
                              │  studentName   │   └──────────┘
                              │  enrolledAt    │
                              └────────────────┘
```

### 3. Assignment Submission Flow (Gold Level)

```
┌─────────┐     ┌──────────┐     ┌────────────┐     ┌──────────┐
│Student  │────>│ Submit   │────>│Validate:   │────>│ Create   │
│Fills    │     │ Modal    │     │• Enrolled? │     │Submission│
│Form     │     │          │     │• Not Dup?  │     │ Document │
└─────────┘     └──────────┘     └────────────┘     └──────────┘
                                       │                   │
                                       ▼                   ▼
                              ┌────────────────┐   ┌──────────┐
                              │POST /submissions   │ Save to  │
                              │{                │   │    DB    │
                              │ assignmentId,   │   └──────────┘
                              │ studentId,      │
                              │ content,        │
                              │ fileUrl         │
                              │}                │
                              └────────────────┘
```

### 4. Grading Flow (Platinum Level)

```
┌─────────┐     ┌──────────┐     ┌────────────┐     ┌──────────┐
│Teacher  │────>│ Grade    │────>│Validate:   │────>│ Update   │
│Enters   │     │ Modal    │     │• 0-Max?    │     │Submission│
│Grade    │     │          │     │• Owner?    │     │ Document │
└─────────┘     └──────────┘     └────────────┘     └──────────┘
                                       │                   │
                                       ▼                   ▼
                              ┌────────────────┐   ┌──────────┐
                              │PUT /grade      │   │ Update:  │
                              │{               │   │ • grade  │
                              │ grade: 95,     │   │ • feedback
                              │ feedback: "..." │   │ • status │
                              │}               │   │ • gradedAt
                              └────────────────┘   └──────────┘
                                       │
                                       ▼
                              ┌────────────────┐
                              │Student Sees    │
                              │Grade & Feedback│
                              └────────────────┘
```

### 5. Analytics Calculation Flow (Platinum Level)

```
┌─────────┐     ┌──────────┐     ┌────────────┐
│Teacher  │────>│Analytics │────>│Get All     │
│Clicks   │     │   Tab    │     │Submissions │
│Analytics│     │          │     │for Course  │
└─────────┘     └──────────┘     └────────────┘
                                       │
                                       ▼
                              ┌────────────────┐
                              │For Each Student│
                              │Calculate:      │
                              │• Total Points  │
                              │• Max Points    │
                              │• Percentage    │
                              └────────────────┘
                                       │
                                       ▼
                              ┌────────────────┐
                              │Formula:        │
                              │(Earned/Max)×100│
                              │                │
                              │Example:        │
                              │95+88=183       │
                              │183/200=91.5%   │
                              └────────────────┘
                                       │
                                       ▼
                              ┌────────────────┐
                              │Display Table:  │
                              │• Student Name  │
                              │• Submissions   │
                              │• Avg Grade %   │
                              │• Points        │
                              └────────────────┘
```

---

## 🔐 Security Architecture

```
┌────────────────────────────────────────────────┐
│              Security Layers                   │
├────────────────────────────────────────────────┤
│                                                │
│  1. Frontend Validation                       │
│     ├─ Required field checks                  │
│     ├─ Email format validation                │
│     └─ Input sanitization                     │
│                                                │
│  2. Backend Validation                        │
│     ├─ All inputs re-validated                │
│     ├─ Type checking                          │
│     └─ Range validation                       │
│                                                │
│  3. Authentication                            │
│     ├─ Password hashing (bcrypt)              │
│     ├─ Salt rounds: 10                        │
│     └─ Session management                     │
│                                                │
│  4. Authorization                             │
│     ├─ Role-based access control              │
│     ├─ Ownership verification                 │
│     └─ Enrollment checks                      │
│                                                │
│  5. Database Security                         │
│     ├─ Unique constraints (email)             │
│     ├─ Index optimization                     │
│     └─ No SQL injection (Mongoose)            │
│                                                │
│  6. CORS Protection                           │
│     ├─ Allowed origins                        │
│     └─ Credential handling                    │
│                                                │
└────────────────────────────────────────────────┘
```

---

## 📊 Role-Based Access Control

```
┌──────────────────────────────────────────────┐
│            Teacher Permissions               │
├──────────────────────────────────────────────┤
│ ✅ Create Courses                            │
│ ✅ Delete Own Courses                        │
│ ✅ View Enrolled Students                    │
│ ✅ Create Assignments                        │
│ ✅ Delete Own Assignments                    │
│ ✅ View All Submissions                      │
│ ✅ Grade Submissions                         │
│ ✅ Provide Feedback                          │
│ ✅ View Analytics                            │
│ ❌ Enroll in Courses                         │
│ ❌ Submit Assignments                        │
└──────────────────────────────────────────────┘

┌──────────────────────────────────────────────┐
│            Student Permissions               │
├──────────────────────────────────────────────┤
│ ✅ View All Courses                          │
│ ✅ Enroll in Courses                         │
│ ✅ View Enrolled Courses                     │
│ ✅ View Course Assignments                   │
│ ✅ Submit Assignments                        │
│ ✅ View Own Grades                           │
│ ✅ Read Teacher Feedback                     │
│ ✅ Track Own Performance                     │
│ ❌ Create Courses                            │
│ ❌ Create Assignments                        │
│ ❌ Grade Assignments                         │
│ ❌ View Other Students' Work                 │
└──────────────────────────────────────────────┘
```

---

## 🎯 Feature Implementation Matrix

| Feature | User Story | Level | Teacher | Student |
|---------|-----------|-------|---------|---------|
| Registration | US1 | Foundation | ✅ | ✅ |
| Login | US1 | Foundation | ✅ | ✅ |
| Create Course | US2 | Foundation | ✅ | ❌ |
| View Courses | US2 | Foundation | ✅ | ✅ |
| Enroll in Course | US3 | Silver | ❌ | ✅ |
| View Enrolled | US3 | Silver | ❌ | ✅ |
| View Students | US3 | Silver | ✅ | ❌ |
| Create Assignment | US4 | Gold | ✅ | ❌ |
| Submit Assignment | US4 | Gold | ❌ | ✅ |
| View Submissions | US4 | Gold | ✅ | ❌ |
| Grade Assignment | US5 | Platinum | ✅ | ❌ |
| View Grades | US5 | Platinum | ❌ | ✅ |
| View Analytics | US5 | Platinum | ✅ | ✅ |

---

## 📈 System Scalability

```
Current Design Supports:

┌─────────────────┬──────────────┐
│ Metric          │ Capacity     │
├─────────────────┼──────────────┤
│ Users           │ Unlimited    │
│ Courses         │ Unlimited    │
│ Assignments     │ Unlimited    │
│ Submissions     │ Unlimited    │
│ Concurrent Req  │ 100+         │
│ DB Size         │ Unlimited    │
└─────────────────┴──────────────┘

Performance Optimizations:
✅ Indexed database queries
✅ Pagination ready
✅ Async/await operations
✅ Efficient algorithms
✅ Minimal frontend re-renders
```

---

## 🎨 UI Component Hierarchy

```
Dashboard
├── Header
│   ├── Title
│   ├── User Badge (name + role)
│   └── Logout Button
│
├── Welcome Section
│   ├── Greeting
│   └── Role-specific message
│
├── Message Area
│   └── Success/Error notifications
│
├── Tab Navigation
│   └── Role-specific tabs
│
└── Content Area
    ├── Teacher Tabs
    │   ├── My Courses (Cards Grid)
    │   ├── Create Course (Form)
    │   ├── Assignments (Form + Grid)
    │   ├── Submissions (Tables)
    │   └── Analytics (Stats + Tables)
    │
    └── Student Tabs
        ├── Available Courses (Cards Grid)
        ├── My Courses (Cards Grid)
        ├── My Assignments (Cards Grid)
        └── My Grades (Stats + Tables)
```

---

This architecture supports all 5 user stories across 3 functional levels (Silver, Gold, Platinum) with complete security, scalability, and maintainability!
