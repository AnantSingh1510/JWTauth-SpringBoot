Blog Application Backend
This project is a backend for a blog application developed using Spring Boot. It incorporates Spring Security for authentication and authorization, utilizing JWT (JSON Web Tokens) for secure, stateless authentication. The application supports role-based access control, distinguishing between roles like ADMIN and USER. It connects to a MySQL database by default but can also be configured to use an H2 in-memory database for development and testing purposes.

Features
RESTful API for managing blog posts, comments, and users.
Secure user authentication using JWT.
Role-based access control.
Connection to MySQL and optional H2 database for easy testing.
Comprehensive error handling and validation.
Prerequisites
Before you can run this project, you will need:

Java JDK 11 or later
Maven 3.6 or later
MySQL Server (Optional for production)
Configuration
Database Setup
MySQL
Install MySQL and start the MySQL service.
Create a database for the application:
sql
Copy code
CREATE DATABASE blog_app;
Update src/main/resources/application.properties for MySQL:
properties
Copy code
spring.datasource.url=jdbc:mysql://localhost:3306/blog_app
spring.datasource.username=your_mysql_username
spring.datasource.password=your_mysql_password
H2 Database
The application is configured to use H2 in development. You can access the H2 console at http://localhost:8080/h2-console with the JDBC URL set to jdbc:h2:mem:testdb.

JWT Configuration
Set your JWT secret and expiration time in src/main/resources/application.properties:

properties
Copy code
app.jwt.secret=your_secret_key
app.jwt.expiration-ms=86400000  # 24 hours
Running the Application
To run the application, use the following command from the root directory of the project:

bash
Copy code
mvn spring-boot:run
API Endpoints
The following are the main endpoints provided by the blog application:

Auth
POST /api/auth/signup - Register a new user.
POST /api/auth/login - Authenticate a user and return a JWT.
Posts
POST /api/home/posts - Create a new blog post (Admin and User).
GET /api/home/posts - Retrieve all posts.

Security
This application uses Spring Security to handle authentication and authorization. The security configuration is set up in com.example.blog.security.SecurityConfig. The configuration includes JWT authentication filter, which intercepts and processes the authentication token.
