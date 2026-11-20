# AI-Based Public Complaint Prioritization and Resolution Management System

An AI-powered public complaint management platform that helps government departments classify complaints, predict severity, identify potential duplicates, analyze uploaded images, and prioritize complaints for efficient resolution.

## 📌 Project Overview

Traditional public complaint management systems often rely on manual complaint classification and processing. This can make it difficult to identify urgent complaints, recognize similar issues, and assign complaints to the appropriate departments.

This project introduces an AI-assisted complaint management system that integrates machine learning, semantic similarity detection, image analysis, and rule-based prioritization into a unified platform.

Citizens can submit complaints through a web portal by providing a description, location, and optional image. The system analyzes the submitted information, predicts the complaint category and severity, identifies potential duplicate complaints, calculates a priority score, and maps the complaint to the appropriate department.

Government staff can access a dedicated dashboard to review complaints and manage their resolution status.

## 🎯 Project Objectives

- Provide an easy-to-use platform for citizens to submit public complaints.
- Automatically classify complaints into relevant categories.
- Predict complaint severity using machine learning.
- Identify potentially duplicate complaints using semantic similarity.
- Analyze uploaded complaint images using a vision-language model.
- Calculate complaint priority using configured business rules.
- Map complaints to the appropriate government departments.
- Provide a centralized dashboard for complaint monitoring and management.
- Store complaint records and analysis results in a relational database.
- Send email confirmations to citizens after complaint submission.

## ✨ Key Features

### 1. Citizen Portal
- User registration and login.
- Submit complaints using text descriptions.
- Provide complaint location details.
- Upload supporting images.
- Track complaint status.

### 2. AI-Based Complaint Classification
- Automatically predicts complaint categories.
- Uses TF-IDF feature extraction and Logistic Regression.
- Supports word-level and character-level text features.

### 3. Severity Prediction
- Predicts complaint severity levels such as Low, Medium, and High.
- Uses unigram and bigram TF-IDF features with Logistic Regression.

### 4. Duplicate Complaint Detection
- Uses Sentence Transformers (`all-MiniLM-L6-v2`).
- Generates semantic embeddings from complaint descriptions.
- Compares complaint similarity to identify potential duplicates.
- Uses a configured similarity threshold of 0.70.

### 5. Image Analysis
- Uses SigLIP2 for zero-shot image analysis.
- Compares uploaded images with candidate text descriptions.
- Provides image–text matching scores to support complaint analysis.

### 6. Complaint Prioritization
- Calculates a priority score using configured backend rules.
- Uses AI analysis results as inputs to the complaint-processing workflow.
- Supports prioritization and organized complaint review.

### 7. Department Mapping
Maps predicted complaint categories to relevant departments, including:

| Complaint Category | Assigned Department |
|---|---|
| Road / Pothole / Road Damage | Roads & Infrastructure Department |
| Water Supply | Water Supply Department |
| Garbage / Waste / Sanitation | Sanitation & Solid Waste Department |
| Streetlight | Street Lighting Department |
| Drainage / Sewage | Drainage & Sewage Department |
| Electricity / Power | Electrical Department |
| Traffic / Illegal Parking | Traffic & Transport Department |
| Unknown / Other Categories | General Civic Services |

### 8. Government Dashboard
- View submitted complaints.
- Review AI-generated analysis.
- View complaint categories and severity.
- Monitor prioritized complaints.
- Update complaint resolution status.
- Manage complaint records.

### 9. Email Notifications
- Sends complaint confirmation emails.
- Supports notification functionality within the complaint workflow.

## 🧠 AI Models and Machine Learning

The project integrates four main AI components.

| AI Component | Model / Technique | Purpose |
|---|---|---|
| Complaint Classification | TF-IDF + Logistic Regression | Predict complaint category |
| Severity Prediction | TF-IDF + Logistic Regression | Predict complaint severity |
| Duplicate Detection | Sentence Transformers – all-MiniLM-L6-v2 | Semantic similarity comparison |
| Image Analysis | SigLIP2 | Zero-shot image–text matching |

### Model Evaluation Results

The following are the reported held-out test accuracies for the two classification models.

| Model | Test Accuracy |
|---|---:|
| Complaint Category Classification | 97.03% |
| Severity Prediction | 91.67% |

**Note:** These accuracy values apply to their respective classification test sets. They do not represent the overall accuracy of the complete application. Duplicate similarity and image–text matching scores are not calibrated probabilities.

## 🏗️ System Architecture

The application follows a layered architecture consisting of frontend, backend, AI services, database, and notification components.

### Architecture Components

1. **Frontend Layer:** React and Vite-based citizen portal and government dashboard.
2. **Backend Layer:** Java 21 and Spring Boot services for authentication, complaint processing, business logic, and API integration.
3. **AI Service Layer:** Python and Flask-based service for model inference.
4. **Data Layer:** PostgreSQL database for storing application and complaint information.
5. **Notification Layer:** Email service for complaint confirmation and related notifications.

### Overall Workflow

1. Citizen submits a complaint through the React portal.
2. The Spring Boot complaint service receives and validates the request.
3. The backend communicates with the Flask AI service.
4. The AI service performs category classification and severity prediction.
5. Duplicate detection checks for semantically similar complaints.
6. SigLIP2 analyzes the image when an image is provided.
7. The backend applies department-mapping and priority rules.
8. Complaint details and available analysis results are stored in PostgreSQL.
9. An email confirmation is sent to the citizen.
10. Government staff review complaints and update their status through the dashboard.

## 🛠️ Technology Stack

| Layer | Technologies |
|---|---|
| Frontend | React.js, Vite, JavaScript, HTML, CSS |
| Backend | Java 21, Spring Boot |
| AI / ML | Python, Scikit-learn, TF-IDF, Logistic Regression |
| Semantic Similarity | Sentence Transformers, all-MiniLM-L6-v2 |
| Image Analysis | SigLIP2 |
| AI API | Flask |
| Database | PostgreSQL |
| ORM / Persistence | Spring Data JPA, Hibernate |
| Build Tools | Maven, npm |
| Development Environment | Visual Studio Code |
| Version Control | Git, GitHub |

## 📂 Project Structure

```text
AI-Public-Complaint-System/
│
├── ai/
│   ├── complaint-classification/
│   │   ├── data/
│   │   ├── predict.py
│   │   ├── train_model.py
│   │   ├── improve_dataset.py
│   │   ├── expand_dataset.py
│   │   └── complaint_classifier.joblib
│   │
│   ├── severity-prediction/
│   │   ├── data/
│   │   ├── predict.py
│   │   ├── train_model.py
│   │   └── severity_model.joblib
│   │
│   ├── duplicate-detection/
│   │   └── duplicate_detector.py
│   │
│   ├── image-analysis/
│   │   ├── evaluate_images.py
│   │   └── test_image_model.py
│   │
│   ├── integration/
│   │   ├── ai_api.py
│   │   └── ai_pipeline.py
│   │
│   └── priority-engine/
│       └── priority_engine.py
│
├── backend/
│   ├── auth-service/
│   │   └── src/
│   │
│   ├── complaint-service/
│   │   └── src/
│   │
│   └── notification-service/
│
├── frontend/
│   ├── citizen-portal/
│   │   └── src/
│   │
│   └── government-dashboard/
│       └── src/
│
├── database/
├── datasets/
├── deployment/
├── diagrams/
├── documentation/
├── research/
├── testing/
│
├── start_project.bat
└── README.md
```

## ⚙️ Installation and Setup

### Prerequisites

Install the following software before running the project:

- Java 21
- Python 3.10 or compatible version
- Node.js and npm
- PostgreSQL
- Maven (or use the included Maven wrapper)
- Visual Studio Code (recommended)

### 1. Clone the Repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd AI-Public-Complaint-System
```

### 2. Configure PostgreSQL

1. Install and start PostgreSQL.
2. Create the project database:

```sql
CREATE DATABASE public_complaint_db;
```

3. Configure the database connection in the relevant backend `application.properties` file.
4. Set database credentials through environment variables or local configuration.

### 3. Configure the Python AI Service

Open the AI integration directory:

```bash
cd ai/integration
```

Create and activate a Python virtual environment:

```bash
python -m venv venv
```

Windows:

```bash
venv\Scripts\activate
```

Install the Python dependencies listed in the project's dependency file, if provided.

Run the AI service:

```bash
python ai_api.py
```

The Flask AI service is configured to run on port `5000`.

### 4. Run the Spring Boot Backend

Open the complaint service directory:

```bash
cd backend/complaint-service
```

Windows:

```bash
.\mvnw.cmd spring-boot:run
```

The complaint service uses port `8080`.

Run the authentication service separately from:

```text
backend/auth-service
```

Its configured port is `8081`.

### 5. Run the Citizen Portal

Open a terminal:

```bash
cd frontend/citizen-portal
npm install
npm run dev
```

The citizen portal runs on:

```text
http://localhost:5173
```

### 6. Run the Government Dashboard

Open another terminal:

```bash
cd frontend/government-dashboard
npm install
npm run dev
```

The government dashboard runs on:

```text
http://localhost:5174
```

### 7. Start the Project

The project root contains a startup script:

```text
start_project.bat
```

It can be used to start the configured project services. Ensure the database and required dependencies are configured before running it.

**Important:** Update any local environment variables, database credentials, email settings, and service URLs before starting the application.

## 🧪 Testing and Evaluation

The project includes testing and evaluation components for:

- Complaint category classification.
- Severity prediction.
- Duplicate complaint detection.
- Image analysis.
- Complaint submission and processing.
- Dashboard operations.
- Complaint status updates.
- Email confirmation.

Model evaluation results should be interpreted separately from complete application testing results.

## 🔒 Security Considerations

- Do not commit database passwords, API keys, email credentials, or secret tokens.
- Keep local environment files out of version control.
- Use environment variables for sensitive configuration.
- Protect authentication endpoints and restrict dashboard access.
- Do not upload virtual environments, dependency folders, or generated build files to GitHub.

## 🚀 Future Scope

- Evaluate models using larger and more diverse real-world complaint datasets.
- Improve model generalization across different locations and complaint descriptions.
- Calibrate confidence and similarity scores where appropriate.
- Expand multilingual complaint support.
- Improve complaint analytics and reporting.
- Evaluate the system under larger deployment workloads.
- Integrate additional government service workflows.

## 🎓 Project Information

| Field | Details |
|---|---|
| Project Title | AI-Based Public Complaint Prioritization and Resolution Management System |
| Student Name | Sachin V |
| Registration Number | 22MIS0303 |
| Guide | Bala Ganesh N |
| Programme | Integrated M.Tech Software Engineering |
| Institution | Vellore Institute of Technology (VIT) |

## 👨‍💻 Author

**Sachin V**

GitHub: [Sachin212004](https://github.com/Sachin212004)

---

*Developed as an academic final-year project to explore the integration of Artificial Intelligence, Machine Learning, semantic similarity, computer vision, and full-stack web development for public complaint management.*
