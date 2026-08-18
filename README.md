# Student Enrollment Management System using JsonPowerDB

A lightweight, responsive, and beginner-friendly web application for managing student enrollment records built as a micro project for the course **"Introduction to JsonPowerDB V2.0"** by **Login2Xplore**.

---

## Description

The **Student Enrollment Management System** allows educational institutions to enroll new students, view existing student details by Roll Number, and update information seamlessly. The application leverages **JsonPowerDB (JPDB)** as a serverless backend database, interacting with it directly through JavaScript REST API requests without requiring any server-side programming language (like PHP, Node.js, Python, etc.).

---

## Benefits of using JsonPowerDB

* **Simple REST API**: Perform CRUD operations easily using HTTP methods directly from client-side JavaScript.
* **Lightweight & Fast**: Extremely quick responses due to memory-centric database architecture.
* **Serverless Development**: Zero backend server setup or database administration required.
* **JSON-native**: Data is stored natively in JSON format, eliminating translation layers between frontend and backend.
* **Easy Web Integration**: Integrates directly with frontend web applications via AJAX and standard HTTP libraries.
* **Minimal Configuration**: No schema definitions required before inserting or retrieving data.

---

## Features

* **Add Student**: Insert new student records into the database with automatic primary key check.
* **Roll Number Lookup**: Automatically checks if a Roll Number already exists upon unfocusing (`onblur`) the Roll Number field.
* **Retrieve Student**: Automatically populates all form fields if the Roll Number exists in the database.
* **Update Student**: Enables updating existing student details while keeping the Roll Number read-only, using JPDB's internal record number (`rec_no`).
* **Form Validation**: Client-side validation ensuring valid email formatting, exactly 10-digit mobile numbers, and non-empty mandatory fields.
* **Duplicate Prevention**: Prevents duplicate insertions for existing Roll Numbers by dynamically controlling button states (`Save` vs `Update`).
* **Responsive UI**: Built with Bootstrap 5 for optimal viewing across mobile, tablet, and desktop devices.

---

## Technologies Used

* **HTML5**: Semantic markup and form layout.
* **CSS3 & Bootstrap 5**: Clean, modern, responsive styling and layout.
* **Vanilla JavaScript & jQuery**: Form handling, DOM manipulation, and validation logic.
* **JsonPowerDB**: Relational JSON database engine for cloud data management.
* **`jpdb-commons.js`**: Login2Xplore's helper library for building JPDB API requests.

---

## JsonPowerDB Configuration

### Steps to Configure Token:

1. Register or log in to your **[Login2Xplore / JsonPowerDB](https://login2explore.com)** account.
2. Navigate to your Developer Dashboard and obtain your **Connection Token**.
3. Open `js/script.js` in your text editor.
4. Locate the configuration block at the top of the file:

```javascript
const JPDB_BASE_URL = "http://api.login2explore.com:5577";
const JPDB_TOKEN = "YOUR_CONNECTION_TOKEN_HERE";
const DB_NAME = "SCHOOL-DB";
const RELATION_NAME = "STUDENT-TABLE";
```

5. Replace `"YOUR_CONNECTION_TOKEN_HERE"` with your actual Connection Token.

> [!WARNING]
> **Security Notice**: Never commit a real private connection token to a public GitHub repository. Before pushing your code to a public repository, reset the `JPDB_TOKEN` value back to `"YOUR_CONNECTION_TOKEN_HERE"` or follow Login2Xplore's recommended token security guidelines.

---

## Database Structure

* **Database Name**: `SCHOOL-DB`
* **Relation (Table) Name**: `STUDENT-TABLE`
* **Primary Key Index**: `rollNo`

### Example Student JSON Document:

```json
{
  "rollNo": "101",
  "name": "Chetanya Kumar",
  "course": "BCA",
  "email": "student@example.com",
  "mobile": "9876543210",
  "city": "Mathura",
  "enrollmentDate": "2026-08-18"
}
```

---

## CRUD / API Operations

This project utilizes standard JsonPowerDB API endpoints and commands:

| Operation | JPDB API Endpoint | JPDB Helper Function | Purpose |
| :--- | :--- | :--- | :--- |
| **Retrieve (GET)** | `/api/irl` | `createGET_BY_KEYRequest()` | Fetches student details using `rollNo` |
| **Create (PUT)** | `/api/iml` | `createPUTRequest()` | Inserts a new student record into `STUDENT-TABLE` |
| **Update (UPDATE)** | `/api/iml` | `createUPDATERecordRequest()` | Updates student record using internal `rec_no` |

---

## How to Run

1. Clone or download this project repository.
2. Open the project folder in **Visual Studio Code**.
3. Open `js/script.js` and add your JsonPowerDB token.
4. Right-click `index.html` and select **"Open with Live Server"** (or use any standard static HTTP web server).
5. Open your browser and navigate to `http://127.0.0.1:5500`.

---

## Screenshots

### Student Enrollment Form
![Student Enrollment Form](screenshots/form_entry.png)

### Record Retrieved
![Record Retrieved](screenshots/record_retrieved.png)

### Record Updated
![Record Updated](screenshots/record_updated.png)

---

## Project Status

This project was developed as a micro project submission for the **"Introduction to JsonPowerDB V2.0"** course by **Login2Xplore**.
