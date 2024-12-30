Online Voting System for Student Council Project Overview This project is an Online Voting System designed for a student council election. The system ensures that each student can vote only once per position using their unique Student Number (USN). It is built using Java (NetBeans IDE) for the front end and MySQL for the database. Features

User Login: Students log in using their college email and password. Secure authentication to ensure only valid users access the system.

Unique Voting Process: Students vote using their USN. The system ensures that each student can vote only once for each position.

Database Integration: Candidate and vote information is stored in a MySQL database. Data integrity is maintained using foreign keys and constraints.

Position-Specific Voting: Allows voting for multiple positions. Ensures that a student can vote only once per position.

Technologies Used Programming Language: Java Integrated Development Environment (IDE): NetBeans Database Management System: MySQL

Installation Instructions Prerequisites Java Development Kit (JDK) NetBeans IDE MySQL Server and MySQL Workbench

Steps Clone the Repository: Clone the project from the repository or download the source files.

Set Up the Database: Create a new database in MySQL: CREATE DATABASE StudentCouncilVoting;

Use the provided SQL script to create the necessary tables: CREATE TABLE Students ( usn VARCHAR(20) PRIMARY KEY, email VARCHAR(100) UNIQUE NOT NULL, password VARCHAR(100) NOT NULL );

CREATE TABLE Candidates ( candidate_id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(100) NOT NULL, position VARCHAR(100) NOT NULL );

CREATE TABLE Votes ( vote_id INT AUTO_INCREMENT PRIMARY KEY, usn VARCHAR(20) NOT NULL, candidate_id INT NOT NULL, position VARCHAR(100) NOT NULL, timestamp DATETIME DEFAULT CURRENT_TIMESTAMP, FOREIGN KEY (usn) REFERENCES Students(usn), FOREIGN KEY (candidate_id) REFERENCES Candidates(candidate_id), UNIQUE (usn, position) );

Configure the Database Connection: Update the DatabaseConnection class with your MySQL credentials:

String url = "jdbc:mysql://localhost:3306/StudentCouncilVoting"; String user = "your_username"; String password = "your_password";

Run the Application: Open the project in NetBeans. Run the LoginForm class to start the application.

Usage Instructions Logging In Use a valid email and password registered in the Students table.

Voting Enter your USN in the voting form. Select a candidate for a specific position. Click "Vote" to submit your vote. The system checks if you have already voted for the selected position.

Database Structure Tables Students usn (Primary Key) email password Candidates candidate_id (Primary Key) name position Votes vote_id (Primary Key) usn (Foreign Key) candidate_id (Foreign Key) position timestamp Troubleshooting Common Errors

Database Connection Issues: Ensure the database credentials in DatabaseConnection are correct. Confirm that the MySQL server is running. Duplicate Vote Error: Check the Votes table’s UNIQUE (usn, position) constraint.

Failed to Record Vote: Ensure the USN and candidate IDs are valid. Check for null values in the Votes table.

Future Enhancements Admin Panel: Add functionality for administrators to manage candidates and view vote counts.

Vote Results: Display live results after voting closes.

Enhanced Security: Implement password encryption. Add CAPTCHA to prevent bots.

