EduBase is a JavaFX-based Student Management System designed to simplify the management of student data, attendance, and academic performance.
It uses:

JavaFX for GUI

SQLite for local storage

MVC Architecture (Model–View–Controller)

BCrypt hashing for secure authentication

ControlsFX for toast notifications

Architecture
| Layer          | Description                                                 | Example Classes                                                            |
| -------------- | ----------------------------------------------------------- | -------------------------------------------------------------------------- |
| **Model**      | Represents data entities and logic                          | `Student.java`, `Subject.java`, `User.java`                                |
| **View**       | FXML files (LoginView.fxml, MainView.fxml) define UI layout | `fxml/` folder                                                             |
| **Controller** | Handles user interactions and connects view with data       | `LoginController.java`, `MainController.java`                              |
| **Service**    | Contains business logic and database access                 | `UserService.java`, `StudentService.java`, `DatabaseService.java`          |
| **Utils**      | Helper functions for UI, validation, alerts, and theming    | `AlertUtils.java`, `ThemeManager.java`, `ToastUtil.java`, `Validator.java` |

🧠 DETAILED EXPLANATION BY PACKAGE
🗂️ com.example.edubase
App.java

Entry point of the program (extends Application).

Initializes the database using DatabaseService.initializeDatabase().

Loads the login view (LoginView.fxml) and applies the saved theme preference.

Sets the app icon and stage properties.


🗂️ controllers
LoginController.java
Handles user authentication.

Key steps:

Takes username & password from text fields.

Validates credentials using UserService.authenticate().

If correct → loads MainView.fxml.

If wrong → shows error using AlertUtils.

MainController.java

Handles all main features after login:

Add, edit, delete, search students.

Calculate total marks and attendance averages.

Apply themes and keyboard shortcuts.

Validate input fields.

Key Functionalities:
| Feature              | Description                                                 |
| -------------------- | ----------------------------------------------------------- |
| **CRUD operations**  | Add/update/delete student records                           |
| **Validation**       | Uses `Validator` class for checking name, age, email, etc.  |
| **Auto Calculation** | Recomputes totals and averages when marks/attendance change |
| **Theming**          | Switch between light/dark modes using `ThemeManager`        |
| **Search Filter**    | Real-time search in student list                            |


FEATURES SUMMARY
| Feature                  | Description                              |
| ------------------------ | ---------------------------------------- |
| **Secure Login**         | BCrypt password hashing and validation   |
| **Student CRUD**         | Create, Read, Update, Delete operations  |
| **Data Validation**      | Regex-based checks for input             |
| **Dynamic UI Updates**   | Auto-calculation of averages             |
| **Dark/Light Themes**    | User preference stored persistently      |
| **Toast Notifications**  | Non-blocking visual feedback             |
| **Database Integration** | SQLite local storage for persistent data |

📊 DATABASE STRUCTURE
| Table        | Columns                                                        | Purpose                     |
| ------------ | -------------------------------------------------------------- | --------------------------- |
| **users**    | id, username, password_hash, role                              | For admin authentication    |
| **students** | id, name, age, address, city, state, phone, email              | Stores personal details     |
| **subjects** | id, student_id, subject_name, attendance, cycle1–cycle4, total | Stores marks and attendance |


🖥️ SAMPLE FLOW
Launch App.java → Database setup → Login screen.

LoginController → verifies credentials via UserService.

MainController → loads student list from DB.

User Actions: Add/Edit/Delete student → validated → saved via StudentService.

Real-time UI updates: Average marks, attendance recalculated automatically.

Logout → returns to Login view
