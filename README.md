# Online Shopping Expense Manager

A Java Swing application designed to help consumers track, analyze, and optimize their shopping expenses. This system empowers users to categorize spending, visualize data with charts, and strictly monitor budget limits.

## 🚀 Features

  * **User Authentication:** Login system to access personal expense data.
  * **Add Expenses:** Detailed tracking for online purchases including platform, product name, category, quantity, and price.
  * **Expense Categorization:** Automatically organizes expenses into categories:
      * Clothing
      * Grocery
      * Electronics
      * Food
      * Cosmetics
  * **Visual Analysis:** Generates Pie Charts (using JFreeChart) to visualize spending distribution across categories.
  * **Budget Management:**
      * Set monthly budget limits.
      * Track "Offline Expenses" separately.
      * Receive alerts when the budget limit is exceeded.
  * **Dashboard:** View total expenses, remaining balance, and income status.

## 🛠️ Tech Stack

  * **Language:** Java (Swing/AWT)
  * **Database:** MySQL
  * **Libraries:**
      * `mysql-connector-j` (Database Connectivity)
      * `jfreechart` & `jcommon` (Data Visualization)
      * `swing-layout` (GUI Layout Manager)
  * **Build Tool:** Launch4j (for .exe creation)

## 📋 Prerequisites

Before running the application, ensure you have the following installed:

1.  **Java Runtime Environment (JRE)**: Version 1.8 or higher.
2.  **MySQL Server**: The application connects to a local MySQL instance at `localhost:3306`.

## ⚙️ Installation & Setup

### 1\. Database Setup

The application requires a specific database schema to function. Open your MySQL Workbench (or command line) and run the following SQL script:

```sql
-- Create Database
CREATE DATABASE IF NOT EXISTS osems;
USE osems;

-- Create User Table
CREATE TABLE IF NOT EXISTS user (
    User_name VARCHAR(50) NOT NULL,
    Password VARCHAR(50) NOT NULL,
    PRIMARY KEY (User_name)
);
-- Insert Default Admin (Username: admin, Password: admin123)
INSERT INTO user (User_name, Password) VALUES ('admin', 'admin123');

-- Create Expenses Table
CREATE TABLE IF NOT EXISTS addexpense (
    Expense_id INT NOT NULL,
    User_id INT,
    CatId VARCHAR(50),
    Amount DECIMAL(10,2),
    ExpenseDate VARCHAR(20),
    Platform VARCHAR(100),
    product_name VARCHAR(100),
    quantity INT,
    PRIMARY KEY (Expense_id)
);

-- Create Income Tracking Table
CREATE TABLE IF NOT EXISTS expense_track (
    id INT AUTO_INCREMENT PRIMARY KEY,
    User_id2 INT,
    Income DECIMAL(10,2)
);

-- Create Budget Management Table
CREATE TABLE IF NOT EXISTS manage (
    user_id INT,
    budget_limit DECIMAL(10,2),
    off_exp DECIMAL(10,2)
);
```

### 2\. Database Configuration

*Note: The source code currently uses the following hardcoded database credentials. If your MySQL password differs, you must update the `.java` files and recompile.*

  * **Hostname:** localhost:3306
  * **Database:** osems
  * **Username:** replace with your user name
  * **Password:** replace with yout password

## 🚀 How to Run

### Option 1: Using the Executable (Windows)

1.  Navigate to the distribution folder (`ExpenseApp_Final` or similar).
2.  Ensure the `lib` folder is present in the same directory as the `.exe`.
3.  Double-click **ExpenseManager.exe**.

### Option 2: Running from Source (Command Line)

If you want to compile and run the code yourself:

1.  Ensure your `lib` folder contains:
      * `mysql-connector-j-8.x.x.jar`
      * `jfreechart-1.0.19.jar`
      * `jcommon-1.0.23.jar`
      * `swing-layout-1.0.4.jar`
2.  Compile the code:
    ```cmd
    javac -d bin -cp "lib\*" src\*.java
    ```
3.  Run the application:
    ```cmd
    java -cp "bin;lib\*" JFrame
    ```

## 📖 Usage Guide

1.  **Login:** Launch the app and enter the credentials (default created in SQL script: `admin` / `admin123`).
2.  **Set Budget:** Go to "Manage Expenses" to set your monthly limit and income.
3.  **Add Expense:** Use the "Add expenses" button to log a new purchase.
4.  **Analyze:** Click "View expense" -\> "Generate" to see your financial breakdown and pie chart.

## 👤 Author

**Subhashini** (Original Project: 2023)
*Updated and Enhanced in 2025*
