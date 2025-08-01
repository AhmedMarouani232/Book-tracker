# Spring Boot Book Management - Backend

A secure RESTful API for managing books, categories, users, and download statistics with JWT-based authentication and role-based authorization.

## Features

- **JWT Authentication**: Secure user registration and login
- **Role-Based Authorization**: ADMIN, CLIENT, and CLIENTA (subscriber) roles
- **Book Management**: Add and retrieve books
- **Category Management**: Add and retrieve categories
- **File Handling**: Upload and download files (including Excel exports)
- **User Management**: Add, find, and manage users with different roles
- **Download Statistics**: Track book downloads by users
- **CORS Support**: Configured for frontend development
- **Password Encryption**: BCrypt password hashing

## API Endpoints

### Authentication
- `POST /auth/register` - Register a new user
- `POST /auth/authenticate` - Authenticate a user and get JWT token

### Book Management
- `POST /Book/addBook` - Add a new book (Authenticated)
- `GET /Book/getbooks` - Get all books (Authenticated)

### Category Management
- `POST /Category/addCategory` - Add a new category (Authenticated)
- `GET /Category/getCategories` - Get all categories (Authenticated)

### File Management
- `GET /files/downloadFile/{fileName}` - Download a file (Authenticated)
- `GET /files/downloadBooksExcel` - Download books as Excel (ADMIN only)
- `POST /files/uploadFile` - Upload a file (Authenticated)

### User Management
- `POST /User/addUser` - Add a new client user (Authenticated)
- `POST /User/addSubscriberUser` - Add a new subscriber user (Authenticated)
- `GET /User/findByEmail` - Find user by email (Authenticated)
- `GET /User/getAllUsers` - Get all users (Authenticated)
- `PUT /User/{userId}/editRole` - Edit user role (ADMIN only)
- `PUT /User/{id}/decreaseDownloadsRemaining` - Decrease user's remaining downloads (Authenticated)

### Download Statistics
- `POST /Statistics/download` - Record a book download (Authenticated)

## Security Implementation

### JWT Authentication Flow
1. Client sends credentials to `/auth/authenticate`
2. Server validates credentials and returns JWT token
3. Client includes token in `Authorization: Bearer <token>` header
4. Server validates token on each request

### Security Components
- **JwtAuthenticationFilter**: Validates JWT tokens on each request
- **JwtService**: Handles token generation, validation, and extraction
- **AppConfig**: Configures authentication provider and password encoder
- **SecurityConfiguration**: Defines security rules and CORS policy

### Roles
- **ADMIN**: Full access including user role management
- **CLIENT**: Regular user with limited downloads
- **CLIENTA**: Subscriber user with extended privileges

# React Book Management - Frontend
A React-based web application for managing books, users, and download statistics. Connects to a Spring Boot backend with JWT authentication.

## Features
📚 Book management (add, view)

👥 User authentication (login/register)

📊 Download statistics tracking

🔐 Role-based access (Admin/Client)

📥 File upload/download functionality

## Technologies
Frontend: React.js, Axios, React Router

Styling: CSS (or your preferred framework)

State Management: React Context/Hooks

Authentication: JWT (via backend API)