# EduHub MongoDB Project

## Project Overview

This project is part of the AltSchool of Data Engineering Tinyuka 2024 Second Semester Exam. The goal is to design and implement a comprehensive MongoDB database system for an online e-learning platform called **EduHub**. This system supports user management, course administration, enrollments, assessments, analytics, and performance optimization using MongoDB and Python.

## Technologies Used

- **MongoDB v8.0+** (Compass & Shell)
- **Python 3.x**
- **PyMongo**
- **pandas**
- **datetime**
- **Jupyter Notebook**

## Repository Structure

mongodb-eduhub-project/
│
├── README.md # Project documentation
├── .gitignore # Git ignore rules
│
├── notebooks/
│ └── eduhub_mongodb_project.ipynb # Jupyter notebook with all operations and outputs
│
├── src/
│ └── eduhub_queries.py # Python script with MongoDB queries (backup/reference)
│
├── data/
│ ├── sample_data.json # Exported JSON data for each collection
│ └── schema_validation.json # Validation rules for collections
│
├── docs/
│ ├── performance_analysis.md # Query performance and indexing documentation
│ └── presentation.pptx # 5–10 slide summary of project design


---

## Setup Instructions

### 1. Clone Repository

```bash
git clone https://github.com/Tomx01/mongodb-eduhub-project.git
cd mongodb-eduhub-project

2. Install Dependencies
Create a virtual environment and install required packages:

pip install pymongo pandas notebook

3. Start MongoDB
Ensure MongoDB server is running locally or connect to MongoDB Atlas.

4. Launch Notebook

jupyter notebook notebooks/eduhub_mongodb_project.ipynb

Functional Features
✅ User Management
Student & instructor registration

Authentication and profile updates

✅ Course Management
Create, update, publish courses

Organize content into lessons and assignments

✅ Enrollment System
Student enrollment tracking

Completion and progress records

✅ Assessment System
Assignments and student submissions

Instructor grading and feedback

✅ Analytics & Reporting
Performance metrics

Revenue and enrollment trends

✅ Search & Discovery
Filter and search courses by title, tags, and category

Key Components
🗃️ Schema Design
Collections:

users – for students and instructors

courses – with metadata and instructors

enrollments – for student-course relationships

lessons – each course has multiple lessons

assignments – linked to lessons/courses

submissions – records of student submissions

Includes validation rules and referential fields.

🔄 CRUD Operations
Implemented with PyMongo and verified via output in notebook:

Create new documents

Read and filter data

Update and manage records

Delete or soft-delete entries

📊 Aggregation & Analytics
Course enrollment counts

Average grades

Monthly engagement

Revenue per instructor

Completion trends

⚙️ Indexing & Optimization
Indexes on user email, course title, tags, and due dates

Query optimization via .explain() and timeit

Performance improvement documentation included

Sample Data
Sample data for all six collections is available in data/sample_data.json. Use MongoDB Compass or PyMongo to import and view.

Performance Analysis
See docs/performance_analysis.md for:

Before/after query performance using .explain()

Indexes created

Timing improvements

Presentation
A short presentation highlighting the system’s design, queries, and analysis is included in docs/presentation.pptx.

License
This project is open-source under the MIT License.

Author
Your Adegunju Hammed Adetomiwa
AltSchool of Data Engineering – Tinyuka 2024

Submission Checklist ✅
 GitHub repository with all files

 README.md with setup instructions and overview

 Jupyter notebook executed with results

 Sample data in JSON format

 Slide presentation included

 ZIP archive prepared as backup

 🔗 Repository
GitHub: https://github.com/Tomx01/mongodb-eduhub-project.git