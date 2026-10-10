# Personal Expense Tracker

A full-stack web application for managing personal income and expenses, monitoring financial balance, filtering transactions by date, and visualizing spending patterns through interactive charts.

## Table of Contents

1. [Project Overview](#project-overview)
2. [Features](#features)
3. [Technologies Used](#technologies-used)
4. [Project Structure](#project-structure)
5. [Application Screens](#application-screens)
6. [Prerequisites](#prerequisites)
7. [Installation and Setup](#installation-and-setup)
8. [Running the Application](#running-the-application)
9. [Using the Application](#using-the-application)
10. [REST API Documentation](#rest-api-documentation)
11. [Database Design](#database-design)
12. [Validation and Error Handling](#validation-and-error-handling)
13. [Testing Checklist](#testing-checklist)
14. [Security Considerations](#security-considerations)
15. [Future Enhancements](#future-enhancements)
16. [Author](#author)

---

## 1. Project Overview

The Personal Expense Tracker helps users record and manage their day-to-day financial transactions through a simple web interface.

Users can add income and expenses, update or delete existing transactions, view their overall financial summary, filter transaction history by date, and analyze monthly income and spending through charts.

Transaction data is stored in a MySQL database and accessed through a Spring Boot REST API.

### Project Objectives

- Simplify personal income and expense management.
- Track total income, total expenses, and remaining balance.
- Organize expenses by category.
- Filter transactions within a selected date range.
- Visualize monthly financial activity and category-wise spending.
- Practice full-stack application development using Java and web technologies.

## 2. Features

### Transaction Management

- Add income and expense transactions.
- View transaction history in a table.
- Edit existing transactions.
- Delete transactions with confirmation.
- Store transaction records in MySQL.

### Financial Dashboard

- Display total income.
- Display total expenses.
- Calculate the current balance.
- Show expense totals grouped by category.

**Balance calculation:**

`Balance = Total Income - Total Expenses`

### Date Filtering

- Filter transactions using a start date and an end date.
- Display transactions within the selected range, including both boundary dates.
- Validate the date range.
- Clear the filter to display all transactions.
- Update the dashboard summary and category totals for the filtered transactions.

### Financial Analytics

- View analytics on a separate page.
- Compare monthly income and expenses using a bar chart.
- View category-wise expenses using a doughnut chart.
- Display overall income, expenses, and balance.
- Navigate between the dashboard and analytics pages.

### Validation and Error Handling

- Reject invalid or non-positive transaction amounts.
- Require a transaction category.
- Validate transaction dates.
- Validate incoming data in the backend.
- Handle missing transaction IDs and invalid requests.
- Display user feedback when operations succeed or fail.

## 3. Technologies Used

| Technology              | Purpose                                |
| ----------------------- | -------------------------------------- |
| Java 21                 | Backend programming language           |
| Spring Boot             | Application framework                  |
| Spring Web MVC          | REST API and HTTP request handling     |
| Spring Data JPA         | Database persistence                   |
| Hibernate               | Object-relational mapping              |
| MySQL                   | Relational database                    |
| Maven                   | Dependency and build management        |
| HTML5                   | Web page structure                     |
| CSS3                    | Styling and responsive layouts         |
| JavaScript              | Frontend interactions and API requests |
| Chart.js                | Interactive analytics charts           |
| Jakarta Bean Validation | Backend input validation               |

## 4. Project Structure

The project follows a typical Spring Boot application structure.

```text
expense-tracker/
├── pom.xml
├── README.md
├── .gitignore
└── src/
    └── main/
        ├── java/
        │   └── com/
        │       └── expensetracker/
        │           ├── controller/
        │           ├── service/
        │           ├── repository/
        │           ├── entity/
        │           └── exception/
        └── resources/
            ├── application.properties
            └── static/
                ├── index.html
                ├── style.css
                ├── script.js
                ├── analytics.html
                └── analytics.js
```

**Note:** The Java package names and folder names above illustrate a typical organization. Keep the actual class names and folder structure that exist in your project.

### Important Files

- `pom.xml` — Maven dependencies and build configuration.
- `application.properties` — Database connection and server configuration.
- `index.html` — Main dashboard and transaction management interface.
- `style.css` — Application styling.
- `script.js` — Dashboard interactions, transaction CRUD operations, and date filtering.
- `analytics.html` — Separate analytics page.
- `analytics.js` — Data retrieval and chart generation.
- Backend controller, service, repository, and entity classes — Handle API requests and database operations.

## 5. Application Screens

The application contains two main pages.

### Dashboard

The dashboard provides:

- Financial summary cards.
- A transaction entry form.
- Transaction history.
- Edit and delete actions.
- Date-range filtering.
- Expense category summary.

### Analytics

The analytics page provides:

- Total income, expenses, and balance.
- Monthly income-versus-expenses bar chart.
- Category-wise expense doughnut chart.
- Navigation back to the dashboard.

**Screenshots:** Add screenshots of both pages to your repository when they are ready. You can create a `screenshots/` folder and insert them into this README.

For example, after adding the images:

```markdown
### Dashboard

![Dashboard](screenshots/dashboard.png)

### Analytics

![Analytics](screenshots/analytics.png)
```

The image filenames must match the files you actually upload.

## 6. Prerequisites

Install the following before running the application:

- Java Development Kit (JDK) 21.
- MySQL Server.
- Maven, or the Maven Wrapper if your project includes it.
- An IDE such as IntelliJ IDEA or Eclipse.
- A modern web browser.

Verify your Java installation:

```bash
java -version
```

Verify Maven if it is installed separately:

```bash
mvn -version
```

## 7. Installation and Setup

### Step 1: Clone the Repository

If the project has been uploaded to GitHub, clone it using:

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

Replace `YOUR_GITHUB_REPOSITORY_URL` with the actual repository URL.

Navigate into the project directory:

```bash
cd expense-tracker
```

If you are running the project locally without cloning, open your existing project folder instead.

### Step 2: Create the MySQL Database

Start your MySQL server and execute:

```sql
CREATE DATABASE expense_tracker;
```

Confirm that the database exists:

```sql
SHOW DATABASES;
```

The application uses this database to store transaction records.

### Step 3: Configure the Database Connection

Open:

`src/main/resources/application.properties`

Configure the application using your own local database credentials:

```properties
spring.application.name=expense-tracker

spring.datasource.url=jdbc:mysql://localhost:3306/expense_tracker
spring.datasource.username=${DB_USERNAME}
spring.datasource.password=${DB_PASSWORD}

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

server.port=8081
```

Set the `DB_USERNAME` and `DB_PASSWORD` environment variables before starting the application.

For a local Windows PowerShell session, you can set them temporarily:

```powershell
$env:DB_USERNAME="root"
$env:DB_PASSWORD="YOUR_LOCAL_MYSQL_PASSWORD"
```

Replace the example password with your actual local MySQL password. Do not upload it to GitHub.

If your current application already uses literal credentials in `application.properties`, move them to environment variables before publishing the repository.

### Step 4: Install Dependencies

From the directory containing `pom.xml`, run:

```bash
mvn clean install
```

This downloads the required dependencies, compiles the application, and runs the configured tests.

If the project includes Maven Wrapper scripts, you can use the wrapper instead:

```powershell
.\mvnw.cmd clean install
```

## 8. Running the Application

Start the application from the project root:

```bash
mvn spring-boot:run
```

Alternatively, if your project includes Maven Wrapper:

```powershell
.\mvnw.cmd spring-boot:run
```

Once Spring Boot starts successfully, open the following URLs.

| Page            | URL                                    |
| --------------- | -------------------------------------- |
| Dashboard       | http://localhost:8081/                 |
| Analytics       | http://localhost:8081/analytics.html   |
| Transaction API | http://localhost:8081/api/transactions |

The application uses port `8081` in the current configuration.

Keep the Spring Boot process running while using the application. If startup fails, check the terminal output and confirm that MySQL is running and the database credentials are correct.

## 9. Using the Application

### Adding a Transaction

1. Open the dashboard.
2. Select the transaction type: Income or Expense.
3. Enter the amount.
4. Enter a category, such as Salary, Food, Rent, or Transport.
5. Select the transaction date.
6. Optionally enter a description.
7. Submit the form.

The transaction should appear in the history table, and the summary should update.

### Editing a Transaction

1. Find the transaction in the table.
2. Click **Edit**.
3. Update the required fields.
4. Save the changes.

### Deleting a Transaction

1. Click **Delete** for the selected transaction.
2. Confirm the deletion.
3. Verify that the transaction is removed from the table.

### Filtering by Date

1. Select the start date.
2. Select the end date.
3. Click **Apply Filter**.
4. Review the matching transactions and filtered totals.
5. Click **Clear Filter** to return to the complete history.

### Viewing Analytics

1. Click **View Analytics** on the dashboard.
2. Review the monthly income-versus-expenses chart.
3. Review the expense category chart.
4. Click **Back to Dashboard** to return.

## 10. REST API Documentation

The application exposes a REST API for transaction management.

**Base URL:** `/api/transactions`

### API Endpoints

| Method | Endpoint                 | Description                                  |
| ------ | ------------------------ | -------------------------------------------- |
| GET    | `/api/transactions`      | Retrieve all transactions                    |
| GET    | `/api/transactions/{id}` | Retrieve a transaction by ID, if implemented |
| POST   | `/api/transactions`      | Create a transaction                         |
| PUT    | `/api/transactions/{id}` | Update an existing transaction               |
| DELETE | `/api/transactions/{id}` | Delete a transaction                         |

The single-transaction GET endpoint should be listed only if it is implemented in your controller.

### Example: Create a Transaction

**Request**

```http
POST /api/transactions
Content-Type: application/json
```

**Request body**

```json
{
  "type": "EXPENSE",
  "amount": 500.0,
  "category": "Food",
  "date": "2026-10-10",
  "description": "Lunch"
}
```

**Expected result:** The API creates the transaction and returns the saved record, including its generated ID, if configured to return the saved entity.

### Example: Retrieve All Transactions

```http
GET /api/transactions
```

Example response:

```json
[
  {
    "id": 1,
    "type": "EXPENSE",
    "amount": 500.0,
    "category": "Food",
    "date": "2026-10-10",
    "description": "Lunch"
  }
]
```

This is an illustrative response; actual IDs and records depend on your database.

### Example: Update a Transaction

```http
PUT /api/transactions/1
Content-Type: application/json
```

```json
{
  "type": "EXPENSE",
  "amount": 650.0,
  "category": "Food",
  "date": "2026-10-10",
  "description": "Lunch and snacks"
}
```

### Example: Delete a Transaction

```http
DELETE /api/transactions/1
```

A successful deletion normally returns HTTP `200 OK` or `204 No Content`, depending on your controller implementation.

### Common HTTP Status Codes

| Status                    | Meaning                                         |
| ------------------------- | ----------------------------------------------- |
| 200 OK                    | Request completed successfully                  |
| 201 Created               | Resource created, if returned by the controller |
| 204 No Content            | Request succeeded without a response body       |
| 400 Bad Request           | Invalid request data                            |
| 404 Not Found             | Requested transaction does not exist            |
| 500 Internal Server Error | Unexpected server-side error                    |

Actual response codes depend on the controller and exception-handler implementation.

## 11. Database Design

The application stores transaction records in a MySQL table managed through JPA and Hibernate.

### Transaction Fields

| Field         | Purpose                           |
| ------------- | --------------------------------- |
| `id`          | Unique transaction identifier     |
| `type`        | Income or expense                 |
| `amount`      | Monetary value of the transaction |
| `category`    | Transaction category              |
| `date`        | Transaction date                  |
| `description` | Optional transaction details      |

### Transaction Types

- `INCOME` — Money received.
- `EXPENSE` — Money spent.

### Persistence

Spring Data JPA handles database operations through the application's repository layer. With `spring.jpa.hibernate.ddl-auto=update`, Hibernate can update the database schema to reflect entity changes in supported cases.

For a production deployment, use a controlled schema migration strategy instead of relying on automatic schema updates.

## 12. Validation and Error Handling

The application uses frontend validation and backend validation to improve data quality.

Examples of validation rules include:

- Amount must be provided.
- Amount must be greater than zero.
- Category must not be blank.
- Date must be valid.
- Transaction type must be supported.
- Description length must respect the configured limit.

The backend also handles invalid requests and missing transaction records through exception handling.

Frontend validation improves the user experience, but backend validation remains essential because API requests can be sent without using the web interface.

## 13. Testing Checklist

Before publishing the project, verify the following.

### Transaction Management

- [ ] Add an income transaction.
- [ ] Add an expense transaction.
- [ ] Edit a transaction.
- [ ] Delete a transaction.
- [ ] Confirm the dashboard totals update correctly.
- [ ] Restart Spring Boot and verify transactions remain saved.

### Validation

- [ ] Try submitting an empty amount.
- [ ] Try submitting a zero or negative amount.
- [ ] Try submitting an empty category.
- [ ] Try an invalid date range.
- [ ] Verify the backend rejects invalid API requests.

### Date Filtering

- [ ] Filter using a start date and end date.
- [ ] Filter using only a start date.
- [ ] Filter using only an end date.
- [ ] Test a range with no matching transactions.
- [ ] Clear the filter and verify all transactions return.

### Analytics

- [ ] Confirm the monthly chart displays.
- [ ] Confirm the category chart displays.
- [ ] Compare displayed totals with the underlying transaction data.
- [ ] Test navigation between dashboard and analytics.

### GitHub Readiness

- [ ] Confirm all required source files are present.
- [ ] Remove passwords and other secrets from tracked files.
- [ ] Add `.gitignore`.
- [ ] Add project screenshots.
- [ ] Verify setup instructions are accurate.

## 14. Security Considerations

- Never commit database passwords, API keys, or other secrets to GitHub.
- Configure database credentials through environment variables or a suitable secret-management mechanism.
- Avoid exposing database credentials in frontend JavaScript.
- Validate data on the backend.
- Use HTTPS and appropriate authentication and authorization before exposing the application to real users.
- Review database permissions and configuration before deployment.
- Avoid using automatic Hibernate schema updates as the long-term production migration strategy.

**Important:** This project is a personal finance management application, not a banking integration or a financial institution's accounting system. Production use would require additional security, access control, and operational safeguards.

## 15. Future Enhancements

Potential improvements include:

- User registration and login.
- Separate transaction data for each user.
- Monthly budgets and spending limits.
- Savings goals.
- CSV or Excel export.
- Search and category filters.
- Recurring transactions.
- Improved mobile responsiveness.
- Additional reports and financial trends.
- Cloud deployment.
- Automated backend and frontend tests.

These are possible future enhancements and are not claimed as currently implemented.

## 16. Author

**Project:** Personal Expense Tracker

**Purpose:** Full-stack application development and personal finance tracking.

**Technologies:** Java, Spring Boot, MySQL, HTML, CSS, JavaScript, and Chart.js.

**GitHub:** Add your GitHub profile or repository URL here.

---

## Conclusion

The Personal Expense Tracker demonstrates how a Java backend, REST API, relational database, and interactive web frontend can work together to manage personal financial records.

The project covers transaction CRUD operations, persistent storage, validation, date-range filtering, financial summaries, and visual analytics. It can be extended with authentication, budgeting, reporting, and deployment as future improvements.
