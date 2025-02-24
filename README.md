# PHP Development Environment with Docker

A modern Docker-based development environment for PHP applications using Apache, MySQL, and Postfix. This configuration provides a complete LAMP stack with additional tools for PHP development.

## Features

- PHP 8.2 with common extensions
- Apache 2.4 web server
- MySQL 8.0 database
- Postfix, Mailhog mail server
- Amazon Linux 2023 base image
- UTF-8 support throughout the stack

## Prerequisites

- Docker Engine
- Docker Compose
- Git (optional)

## Quick Start

1. Clone this repository:
```bash
git clone https://github.com/mtm-heinhtetsoe/docker-php-dev
cd docker-php-dev
```

2. Create your PHP application in the `src` directory or modify the Apache configuration to point to your desired directory.

3. Build the Image:
```bash
docker-compose build
```

4. Start the environment:
```bash
docker-compose up -d
```

5. Update mail settings in your application `.env`
```env
MAIL_MAILER=smtp
MAIL_HOST=mailhog
MAIL_PORT=1025
MAIL_USERNAME=null
MAIL_PASSWORD=null
MAIL_ENCRYPTION=null
MAIL_FROM_ADDRESS="hello@example.com"
MAIL_FROM_NAME="${APP_NAME}"
```

6. Access your application at `http://localhost:8000`


## Structure

```
.
├── app/
│   ├── Dockerfile           # PHP application container configuration
│   ├── php.ini             # PHP configuration
│   ├── main.cf             # Postfix configuration
│   └── httpd/
│       └── conf.d/
│           └── app.conf    # Apache virtual host configuration
├── db/
│   ├── Dockerfile          # MySQL container configuration
│   └── my.cnf             # MySQL configuration
├── src/                    # Create or Clone your PHP Application Here
├── docker-compose.yml      # Docker Compose configuration
├── LICENSE                 # MIT License
└── .env.example              
└── .gitignore              
└── CONTRIBUTING.md              
└── README.md              # This file
```

## Configuration

### PHP Configuration
- PHP 8.2 with common extensions (bcmath, gd, intl, mbstring, mysql, xml, zip)
- Custom php.ini configuration available in `app/php.ini`

### Apache Configuration
- Virtual host configuration in `app/httpd/conf.d/app.conf`
- Document root set to `/var/www/html/app/public`
  - Edit the `app` with your app's dirname

### MySQL Configuration
- Custom MySQL configuration in `db/my.cnf`
- Default character set: utf8mb4
- Default collation: utf8mb4_unicode_ci
- Native password authentication enabled

### Mail Configuration
- Postfix configuration available in `app/main.cf`

## Customization

### Environment Variables
Create a `.env` file in the root directory by copying `.env.example` to override default settings:

```env
MYSQL_ROOT_PASSWORD=your_root_password
MYSQL_DATABASE=your_database
MYSQL_USER=your_user
MYSQL_PASSWORD=your_password
```

### Adding PHP Extensions
To add more PHP extensions, modify the `app/Dockerfile`:

```dockerfile
RUN yum install -y \
    php8.2-additional-extension
```

## Development

1. Place your PHP application in the `src` directory
2. Configure your database connection using the environment variables
3. Build the image `docker compose build`
4. Run the containers `docker compose up -d`
5. Access your application at `http://localhost:8000`

## Production Use

This configuration is primarily designed for development. For production use:

1. Remove development tools and configurations
2. Set appropriate PHP settings in php.ini
3. Configure proper security measures
4. Use strong passwords
5. Consider using official Docker images instead of custom builds

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a new Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Docker Documentation](https://docs.docker.com/)
- [PHP Documentation](https://www.php.net/docs.php)
- [Apache Documentation](https://httpd.apache.org/docs/)
- [MySQL Documentation](https://dev.mysql.com/doc/)
