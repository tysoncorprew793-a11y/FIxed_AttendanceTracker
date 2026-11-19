# NSU Smart Attendance Tracker

**Course:** CSC 380 – Software Engineering  
**Institution:** Norfolk State University  
**Team Name:** Trust The Process  
**Project Status:** In Development

## Project Overview

The NSU Smart Attendance Tracker is a web-based application designed to improve classroom attendance management for students and professors at Norfolk State University.

The project aims to replace traditional manual attendance methods with a digital system that allows professors to create attendance sessions and students to check in using QR codes.

By automating attendance tracking, the system aims to reduce classroom interruptions, improve record accuracy, and make attendance information easier to access and manage.

## Team Members

- **Tyson Corprew** – Project Coordinator, UML Design, and Presentation Lead
- **Carissa Cuffee** – Requirements and Documentation Lead
- **Jason Kennedy** – Implementation, Database, and Testing Lead

## Major Features

### Student and Professor Interfaces
Separate interfaces designed for students and professors, with features based on their responsibilities.

### QR Code Attendance
Professors can create attendance sessions that students can access by scanning QR codes.

### Attendance Management
Professors can view attendance records and track students as present or absent.

### Student Attendance History
Students can review their attendance history for their courses.

### Attendance Reports
Professors can generate attendance reports and export records as CSV files.

### Course Management
Professors can organize attendance sessions by course.

### Attendance Validation
Planned validation measures to reduce duplicate or unauthorized check-ins.

## Technologies Used

The project is currently being developed using:

- **Bolt** – Primary web-based development environment
- **React** – User interface development
- **TypeScript** – Application programming
- **HTML and CSS** – Page structure and styling
- **JavaScript** – Interactive functionality
- **Git and GitHub** – Version control and team collaboration

The project was originally prototyped in StackBlitz before development moved to Bolt.

Data storage and backend technologies are being evaluated and refined as development continues.

## Installation and Setup

### Running the Project in Bolt

1. Open the NSU Smart Attendance Tracker project in Bolt.
2. Access the project's development workspace.
3. Start or open the application preview.
4. Test the available student and professor features.

### Running the Project Locally

If the repository contains the React project files and a `package.json` file:

1. Install Node.js and npm.
2. Clone the GitHub repository:

   ```bash
   git clone <repository-url>
   ```

3. Open the downloaded project folder:

   ```bash
   cd <repository-folder>
   ```

4. Install the dependencies:

   ```bash
   npm install
   ```

5. Start the development server:

   ```bash
   npm run dev
   ```

6. Open the local address shown in the terminal.

These local instructions assume the project uses npm and has a development script configured.

## How to Use the Application

### For Professors

1. Open the application and access the professor interface.
2. Select a course or attendance session.
3. Generate or display an attendance QR code.
4. Allow students to check in.
5. Review attendance records.
6. Export attendance reports when available.

### For Students

1. Open the application or scan the attendance QR code.
2. Enter the required student information.
3. Submit the attendance check-in.
4. Review attendance information when the feature is available.

## Current Project Status

The NSU Smart Attendance Tracker is currently in the development and testing phase.

The team has completed work on project requirements, user stories, UML diagrams, software architecture planning, and initial application prototyping.

Development began in StackBlitz and later moved to Bolt to continue improving the application.

Current priorities include refining the student and professor interfaces, improving QR code check-in, testing attendance record accuracy, and strengthening data management.

Not all planned features are fully implemented or tested.

## Known Issues and Limitations

- QR code validation and duplicate check-in prevention require additional testing.
- Secure authentication and role-based access controls need to be verified before production use.
- Data persistence and database integration require further verification.
- CSV attendance exports need continued testing.
- The application is still a prototype and is not ready for production use with real student records.

## GitHub Collaboration Workflow

GitHub is used to organize project files, track changes, and support team collaboration.

The team's intended workflow includes:

1. Creating GitHub issues for project tasks.
2. Assigning tasks to team members.
3. Creating feature branches for individual changes.
4. Committing changes with descriptive messages.
5. Pushing updated branches to GitHub.
6. Creating pull requests for proposed changes.
7. Reviewing changes before merging.
8. Merging accepted changes into the main branch.

This process helps maintain organized development and provides a record of individual contributions.

## Future Improvements

- Improve secure student and professor authentication.
- Add stronger QR code validation and expiration.
- Improve centralized attendance data storage.
- Expand attendance reporting and CSV exports.
- Improve mobile accessibility.
- Strengthen privacy and security protections.
- Complete additional functionality and usability testing.

## Project Purpose

The NSU Smart Attendance Tracker demonstrates how software engineering principles can be used to solve a practical problem in a university environment.

Through this project, Team Trust The Process is applying requirements engineering, UML modeling, software architecture, application development, testing, and version control to create a more efficient attendance management system.

---

**Norfolk State University**  
**CSC 380 – Software Engineering**  
**Team Trust The Process**
