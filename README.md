# LetsBelajar

LetsBelajar is a collaborative study and assignment management platform built with Laravel. It enables students, teachers, and project members to organize assignments, coordinate tasks via Kanban boards, share files and folders, track deadlines using an interactive calendar, and receive real-time notifications. It also features an administrative panel to monitor user activity and manage accounts.

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

Follow these steps to set up the project locally:

### 1. Clone the Repository
Clone the project to your local machine and navigate into the project directory:
```bash
git clone <repository-url>
cd jomstudy
```

### 2. Install Dependencies
Install PHP dependencies via Composer and frontend dependencies via NPM:
```bash
composer install
npm install
```

### 3. Environment Configuration
Copy the template environment file to create your own configuration:
```bash
copy .env.example .env
```
Ensure you generate an application key:
```bash
php artisan key:generate
```

### 4. Database Setup
Configure your database credentials in the .env file. If using the default Docker setup (Laravel Sail), configure your credentials or use the default Docker environment variables:
```bash
# Example for Docker Sail environment (.env.docker / .env)
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=letsbelajar
DB_USERNAME=sail
DB_PASSWORD=password
```
Run database migrations and seeders:
```bash
php artisan migrate --seed
```

### 5. Running the Application
You can run the application using Laravel Sail or the local PHP development server:

#### Using Laravel Sail (Docker)
Start the containers in the background:
```bash
./vendor/bin/sail up -d
```
Then run the migration/seeding command within the container if you haven't done so:
```bash
./vendor/bin/sail artisan migrate --seed
```

#### Using Local PHP Development Server
Start both the Laravel development server and Vite asset compiler using the helper composer script:
```bash
composer run dev
```

### 6. Accessing the Platform
Open your browser and navigate to:
- Application URL: http://localhost
- Mailpit Dashboard (if running Sail): http://localhost:8025

You can log in using the administrator account seeded during database setup, or register a new user account.
