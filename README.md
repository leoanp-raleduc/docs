# SGR Documentation

## Table of Contents

1. [Introduction](#introduction)
   - [Purpose](#purpose)
   - [Features Overview](#features-overview)
   - [Tech Stack](#tech-stack)
   - [Project Structure](#project-structure)

2. [Getting Started](#getting-started)
   - [Prerequisites](#prerequisites)
   - [Installation](#installation)
   - [Configuration](#configuration)
   - [Running the Application](#running-the-application)

3. [Backend (Django)](#backend-django)
   - [Application Overview](#application-overview)
   - [Core Functionality](#core-functionality)
   - [Udemy API Integration](#udemy-api-integration)
   - [PDF Generation](#pdf-generation)
   - [Reporting](#reporting)
   - [Data Models](#data-models)
   - [API Endpoints](#api-endpoints)

4. [Frontend (Angular)](#frontend-angular)
   - [Application Overview](#application-overview-1)
   - [Core Features](#core-features)
   - [Routing](#routing)
   - [Component Hierarchy](#component-hierarchy)
   - [Styling](#styling)

5. [Deployment](#deployment)
   - [Docker Setup](#docker-setup)
   - [Environment Variables](#environment-variables)
   - [Production Considerations](#production-considerations)
   - [CI/CD Pipeline](#cicd-pipeline)

6. [Testing](#testing)
   - [Unit Tests](#unit-tests)
   - [Integration Tests](#integration-tests)

7. [Contributing](#contributing)
   - [Code of Conduct](#code-of-conduct)
   - [Contribution Guidelines](#contribution-guidelines)

8. [License](#license)

---

## Introduction

### Purpose
The purpose of this fullstack web application is to provide a platform for managing course completion certificates for clients who have completed courses on Udemy. The application serves both an external-facing component for clients to generate and download their certificates and an internal-facing component for business analytics and decision-making.

### Features Overview
- **Certificate Generation:** Automatically generate PDF certificates for completed courses using data from the Udemy API.
- **Course Data Synchronization:** Regularly sync course data and completion metrics from Udemy.
- **Business Analytics:** Leverage course and user data to generate reports and visualizations that aid in strategic business decisions.
- **User Management:** Secure authentication and user management for both clients and internal staff.
- **Responsive Design:** A modern, responsive frontend interface built using Angular and the Fuse theme.

### Tech Stack
- **Backend:** Django
- **Frontend:** Angular with Fuse theme
- **Database:** PostgreSQL
- **API Integration:** Udemy API
- **Deployment:** Docker

### Project Structure
The project is organized into two main parts:
- **Backend (Django):** Handles the core application logic, API endpoints, data processing, and integrations.
- **Frontend (Angular):** Provides the user interface, built using the Fuse theme for a modern look and feel.

The application is structured to allow easy maintenance and scalability, ensuring that future developers can quickly navigate and understand its components.


---

## Getting Started

This section will guide you through the process of setting up the application locally for development and testing purposes.

### Prerequisites

Before you begin, ensure you have the following software installed on your machine:

- **Python 3.8+**: Required for running the Django backend.
- **Node.js 14+**: Needed for Angular development.
- **npm 6+**: Used for managing JavaScript packages.
- **Docker**: For containerization and deployment.
- **Git**: Version control system to clone the repository.

### Installation

Follow these steps to set up the application:

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/your-repo/project.git
   cd project
   ```

2. **Backend Setup (Django):**

   - Create and activate a virtual environment:

     ```bash
     python -m venv venv
     source venv/bin/activate  # On Windows use `venv\Scripts\activate`
     ```

   - Install Python dependencies:

     ```bash
     pip install -r requirements.txt
     ```

   - Apply database migrations:

     ```bash
     python manage.py migrate
     ```

   - Create a superuser account for the Django admin interface:

     ```bash
     python manage.py createsuperuser
     ```

3. **Frontend Setup (Angular):**

   - Navigate to the Angular directory:

     ```bash
     cd angular
     ```

   - Install Node.js dependencies:

     ```bash
     npm install
     ```

4. **Environment Configuration:**

   - Copy the example environment configuration and customize it:

     ```bash
     cp project/settings.example.py project/settings.py
     ```

   - Ensure you replace placeholders with actual values (e.g., API keys, database URL).

### Configuration

- **Environment Variables:**
  Set the required environment variables as specified in the `project/settings.py` or `.env` file.

  - `DJANGO_SECRET_KEY`: Your Django secret key for the application.
  - `UDEMY_API_KEY`: API key for accessing Udemy data.
  - `DATABASE_URL`: URL of the production database if different from SQLite.

### Running the Application

1. **Start the Backend Server:**

   Make sure your virtual environment is activated, then run:

   ```bash
   python manage.py runserver
   ```

   The Django development server will start at `http://127.0.0.1:8000/`.

2. **Start the Frontend Server:**

   Open a new terminal window, navigate to the Angular directory, and run:

   ```bash
   ng serve
   ```
---

## Backend (Django)

### Application Overview

The backend of this application is built using Django, a high-level Python web framework that encourages rapid development and clean, pragmatic design. It handles all server-side logic, including API integrations, data processing, and PDF generation, ensuring a seamless backend operation for the application.

### Core Functionality

- **Udemy API Integration:** The backend synchronizes course data from Udemy using their API, storing the data in the local database for use in certificate generation and reporting.
- **Certificate Generation:** The application generates PDF certificates for users who have completed courses, leveraging the `pdf_generator.py` module.
- **Data Reporting:** Utilizes `report_generator.py` to create comprehensive reports based on user activity and course completion data.

### Udemy API Integration

The Udemy API integration is handled primarily within the `api_integration` app. This includes:
- **Scripts:** The `scripts/udemy.py` module manages data pulls from the Udemy API.
- **Models:** Defined in `models/udemy_api.py`, representing the data structure for storing course and user activity information.
- **Views:** Located in `views/udemy_api.py`, exposing endpoints for retrieving and processing Udemy data.

### PDF Generation

Certificate generation is managed by the `pdf_generator.py` module, which constructs and renders PDF documents based on user data and course completion status. The PDFs are stored in the `media` directory and can be downloaded by users via the frontend.

### Reporting

Comprehensive user and course reports are generated using `report_generator.py`, providing insights into course completion rates and user engagement metrics. The reports are accessible through the admin interface and can be used for strategic decision-making.

### Data Models

The application includes several key models:
- **Udemy API Data:** Defined in `models/udemy_api.py`, modeling course and user completion data.
- **User Activity:** Captured in `models/user_activity.py`, tracking user interactions and course progress.
- **User Course Activity:** Detailed in `models/user_course_activity.py`, mapping user progress across different courses.

### API Endpoints

API endpoints are defined in `urls.py` and implemented in the respective view modules:
- **Udemy Data Endpoints:** Handled by `views/udemy_api.py`, providing access to course and user data.
- **User Activity Endpoints:** Managed by `views/user_activity.py` and `views/user_course_activity.py`, exposing data relevant to user interactions and course activities.
- **Report Endpoints:** Included in `views/reports.py`, allowing users to access generated reports.

### Additional Components

- **Admin Configuration:** Managed by `admin.py` for data model administration.
- **Serializers:** Located in `serializers/`, transforming complex data types into JSON and vice versa.
- **Utilities:** Utility functions and classes are defined in `utils/`, including custom authentication and cloud task management.
- **Testing:** Test cases are implemented in `tests.py`, ensuring the robustness and reliability of the backend logic.


---

## Frontend (Angular)

### Application Overview
Provide a detailed overview of the frontend application.

### Core Features
Explain the main features and functionality provided in the frontend.

### Routing
Describe the routing configuration and structure.

### Component Hierarchy
Outline the component hierarchy and architecture.

### Styling
Discuss the styling approach, including custom styles and the use of the Fuse theme.

---

## Deployment

### Docker Setup
Instructions on how to set up and use Docker for the application.

### Environment Variables
List and explain the required environment variables.

### Production Considerations
Discuss considerations and configurations for deploying to a production environment.

### CI/CD Pipeline
Overview of the CI/CD pipeline setup for the application.

---

## Testing

### Unit Tests
Explain the unit testing strategy and coverage.

### Integration Tests
Discuss integration testing and how different parts of the application are tested together.

---

## Contributing

### Code of Conduct
Outline the expected behavior and code of conduct for contributors.

### Contribution Guidelines
Provide guidelines on how to contribute to the project.

---

## License
Include licensing information for the project.
