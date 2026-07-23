# 📅 Smart Routine Management System (SRMS)

## 🚀 Overview
The **Smart Routine Management System** is a robust, full-stack web application designed to automate and optimize the process of class scheduling. It eliminates manual errors, prevents scheduling conflicts, and provides a seamless real-time routine viewing experience for students and faculty.

## 💡 Solution to Existing Problems (Unique Ideas)
* **Conflict-Free Scheduling:** An integrated validation engine (Rule-based heuristic logic) ensures no two classes are assigned to the same room or teacher at the same time.
* **Role-Based Access Control:** Secure boundaries between Faculty Admins, Department Admins, and general users.
* **Exceptional UI/UX:** Built with Tailwind CSS, ensuring a responsive, modern, and intuitive interface across all devices.

## 🛠️ Tech Stack (Full Stack)
* **Backend:** Python, Django
* **Database:** PostgreSQL (Serverless via Neon DB)
* **Frontend:** HTML5, Tailwind CSS
* **Deployment:** Render.com

## ⚙️ System Architecture Flowchart
```mermaid
graph TD
    subgraph Frontend [Frontend - Client Side]
        UI[Web Browser / UI]
        CSS[Tailwind CSS & HTML5]
    end

    subgraph Backend [Backend - Render.com Hosting]
        Django[Django Framework]
        Auth[Role-Based Access Control]
        Logic[Validation Engine / Business Logic]
    end

    subgraph Database [Cloud Database]
        Neon[(Neon DB - PostgreSQL)]
    end

    UI -->|HTTP Requests| Django
    Django -->|HTTP Responses| UI
    UI --- CSS
    Django --- Auth
    Django --- Logic
    Logic <-->|Read / Write Data| Neon



graph LR
    Admin[Dept Admin] -->|1. Assigns Class, Room & Time| Engine(Validation Engine)
    Engine -->|2. Checks existing records| DB[(PostgreSQL Database)]
    DB -->|3. Returns Data Status| Engine
    
    Engine -->|4a. Conflict Detected| Error[Show Error Message]
    Error --> Admin
    
    Engine -->|4b. No Conflict| Save[Save New Routine]
    Save --> DB
    
    Student[Student / Teacher] -->|5. Requests Routine View| View(Query Routine Data)
    View --> DB
    DB -->|6. Sends Data| View
    View -->|7. Displays Routine| Student
```

## 📂 Project Structure
```text
URMS_WORKSPACE/
├── routines/               # Main App (Models, Views, Controllers)
│   ├── migrations/         # Database migrations
│   ├── templates/          # UI / HTML files (Tailwind integrated)
│   ├── models.py           # Database Schema (Course, Room, Teacher, Routine)
│   └── views.py            # Business Logic & Validation Engine
├── urms_project/           # Project Configuration
│   ├── settings.py         # App settings & DB Config
│   └── wsgi.py             # Web Server Gateway Interface
├── staticfiles/            # Compiled static assets
├── .env                    # Environment Variables (Ignored in Git)
├── Procfile                # Deployment instructions for Render
└── requirements.txt        # Python dependencies


