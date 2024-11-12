# Laravel To-Do List Deployment with docker compose
# Setup Instructions
## Prerequisites
Docker
Docker-compose

## Deployement Instruction
## 1. Install Docker and docker-compose
## 2. Verify Docker running
```sh
systemctl status docker.service
```
## 3. Pull the code in your working directory
## 4. cp .env.example to .env
```sh
cp .env.example .env
```
## 5. Update .env file
Update the .env file with your environment-specific details, such as database credentials and Redis connection as defined in docker-compose.yml
## 6. Build and Start Containers
Navigate to the application root folder and run Docker Compose to build and start your containers:
```sh
docker-copose up -d
```
## 7. Finalize Setup
```sh
docker-compose exec app php artisan key:generate
docker-compose exec app php artisan migrate
```
## 8. Install Composer Dependencies (If Needed)
```sh
docker-compose exec app composer install
```
## 9. Generate Application Key and Run Migrations and Seeders
```sh
docker-compose exec app php artisan key:generate
docker-compose exec app php artisan migrate
docker-compose exec app php artisan db:seed
```
## 10. Adjust Permissions If Needed
```sh
docker-compose exec app chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache
docker-compose exec app chmod -R 775 /var/www/html/storage /var/www/html/bootstrap/cache
```
## 11. Access the Application
Your Laravel application should now be accessible at http://localhost:8000.
## 12. Final Notes
Adjust any configuration options as necessary for security.
Always remember to keep sensitive data secure, especially in production environments.
