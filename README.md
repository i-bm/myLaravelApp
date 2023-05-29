
# PHP Laravel Web Application Deployment

This repository contains the code and instructions for deploying a PHP Laravel web application with a MySQL database on physical bare servers using DevOps best practices.

## Prerequisites

Before you begin, make sure you have the following:

- Physical bare servers (target servers) running a compatible operating system (e.g., Ubuntu 20.04)
- Ansible installed on your local machine
- Docker installed on your target servers
- A Git repository set up to store the application code
- Basic knowledge of Laravel, PHP, MySQL, Docker, and Ansible

## Deployment Process

Follow the steps below to deploy the PHP Laravel web application:

### 1. Clone the Git Repository

```bash
git clone https://github.com/i-bm/myLaravelApp
cd myLaravelApp
```

### 2. Configure Ansible Inventory

Open the `hosts.ini` file and specify the target servers' IP addresses or hostnames under the appropriate group(s).

```ini
[web]
server1 ansible_host=192.168.100.10
server2 ansible_host=192.168.100.11

[database]
db1 ansible_host=192.168.100.12
db2 ansible_host=192.168.100.13
```

### 3. Customize Deployment Configuration

Open the `group_vars/all.yml` file and customize the deployment configuration according to your environment. Update variables such as the application name, database credentials, and any other required settings.

### 4. Run the Ansible Playbook

```bash
ansible-playbook -i hosts.ini deploy.yml
```

This will execute the Ansible playbook `deploy.yml` and automate the deployment process on the target servers.

### 5. Containerize the Application with Docker

- Build the Docker image:

  ```bash
  docker build -t laravel-app .
  ```

- Run the Docker container:

  ```bash
  docker run -d -p 80:80 --name laravel-container laravel-app
  ```

- Access the application in your web browser at `http://<server-ip>`.

### 6. Configure MySQL for High Availability

Implement the necessary steps to configure MySQL for high availability and scalability. This can include setting up replication, clustering, load balancing, and failover mechanisms. Ensure you follow best practices for securing the MySQL database and optimizing its performance.

### 7. Implement Security Best Practices

Take the following security measures to protect the application and infrastructure:

- Use HTTPS for secure communication.
- Configure a firewall to restrict access to necessary ports.
- Enforce strong passwords and limited access privileges for the MySQL database.
- Apply security patches and updates regularly.
- Implement secure coding practices in the application code.
- Perform regular vulnerability scans and security audits.

### 8. Set Up Monitoring and Logging

Configure monitoring and logging for the application and infrastructure:

- Use a monitoring tool (e.g., Prometheus) to monitor server metrics, database performance, and application health.
- Set up alerting rules to receive notifications for critical issues.
- Implement centralized logging using tools like ELK stack or Splunk to collect and analyze logs from servers and the application.
- Monitor application logs for errors, exceptions, and security-related events.

## Local Development

To run the application locally for development or testing purposes, follow these steps:

1. Install PHP: Make sure you have PHP installed on your computer. You can download PHP from the official website (https://www.php.net/downloads.php) or use a package manager like Homebrew (for macOS) or Chocolatey (for Windows).

2. Install Composer: Composer is a dependency management tool for PHP that Laravel uses. You can download and install Composer from the official website (https://getcomposer.org/download/). Follow the installation instructions for your operating system.

3. Install Laravel: Once you have Composer installed, open a terminal or command prompt and run the following command to install Laravel globally on your system:

   ```bash
   composer global require laravel/installer
   ```

4. Clone the Laravel app: If you haven't done so already, clone the Laravel app repository from a version control system like Git. Navigate to the directory where you want to store the project and run the following command:

   ```bash
   git clone <repository_url>
   ```

5. Install project dependencies: Change into the project directory by running `cd <project_name>`. Next, install the project dependencies by running the following command:

   ```bash
   composer install
   ```

6. Create a .env file: Laravel requires an environment configuration file (.env) to run. You can duplicate the `.env.example` file and rename it to `.env`. Open the `.env` file and set the necessary environment variables such as database connection details, app URL, etc.

7. Generate an application key: Laravel requires an application key for encryption and other security purposes. In the terminal, run the following command to generate an application key:

   ```bash
   php artisan key:generate
   ```

8. Set up the database: If your application uses a database, create a new database and update the necessary database configuration details in the `.env` file.

9. Run migrations: Laravel uses database migrations to create the necessary database tables. Run the migrations using the following command:

   ```bash
   php artisan migrate
   ```

10. Start the development server: Finally, start the Laravel development server by running the following command:

    ```bash
    php artisan serve
    ```

   This command will start a local development server at `http://localhost:8000` by default.

11. Access the application: Open your web browser and navigate to `http://localhost:8000` (or the URL shown in the terminal). If everything is set up correctly, you should see your Laravel application running locally.

These steps should help you run a Laravel app locally on your machine.
