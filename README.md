# Laptop-mania-
A tangerine-inspired e-commerce platform for laptops, built with PHP, MySQL, and Bootstrap. Features product management, sales analytics, and a vibrant K-drama aesthetic.
# Laptopmania 🍊 - A Tangerine-Inspired E-Commerce Platform

![Laptopmania Logo](project/img/logo.png)

**Laptopmania** is a vibrant e-commerce platform for laptop enthusiasts, built as part of a web development lab (01CE0611, Marwadi University). Inspired by the warm, coastal vibes of the K-drama *When Life Gives You Tangerines*, this project features a tangerine-orange aesthetic with a modern glassmorphism design, wave animations, and a classy user experience. It allows users to browse and purchase laptops, while admins can manage products, categories, and sales analytics.

## ✨ Features
- **User Features**:
  - Browse laptops by category with a visually appealing interface.
  - Add products to cart, checkout, and view order confirmations.
  - Submit inquiries via a contact form.
  - User profile with order history.
- **Admin Features**:
  - Dashboard with sales analytics (total products, categories, sales, and monthly trends).
  - Add, edit, and delete products and categories.
  - Secure admin authentication.
- **Design**:
  - Tangerine-inspired color palette (`#ff8c00`, `#ffd700`, `#1e90ff`, `#20b2aa`, `#d4af37`).
  - Glassmorphism cards, gradient backgrounds, and wave animations.
  - High contrast for accessibility (WCAG 2.1 AA compliant).

## 🛠️ Technologies Used
- **Frontend**: HTML, CSS (Bootstrap 5.3), JavaScript
- **Backend**: PHP (with session management and CSRF protection)
- **Database**: MySQL (schema includes users, products, categories, orders, and contact messages)
- **Environment**: XAMPP (local development)
- **Styling**: Custom `styles.css` with tangerine-inspired design elements

## 📂 Project Structure
laptopmania/
├── project/
│   ├── img/                # Images (logo, product images, user profile)
│   ├── add_category.php    # Add new categories (admin)
│   ├── add_product.php     # Add new products (admin)
│   ├── admin_dashboard.php # Admin dashboard with sales analytics
│   ├── checkout.php        # Checkout process for users
│   ├── contactus.php       # Contact form for user inquiries
│   ├── edit_product.php    # Edit existing products (admin)
│   ├── homepage.php        # Homepage with featured products
│   ├── login.php           # User and admin login
│   ├── logout.php          # Logout functionality
│   ├── manage_products.php # Manage products (admin)
│   ├── order_confirmation.php # Order confirmation page
│   ├── products.php        # Product listing page
│   ├── profile.php         # User profile and order history
│   ├── styles.css          # Custom styles with tangerine theme
│   └── db_connect.php      # Database connection script
├── .gitignore              # Git ignore file
└── README.md               # Project documentation

text

Collapse

Wrap

Copy

## 🚀 Getting Started

### Prerequisites
- XAMPP (or any PHP/MySQL environment)
- Git
- A web browser

### Installation
1. **Clone the Repository**
   ```bash
   git clone https://github.com/<your-username>/Laptop-mania.git
   cd Laptop-mania
Set Up the Database
Start XAMPP and ensure Apache and MySQL are running.
Import the database schema:
sql

Collapse

Wrap

Copy
CREATE DATABASE laptopmania;
USE laptopmania;
Then, run the SQL script from database.sql (or copy-paste the schema provided below) to create the tables.
Configure the Database Connection
Open project/db_connect.php and update the database credentials:
php

Collapse

Wrap

Copy
$host = 'localhost';
$user = 'root';
$pass = '';
$dbname = 'laptopmania';
Move Files to XAMPP
Copy the Laptop-mania folder to htdocs in your XAMPP directory (e.g., C:\xampp\htdocs\Laptop-mania).
Run the Application
Open a browser and navigate to http://localhost/Laptop-mania/project/homepage.php.
Database Schema
The project uses the following tables:

admin: Admin credentials
users: User information
products: Product details
categories: Product categories
orders: Order details
contact_messages: Contact form submissions
login_attempts: Tracks login attempts for security
Run the following SQL to set up the database:

sql

Collapse

Wrap

Copy
-- Create the database
CREATE DATABASE IF NOT EXISTS laptopmania;
USE laptopmania;

-- Table: admin
CREATE TABLE admin (
    id INT(11) NOT NULL AUTO_INCREMENT,
    email VARCHAR(255) NOT NULL,
    password VARCHAR(255) NOT NULL,
    PRIMARY KEY (id),
    UNIQUE KEY email (email)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- Table: categories
CREATE TABLE categories (
    id INT(11) NOT NULL AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (id),
    UNIQUE KEY name (name)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- Table: contact_messages
CREATE TABLE contact_messages (
    id INT(11) NOT NULL AUTO_INCREMENT,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL,
    message TEXT NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- Table: login_attempts
CREATE TABLE login_attempts (
    id INT(11) NOT NULL AUTO_INCREMENT,
    email VARCHAR(255) NOT NULL,
    attempts INT(11) DEFAULT 0,
    last_attempt TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- Table: orders
CREATE TABLE orders (
    id INT(11) NOT NULL AUTO_INCREMENT,
    user_id INT(11) NOT NULL,
    product_id INT(11) NOT NULL,
    quantity INT(11) NOT NULL,
    price DECIMAL(10,2) NOT NULL,
    order_date TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (id)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- Table: products
CREATE TABLE products (
    id INT(11) NOT NULL AUTO_INCREMENT,
    name VARCHAR(255) NOT NULL,
    description TEXT NOT NULL,
    price DECIMAL(10,2) NOT NULL,
    image_path VARCHAR(255) NOT NULL,
    category_id INT(11) DEFAULT NULL,
    stock_quantity INT(11) DEFAULT 0,
    PRIMARY KEY (id),
    UNIQUE KEY name (name),
    INDEX idx_category (category_id),
    FOREIGN KEY (category_id) REFERENCES categories(id) ON DELETE SET NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

-- Table: users
CREATE TABLE users (
    id INT(11) NOT NULL AUTO_INCREMENT,
    fullname VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    reset_token VARCHAR(100) DEFAULT NULL,
    reset_expires DATETIME DEFAULT NULL,
    PRIMARY KEY (id),
    UNIQUE KEY email (email)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;
🤝 Contributing
Contributions are welcome! Please follow these steps:

Fork the repository.
Create a new branch (git checkout -b feature/your-feature).
Make your changes and commit (git commit -m "Add your feature").
Push to your branch (git push origin feature/your-feature).
Open a pull request.
📜 License
This project is licensed under the MIT License - see the  file for details.

📧 Contact
For inquiries, reach out via the contact form or email us at support@laptopmania.com.

text

Collapse

Wrap

Copy

---

### Steps to Create the Repository on GitHub

Follow these steps to create the "Laptopmania" repository on GitHub with the settings you specified:

1. **Sign in to GitHub**
   - Go to [GitHub](https://github.com) and sign in to your account.

2. **Create a New Repository**
   - Click the "+" icon in the top-right corner and select "New repository."

3. **Fill in the Repository Details**
   - **Owner**: Select your GitHub username (e.g., `<your-username>`).
   - **Repository Name**: Enter `Laptop-mania` (GitHub will automatically format it as `Laptop-mania`).
   - **Description**: Paste the short description:
A tangerine-inspired e-commerce platform for laptops, built with PHP, MySQL, and Bootstrap. Features product management, sales analytics, and a vibrant K-drama aesthetic.

text

Collapse

Wrap

Copy
- **Visibility**: Select **Public** (as specified: "Anyone on the internet can see this repository. You choose who can commit.").

4. **Initialize the Repository**
- Check the following options:
- **Add a README file**: This will create a `README.md` file. You can copy-paste the full `README.md` content provided above into it.
- **Add .gitignore**: Choose the `PHP` template to ignore common PHP files (e.g., `vendor/`, `.env`).
- **Choose a license**: Select the `MIT License` (a common choice for open-source projects, allowing others to use and modify your code with attribution).

5. **Create the Repository**
- Click the "Create repository" button. GitHub will create the repository with the default branch set to `main` (as noted: "This will set main as the default branch").

---

### Post-Creation Steps

After creating the repository, you can add your project files and push them to GitHub. Here’s how:

1. **Clone the Repository to Your Local Machine**
```bash
git clone https://github.com/<your-username>/Laptop-mania.git
cd Laptop-mania
Add Your Project Files
Copy your project/ folder (containing all PHP files, styles.css, img/, etc.) into the Laptop-mania directory.
If you have a database.sql file with the schema, add it to the root directory for reference.
Stage and Commit Your Changes
bash

Collapse

Wrap

Copy
git add .
git commit -m "Initial commit: Add Laptopmania project files"
Push to GitHub
bash

Collapse

Wrap

Copy
git push origin main
Verify on GitHub
Visit https://github.com/<your-username>/Laptop-mania to ensure all files are uploaded correctly.
Edit the README.md file on GitHub (or locally) to include the full content provided above.
