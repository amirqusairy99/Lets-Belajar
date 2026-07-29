# LetsBelajar

LetsBelajar (also known as LetsBelajar) is a collaborative study and assignment management platform built with Laravel. It enables students, teachers, and project members to organize assignments, coordinate tasks via Kanban boards, share files and folders, track deadlines using an interactive calendar, and receive real-time notifications. It also features an administrative panel to monitor user activity and manage accounts.

## Features

- Assignment Management: Create, edit, and archive assignments. Track member contributions and view analytic reports for assignment progress.
- Member Roles and Permissions: Manage members within an assignment, assign specific roles, and update collaboration permissions.
- Task Management and Kanban Board: Break down assignments into tasks. Track progress dynamically using a Kanban board view divided into To Do, In Progress, and Completed states.
- File and Folder Sharing: Upload files, organize them into folders, and download resources. Includes in-browser PDF previews.
- Interactive Calendar: View deadlines, tasks, and assignment schedules on an interactive calendar interface.
- Notifications System: Receive updates on newly uploaded files, assigned tasks, and membership changes.
- Administrator Dashboard: Dedicated interface for platform administrators to manage users, monitor active accounts, and suspend or activate users.

## Technology Stack

- Backend Framework: Laravel 12.x
- PHP Version: 8.2 or higher
- Database: MySQL 8.4
- Frontend: TailwindCSS, Blade Templates, Vite, Axios, Firebase JS SDK
- Environment Management: Laravel Sail (Docker Compose)
- Mail Service: Mailpit (local testing) and Resend integration for transactional emails
- Third-Party Integrations: Firebase (Authentication, Storage configuration ready)

## Prerequisites

Ensure you have the following installed on your system:

- PHP 8.2 or higher (if running locally without Sail)
- Composer
- Node.js and NPM
- Docker and Docker Desktop (recommended, if using Laravel Sail)

## Getting Started

Choose one of the setup options below depending on your environment preference:

---

### Option A: Setup using Docker (Laravel Sail)

This option uses Docker containers for running the application, database, and auxiliary services like Mailpit.

#### 1. Clone the Repository
Clone the project to your local machine and navigate into the project directory:
```bash
git clone <repository-url>
cd Lets-Belajar
```

#### 2. Configure the Environment
Copy the environment template file:
```bash
copy .env.example .env
```
In your `.env` file, configure the database variables to match the Docker Sail configuration:
```env
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=letsbelajar
DB_USERNAME=sail
DB_PASSWORD=password
```

#### 3. Install Dependencies
Run a temporary Docker container to install composer dependencies without needing local PHP installed:
```bash
docker run --rm \
    -u "$(id -u):$(id -g)" \
    -v "$(pwd):/var/www/html" \
    -w /var/www/html \
    laravelsail/php8.2-composer:latest \
    composer install --ignore-platform-reqs
```
*(Alternatively, if you have Composer installed locally, simply run `composer install`)*

Next, install frontend dependencies:
```bash
npm install
```

#### 4. Start the Application and Build Assets
Start the containers in the background:
```bash
./vendor/bin/sail up -d
```

Generate the application key and run the migrations with seeders:
```bash
./vendor/bin/sail artisan key:generate
./vendor/bin/sail artisan migrate --seed
```

Start the Vite dev server for compilation:
```bash
./vendor/bin/sail npm run dev
```

#### 5. Access the Platform
- Application URL: http://localhost
- Mailpit Dashboard: http://localhost:8025

---

### Option B: Setup without Docker (Local PHP & MySQL)

This option runs the services directly on your host machine.

#### 1. Clone the Repository
Clone the project to your local machine and navigate into the project directory:
```bash
git clone <repository-url>
cd jomstudy
```

#### 2. Install Dependencies
Install PHP dependencies via Composer and frontend dependencies via NPM:
```bash
composer install
npm install
```

#### 3. Configure the Environment
Copy the environment template file:
```bash
copy .env.example .env
```
Generate the application key:
```bash
php artisan key:generate
```

#### 4. Database Setup
Create a new MySQL database named `letsbelajar` (or matching your custom settings) on your local server.

Update the `.env` file with your local database connection details:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=letsbelajar
DB_USERNAME=root
DB_PASSWORD=your_local_password
```

Run database migrations and seeders:
```bash
php artisan migrate --seed
```

#### 5. Running the Application
Start both the Laravel development server and Vite asset compiler using the helper composer script:
```bash
composer run dev
```

#### 6. Access the Platform
- Application URL: http://localhost:8000
- Vite Server: http://localhost:5173

You can log in using the administrator account seeded during database setup, or register a new user account.
