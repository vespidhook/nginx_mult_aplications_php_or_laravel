# README

## NGINX PHP-FPM Configuration for Multiple Applications

This repository contains the NGINX configuration for hosting multiple PHP applications on a single server using the wyveo/nginx-php-fpm Docker image with PHP 8.2.

### Configuration Details

#### NGINX Configuration

The NGINX configuration is set up to listen on port 80 and handle multiple PHP applications, each located in a subdirectory. Key features include:

- `X-Frame-Options`, `X-XSS-Protection`, and `X-Content-Type-Options` headers for enhanced security.
- Default charset set to UTF-8.
- Error page handling, redirecting 404 errors to the main index.php.
- Denying access to hidden files and directories.
- Custom error pages for favicon.ico and robots.txt.

#### PHP Application Configuration

The configuration includes settings for three PHP applications (`app1`, `app2`, and `app3`). Each application block consists of:

- Alias to the respective application's public directory.
- Attempt to serve static files directly, falling back to the application's index.php if not found.
- Configuration for handling PHP files, forwarding requests to the PHP-FPM socket.

#### Dockerfile

The Dockerfile is based on the wyveo/nginx-php-fpm image with PHP 8.2. It includes:

- Exposing port 80.
- Creating necessary directories for NGINX logs and web applications.
- Setting appropriate permissions for the web server to access directories.

### Usage

1. Ensure Docker is installed on your system.
2. Clone this repository:

    ```bash
    git clone https://github.com/yourusername/your-repo.git
    ```

3. Navigate to the repository:

    ```bash
    cd your-repo
    ```

4. Build the Docker image:

    ```bash
    docker build -t your-image-name .
    ```

5. Run the Docker container:

    ```bash
    docker run -p 8080:80 --name your-container-name -d your-image-name
    ```

Replace `your-username`, `your-repo`, `your-image-name`, and `your-container-name` with appropriate values.

### Customization

Feel free to customize the NGINX configuration (`default.conf`) or add more PHP applications following the established pattern.

### Important Note

This configuration is intended for development or educational purposes. For production use, consider enhancing security measures and adapting configurations based on specific requirements.

### Credits

This NGINX PHP-FPM configuration is based on the wyveo/nginx-php-fpm image (PHP 8.2). Visit [wyveo/nginx-php-fpm](https://github.com/wyveo/nginx-php-fpm) for more information about the base image.

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.