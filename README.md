# PHP App Deployment and Config with Ansible 

## Overview
This task automates the deployment and configuration of a Laravel PHP boilerplate application from "https://github.com/hngprojects/hng_boilerplate_php_laravel_web.git" using Ansible. The process involves setting up a new Linux server instance, cloning the application repository, installing dependencies, configuring PostgreSQL and messaging queues, setting up application and Nginx, and configuring logging.

## Steps

1. **User and Directory Setup**:
    - Create a user named `hng` with sudo privileges.
    - Clone the boilerplate repository into `/opt/stage_5b` and ensure it is owned by the `hng` user.

2. **Database and Dependencies**:
    - Install PostgreSQL and save the admin credentials in `/var/secrets/pg_pw.txt`.
    - Install necessary application dependencies, including PHP extensions, RabbitMQ, and others.

3. **Application and Proxy Setup**:
    - Ensure the application is running on `127.0.0.1:3000`.
    - Install Nginx 1.26 and configure it to reverse proxy requests from port `80` to the application.

4. **Logging Configuration**:
    - Set up logging so that stderr logs are written to `/var/log/stage_5b/error.log` and stdout logs to `/var/log/stage_5b/out.log`, with both files owned by the `hng` user.

## Execution
Run the Ansible playbook using the following command:
```bash
ansible-playbook -i inventory.cfg main.yaml -b
```

## Inventory Configuration (`inventory.cfg`)
```ini
[hng]
your_server_ip_or_hostname
```




## Conclusion
This setup ensures an automated and consistent deployment of the boilerplate application with necessary configurations, making it easier to manage and scale.

## Contact
For any issues or further information, please contact the project maintainer.
