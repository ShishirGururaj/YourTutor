# YourTutor - Online Tutor and Tuition Management Platform

A database-driven web application developed as an academic mini-project for the **15CSL58 - DBMS Laboratory** course under **Bachelor of Engineering in Information Science at Visvesvaraya Technological University (VTU)**.

The project, **YourTutor**, provides a web-based platform for connecting students and guardians with tutors. It allows users to register according to their role, search for tutors, submit tuition requests, and access tutor information. Teachers can register their profiles and make their qualifications, subjects, and availability discoverable to users.

The application demonstrates the use of **PHP, MySQL, HTML, CSS, JavaScript, jQuery, AJAX, and database-driven web application development**.

---

## Overview

YourTutor is designed as a simplified online platform for managing private tutoring and tuition requests.

The application supports three primary user roles:

* **Students**
* **Teachers / Tutors**
* **Guardians**

An additional administrative interface is provided for managing tutor information.

The platform connects users looking for tuition with tutors who provide tutoring services.

Users can:

* Register an account
* Log in and log out
* Search for tutors
* View tutor details
* Submit tuition requests
* Browse tutor availability and qualifications

Teachers can:

* Register as tutors
* Provide qualification information
* Specify subjects taught
* Provide contact details
* Specify areas of availability

Guardians can:

* Register on the platform
* Search for tutoring options
* Submit tuition requests

---

## Features

### User Authentication

The application provides a common login workflow for registered users.

Users authenticate using:

* Email
* Password

The application identifies the user's role and redirects them to the corresponding user interface.

Supported roles include:

* Student
* Teacher
* Guardian

The application uses PHP sessions to maintain login state.

---

### Student Registration

Students can create an account by providing information including:

* Name
* Email / Username
* Mobile number
* Password
* Class
* Institute name

The registration workflow uses client-side validation and AJAX to submit registration data to the backend.

---

### Teacher Registration

Teachers can register as tutors by providing:

* Name
* Email
* Mobile number
* Password
* Qualification

The application validates user input before submitting the registration request.

Registered teachers can later access their teacher dashboard and view their account information.

---

### Guardian Registration

Guardians can register on the platform and create an account for accessing tutoring-related services.

The guardian workflow allows the platform to support users seeking tutors on behalf of students.

---

### Tutor Profiles

Tutor information includes:

* Name
* Qualification
* Subjects taught
* Area of availability
* Email address
* Mobile number

The platform provides a tutor details page that displays publicly available tutor information.

Contact information is intended to be available only to authenticated users.

Unauthenticated users are prompted to log in before accessing further contact details.

---

### Tutor Search

Users can search for available tutors through the tutor search functionality.

Tutor profiles can be explored to view information about:

* Qualifications
* Subjects offered
* Areas of availability
* Contact information

---

### Tuition Requests

Students or guardians can submit requests for tutoring services.

A tuition request can contain:

* Name
* Email
* Mobile number
* Subject
* Student class
* Preferred tutor qualification
* Preferred area
* Honorarium / expected payment

Submitted requests are stored in the database and can be viewed through the tutor-request functionality.

---

### Tutor Request Search

Tutors can browse available tuition requests to identify potential tutoring opportunities.

The request information includes details such as:

* Requested subject
* Preferred qualification
* Student class
* Area
* Honorarium

Users can select an individual request to view additional details.

---

### Teacher Dashboard

Authenticated teachers can access a teacher panel displaying their account information.

The dashboard displays:

* Teacher name
* Qualification
* Email
* Mobile number

The teacher can also log out from the dashboard.

---

### Student Dashboard

Authenticated students can access a student administration interface.

The student dashboard is intended to provide student-specific access to the platform.

---

### Guardian Dashboard

Authenticated guardians can access a guardian administration interface.

The guardian dashboard provides a role-specific interface for guardians using the platform.

---

### Admin Panel

The project includes an administrative interface for managing tutor information.

The administrator can add tutor information including:

* Name
* Email
* Mobile number
* Qualification
* Subject
* Area of availability

Tutor information is submitted asynchronously using AJAX.

---

## Technology Stack

| Technology | Purpose                                    |
| ---------- | ------------------------------------------ |
| PHP        | Server-side application logic              |
| MySQL      | Database management and persistent storage |
| HTML       | Web page structure                         |
| CSS        | Application styling                        |
| JavaScript | Client-side functionality                  |
| jQuery     | DOM manipulation and AJAX requests         |
| AJAX       | Asynchronous form submissions              |
| Bootstrap  | Responsive UI components                   |

---

## Architecture

The application follows a traditional PHP-based, database-driven web application architecture.

```text id="z0g4me"
                         ┌─────────────────────┐
                         │       Browser       │
                         │                     │
                         │  HTML / CSS / JS    │
                         └──────────┬──────────┘
                                    │
                                    │ HTTP Requests
                                    ▼
                         ┌─────────────────────┐
                         │     PHP Backend     │
                         │                     │
                         │ Authentication      │
                         │ Registration        │
                         │ Tutor Management    │
                         │ Tutor Search        │
                         │ Tuition Requests    │
                         │ Session Management  │
                         └──────────┬──────────┘
                                    │
                                    │ MySQL Queries
                                    ▼
                         ┌─────────────────────┐
                         │   MySQL Database    │
                         │                     │
                         │ Users               │
                         │ Students            │
                         │ Teachers            │
                         │ Guardians           │
                         │ Tutor Profiles      │
                         │ Tutor Requests      │
                         └─────────────────────┘
```

---

## User Roles

### Student

A student can:

* Register an account
* Log in
* Search for tutors
* View tutor profiles
* View tutor contact information after authentication
* Submit tuition requests

---

### Teacher / Tutor

A teacher can:

* Register as a tutor
* Provide qualification details
* Specify subjects taught
* Specify availability
* View their account information
* Browse tuition requests

---

### Guardian

A guardian can:

* Register an account
* Log in
* Search for tutors
* Submit tuition requests
* Access guardian-specific functionality

---

### Administrator

The administrator can:

* Access the admin panel
* Add tutor records
* Provide tutor qualification information
* Specify subjects and areas of availability

---

## Database

The application uses a MySQL database named:

```text id="6z4q5v"
bdtutor
```

The database is referenced throughout the project through the central database configuration.

The application source code indicates the use of tables representing several entities in the tutoring platform.

### `user`

Stores authentication and role information.

The application associates user accounts with:

* Email
* Password
* User type

Supported user types include:

```text id="m3q5h7"
student
teacher
guardian
```

---

### `teacher`

Stores teacher or tutor account information.

The source code indicates fields including:

```text id="m4o2i0"
name
mobile
password
email
qualification
```

---

### `student`

Stores student registration information.

The registration workflow captures information including:

* Name
* Username / email
* Mobile number
* Class
* Password
* Institute name

---

### `guardian`

Stores guardian registration information.

Guardian accounts are used to support users seeking tutoring services.

---

### `add_tutor`

Stores tutor profile information.

The application uses fields including:

```text id="h2h9n0"
id
name
qualification
subjects_taught
available_at
img
mobile
email
```

This table represents tutor profiles available through the platform.

---

### `tutor_request`

Stores tuition requests submitted by students or guardians.

The application uses information including:

```text id="5x8f9j"
name
mobile
email
class
subject
t_qualification
area
honorary
```

These records represent tutoring requirements that teachers can browse.

---

## Application Flow

```text id="h1v9j6"
                           Start
                             │
                             ▼
                       Open YourTutor
                             │
                             ▼
                     Register / Login
                             │
             ┌───────────────┼────────────────┐
             │               │                │
             ▼               ▼                ▼
          Student         Teacher          Guardian
             │               │                │
             ▼               ▼                ▼
       Search Tutors    Create Profile    Search Tutors
             │               │                │
             ▼               │                ▼
      View Tutor Details     │         Submit Tutor Request
             │               │                │
             ▼               ▼                │
      Submit Request    Browse Requests      │
             │               │                │
             └───────────────┴────────────────┘
                             │
                             ▼
                    Tutor / Tuition Matching
```

---

## Project Structure

The recommended repository structure is:

```text id="8x3jkd"
YourTutor/
├── README.md
│
├── database/
│   └── bdtutor.sql
│
├── src/
│   ├── index.php
│   ├── about.php
│   ├── contact.php
│   ├── login.php
│   ├── logout.php
│   ├── studentreg.php
│   ├── teacherreg.php
│   ├── gurdianreg.php
│   ├── searchtutor.php
│   ├── searchtuition.php
│   ├── detailstutor.php
│   ├── detailstutorreq.php
│   ├── tutor_req.php
│   ├── panel.php
│   ├── admin.php
│   ├── studentadmin.php
│   ├── teacheradmin.php
│   └── gurdianadmin.php
│
├── includes/
│   ├── constant.php
│   ├── header.php
│   ├── footer.php
│   ├── loginprocess.php
│   ├── addtutordata.php
│   ├── studentreg.php
│   ├── treacherreg.php
│   └── logout.php
│
├── assets/
    ├── css/
    │   ├── style.css
    │   └── grid.min.css
    ├── js/
    │   ├── jquery-2.js
    │   └── validate.js
    └── images/
        ├── 2.jpg
        ├── 3.jpg
        ├── 4.jpg
        ├── 5.jpg
        ├── 6.jpg
        ├── 7.jpg
        ├── 10.jpg
        ├── bg1.jpg
        ├── contact.png
        └── img_avatar.png

```

> **Important:** The supplied archive does not include the SQL database dump referenced by the project instructions. The database schema should be recovered or exported from the original development environment before publishing the repository as a fully reproducible project.

---

## Local Setup

### Prerequisites

Install:

* PHP
* MySQL
* Apache or another PHP-compatible web server
* A web browser

The project can be hosted using a local development environment such as:

* XAMPP
* WAMP
* MAMP
* LAMP

---

### 1. Clone the Repository

```bash id="e7e2k3"
git clone <repository-url>
cd YourTutor
```

---

### 2. Create the Database

Create a MySQL database named:

```text id="b0u9u7"
bdtutor
```

Import the project's SQL dump into the database.

For example:

```bash id="6v1h0d"
mysql -u root -p bdtutor < database/bdtutor.sql
```

> The SQL dump is not included in the supplied project archive and must be recovered or recreated before this command can be used.

---

### 3. Configure the Database Connection

Update:

```text id="l9w2k4"
includes/constant.php
```

with the appropriate local MySQL configuration.

The original application expects a configuration similar to:

```text id="j7m1q8"
Host: localhost
Username: root
Password: ""
Database: bdtutor
```

The exact credentials depend on the local MySQL installation.

---

### 4. Start the Web Server

Place the project in the web server's document root.

For example, with XAMPP:

```text id="w5g7m2"
htdocs/
└── YourTutor/
```

Start:

* Apache
* MySQL

Then open the application in a browser.

---

## Example Workflows

### Student Looking for a Tutor

```text id="u6v8p2"
Register as Student
        │
        ▼
      Login
        │
        ▼
 Search Available Tutors
        │
        ▼
 Select Tutor
        │
        ▼
 View Tutor Details
        │
        ▼
 Contact Information
```

---

### Student or Guardian Requesting a Tutor

```text id="g5d1v9"
Register / Login
       │
       ▼
Submit Tuition Request
       │
       ├── Subject
       ├── Student Class
       ├── Qualification
       ├── Area
       └── Honorarium
       │
       ▼
Request Stored in Database
       │
       ▼
Tutor Searches Available Requests
```

---

### Teacher Registering as a Tutor

```text id="r4k8p1"
Register as Teacher
       │
       ▼
Provide Qualification
       │
       ▼
Provide Contact Information
       │
       ▼
Teacher Account Created
       │
       ▼
Access Teacher Panel
```

---

## AJAX Integration

The application uses jQuery AJAX requests for selected registration and administrative operations.

The general workflow is:

```text id="a8s4m0"
User Completes Form
        │
        ▼
Client-Side Validation
        │
        ▼
jQuery AJAX Request
        │
        ▼
PHP Processing Script
        │
        ▼
MySQL Database
        │
        ▼
Response Returned
        │
        ▼
Result Displayed Without Full Page Reload
```

This approach is used in functionality such as:

* Student registration
* Teacher registration
* Guardian registration
* Tutor requests
* Adding tutor records

---

## Security Considerations

This project was developed as an academic DBMS Laboratory project and should not be considered production-ready.

Areas requiring improvement include:

* Passwords should be securely hashed using modern password hashing functions.
* SQL queries should use prepared statements.
* User input should be validated and sanitized on the server.
* Session checks should be implemented consistently.
* Authorization should be enforced for every protected resource.
* User-controlled IDs should be validated before being used in database queries.
* CSRF protection should be added to state-changing forms.
* Database credentials should be stored outside the source code.
* Error messages should not expose SQL queries or database details.

The original implementation uses direct SQL string interpolation and stores passwords directly, which are appropriate topics to identify as areas for improvement when discussing the project today.

---

## Known Limitations

The supplied academic project has several limitations:

* The SQL database dump is not included in the provided project archive.
* The source code expects a directory structure involving `inc/`, `images/`, and `js/` directories that does not match the supplied archive structure.
* Some filenames contain spelling inconsistencies such as `gurdian` and `treacherreg`.
* The application relies on direct SQL queries constructed from input values.
* Passwords are not securely hashed in the original implementation.
* The application does not implement a modern role-based authorization framework.
* There is no dedicated payment system.
* There is no automated tutor matching or recommendation engine.
* There is no messaging or real-time communication system between students and tutors.
* There is no scheduling or calendar management functionality.
* There is no formal booking or lesson management workflow.

---

## Potential Improvements

A modern version of YourTutor could introduce:

### Backend

* MVC architecture
* RESTful APIs
* Prepared statements
* Secure password hashing
* Role-based access control
* Centralized authentication
* Input validation and sanitization

### Database

* Normalized relational schema
* Foreign-key relationships
* Database constraints
* Dedicated user-role model
* Tutor availability tables
* Tutor subject mapping
* Tuition request status tracking

### Platform Features

* Tutor search by subject
* Location-based tutor search
* Tutor filtering by qualification
* Tutor ratings and reviews
* Tutor availability calendars
* Lesson scheduling
* Student-tutor messaging
* Application notifications
* Request acceptance and rejection workflows

### User Experience

* Responsive mobile-first interface
* Improved search and filtering
* Tutor profile pages
* Dashboard analytics
* Better form validation
* Improved error handling

---

## Academic Context

**Project:** YourTutor - Online Tutor and Tuition Management Platform
**Course:** 15CSL58 - DBMS Laboratory
**Institution:** Visvesvaraya Technological University (VTU)
**Project Type:** Undergraduate Mini Project

The project was developed as part of the DBMS Laboratory curriculum to demonstrate the application of database management concepts in a web-based system.

The application combines a PHP web interface with a MySQL database to manage users, tutor profiles, and tuition requests.
