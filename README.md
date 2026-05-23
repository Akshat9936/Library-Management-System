# Library Management System (LMS)

A comprehensive, virtual Library Management System built in C++ using core Object-Oriented Programming (OOP) principles. This system is designed to manage books, users, and borrowing activities with security, data persistence, and robust input validation. 

It features a secure, menu-driven command-line interface tailored for librarians, students, and faculty members alike.

---

##  Features

### 1. User Roles & Authentication
* **Librarians:** Full administrative privileges (add, remove, and edit book/user records).
* **Students:** Standard access with a 3-book borrowing limit and an overdue fine rate of ₹10/day.
* **Faculty:** Elevated access with a 5-book borrowing limit and an extended 60-day grace period.
* **Security:** Secure access managed via a distinct username-password login system.

### 2. Book Management
* Complete CRUD operations (Add, Read, Update, Delete) for book records.
* Real-time availability tracking across three states: `Available`, `Borrowed`, and `Reserved`.
* Dynamic searching and scannable tabular layouts for catalog browsing.

### 3. Borrowing & Fine Tracking
* Automated due date calculation based on user roles.
* Real-time overdue tracking and fine computation.
* Persistent localized borrowing history tracking per user account.

### 4. Data Persistence & Robustness
* **File Processing:** Complete state management utilizing CSV flat-file storage for books and users.
* **Concurrency Protection:** Active file-locking mechanisms to prevent data corruption during write operations.
* **Defensive Programming:** Strict input validation rejecting invalid ISBNs, incorrect data types (e.g., matching alphabetic inputs against numeric fields), and weak passwords.

---

##  Prerequisites

To compile and run this project, you need:
* A C++ compiler supporting **C++17** or higher (such as GCC, Clang, or MSVC).
* A terminal emulator or command prompt.

---

##  Getting Started

Follow these steps to clone, compile, and execute the program on your local machine:

### 1. Clone the Repository
```bash
git clone [https://github.com/Akshat9936/Library-Management-System](https://github.com/Akshat9936/Library-Management-System)
cd Library-Management-System

```

### 2. Compile the Source Code

```bash
g++ -std=c++17 main.cpp -o library

```

### 3. Run the Executable

```bash
library

```

---

##  Important Usage Notes

*  **File Locking Warning:** **DO NOT** open the underlying CSV files before or during the execution of the program. Doing so may trigger a file lock, preventing the software from saving data and causing it to throw a "CSV file is locked" error.

* **Viewing Data Safely:** You may safely inspect the CSV databases *after* closing the executable. It is recommended to use **Notepad** or a basic text editor.
* **Excel Usage:** If opening data files in Microsoft Excel, disable default scientific notation formatting first to ensure ISBN numbers do not become truncated or corrupted.
* **Terminal Formatting:** For the tabular data grids to align properly, please run your terminal in **Full Screen Mode**. If text rows still wrap abnormally, reduce your terminal's font size slightly until the columns snap into place.

---

##  Database Schema Formats

The backend state is tracked natively across two primary data structures:

### `books.csv`

```text
Genre,Title,Author,Publisher,Year,ISBN,Status

```

### `users.csv`

```text
User Id,Username,Password,Role (Student/Faculty/Librarian),Name,Age,Gender,Borrowing history,Fine

```

####  Borrowing History Sub-Format

Within the user database, distinct book transactions are delimited by semicolons (`;`). Individual book nodes observe the following internal sequence:

```text
ISBN,Title,Borrowing Date,Return Date,Due Date,Status,Fine

```

