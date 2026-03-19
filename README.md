# ServiceHub

A comprehensive service booking and management platform built with Spring Boot backend and Android frontend. ServiceHub enables users to discover, book, and manage various services including carpooling, tutoring, home services, and more through an intuitive mobile interface.

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Backend Setup](#backend-setup)
- [Frontend Setup](#frontend-setup)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [Database](#database)
- [API Documentation](#api-documentation)
- [Testing](#testing)
- [Team & Contributors](#team--contributors)
- [License](#license)

## Project Overview

ServiceHub is a full-stack application designed to connect service providers with customers. The platform supports multiple service categories and provides real-time communication through WebSocket integration. This is a collaborative project developed as part of an educational initiative with multiple team members contributing specialized modules.

## Features

- **Multiple Service Categories**
  - User Profile Management
  - Booking & Reservation System
  - Carpooling Services
  - Real-time Chat
  - Cleaning Services
  - Home Services
  - Painting Services
  - Plumbing Services
  - Tutoring/Education Services

- **Backend Capabilities**
  - RESTful API architecture
  - WebSocket support for real-time communication
  - Database persistence with MySQL and ORM (Hibernate/JPA)
  - Comprehensive testing framework
  - Swagger/SpringFox API documentation

- **Frontend Features**
  - Native Android application
  - User authentication and profile management
  - Service browsing and booking interface
  - Real-time messaging
  - Responsive UI/UX design

## Architecture

The application follows a standard three-tier architecture:

```
┌─────────────────────────────────────┐
│      Android Frontend (Gradle)      │
│   - User Interface & Navigation     │
│   - Service Browsing & Booking      │
└──────────────┬──────────────────────┘
               │ HTTP/WebSocket
┌──────────────▼──────────────────────┐
│   Spring Boot REST API (Maven)      │
│   - Service Management              │
│   - User Management                 │
│   - Booking & Reservation           │
│   - Real-time Communication         │
└──────────────┬──────────────────────┘
               │ JDBC/JPA
┌──────────────▼──────────────────────┐
│      MySQL Database                 │
│   - User Data                       │
│   - Service Information             │
│   - Booking Records                 │
│   - Chat Messages                   │
└─────────────────────────────────────┘
```

## Tech Stack

### Backend
- **Framework**: Spring Boot 2.4.0
- **Java Version**: 11
- **Build Tool**: Maven
- **ORM**: Hibernate/JPA
- **Database**: MySQL
- **WebSocket**: Spring WebSocket
- **Testing**: JUnit 4, REST-Assured
- **Additional Libraries**: Lombok, Jackson, JAXB

### Frontend
- **Platform**: Android
- **Build Tool**: Gradle
- **Language**: Java

### Documentation
- **API Documentation**: Swagger/SpringFox
- **JavaDoc**: Comprehensive API documentation available in `/Documents/APIFrontend/javadoc/`

## Prerequisites

### For Backend Development
- Java Development Kit (JDK) 11 or higher
- Maven 3.6 or higher
- MySQL Server (running and accessible)
- Curl or Postman for API testing

### For Frontend Development
- Android SDK API 21 or higher
- Android Studio or compatible IDE
- Gradle 6.0 or higher

## Installation & Setup

### Clone the Repository

```bash
git clone <repository-url>
cd servicehub
```

## Backend Setup

### 1. Database Configuration

Before running the backend, ensure MySQL is running and accessible:

- **Default Connection String**: `jdbc:mysql://coms-309-063.class.las.iastate.edu:3306/coms_309`
- **Default Username**: `ec3`
- **Default Password**: `coms309`

To modify database credentials, edit [Backend/springboot_example/application.properties](Backend/springboot_example/application.properties):

```properties
spring.datasource.url=jdbc:mysql://your-host:3306/your-database
spring.datasource.username=your-username
spring.datasource.password=your-password
```

### 2. Build the Backend

```bash
cd Backend/springboot_example
mvn clean install
```

### 3. Run the Spring Boot Application

```bash
mvn spring-boot:run
```

The backend server will start on `http://localhost:8080`

### 4. Verify Backend is Running

Test the API with a simple health check:

```bash
curl http://localhost:8080/
```

## Frontend Setup

### 1. Open Android Project

```bash
cd Frontend/servicehub
```

Open the project in Android Studio or your IDE.

### 2. Build the APK

```bash
./gradlew build
```

### 3. Install on Device/Emulator

```bash
./gradlew installDebug
```

Or use Android Studio's built-in emulator runner.

### 4. Configure API Endpoint

Update the API endpoint in the Android application to point to your backend server:
- Change `localhost:8080` to your backend server address if running remotely

## Project Structure

```
ServiceHub/
├── Backend/
│   ├── springboot_example/          # Main Spring Boot Application
│   │   ├── src/main/java/onetoone/  # Source Code
│   │   │   ├── Users/               # User management module
│   │   │   ├── Profile/             # Profile management
│   │   │   ├── Booking/             # Booking system
│   │   │   ├── Reservation/         # Reservation management
│   │   │   ├── Chat/                # Real-time chat
│   │   │   ├── Carpooling/          # Carpooling service
│   │   │   ├── HomeService/         # General home services
│   │   │   ├── Cleaning/            # Cleaning service
│   │   │   ├── Painting/            # Painting service
│   │   │   ├── Plumbing/            # Plumbing service
│   │   │   ├── Tutors/              # Tutoring service
│   │   │   ├── Main.java            # Application entry point
│   │   │   └── SpringFoxConfig.java # API documentation config
│   │   ├── src/main/resources/      # Configuration and templates
│   │   ├── src/test/                # Unit and integration tests
│   │   ├── pom.xml                  # Maven dependencies
│   │   ├── application.properties   # Application configuration
│   │   ├── Client_JS/               # JavaScript test client
│   │   └── testClient.html          # HTML test client
│   └── .mvn/                        # Maven wrapper
│
├── Frontend/
│   └── servicehub/                  # Android Application
│       ├── app/                     # Main app module
│       │   ├── src/                 # Source code and resources
│       │   └── build.gradle         # Gradle build configuration
│       ├── gradle/                  # Gradle build files
│       ├── build.gradle             # Project build configuration
│       ├── settings.gradle          # Gradle project settings
│       └── gradlew                  # Gradle wrapper
│
├── Documents/
│   ├── APIFrontend/javadoc/         # Generated JavaDoc for API
│   ├── outputs-Ldutta/javadoc/      # Team member's API documentation
│   ├── Test Results/                # Test execution results
│   └── test.txt                     # Test logs
│
├── Experiments/
│   ├── ec3/                        # ec3's experimental modules
│   ├── Ldutta/                     # Ldutta's experimental modules
│   ├── npathuri/                   # npathuri's experimental modules
│   └── yvarun79/                   # yvarun79's experimental modules
│
└── README.md                        # This file
```

## Configuration

### Backend Configuration (application.properties)

The main configuration file is located at: [Backend/springboot_example/application.properties](Backend/springboot_example/application.properties)

**Key Properties:**

```properties
# Server Configuration
server.port=8080

# Database Configuration
spring.datasource.url=jdbc:mysql://coms-309-063.class.las.iastate.edu:3306/coms_309
spring.datasource.username=ec3
spring.datasource.password=coms309
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

# JPA/Hibernate Configuration
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL5Dialect
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.show-sql=true
```

## Database

### Database Setup

The application uses MySQL with Hibernate ORM for automatic schema generation and management.

**Key Features:**
- Automatic schema creation via `spring.jpa.hibernate.ddl-auto=update`
- Support for one-to-one, one-to-many, and many-to-many relationships
- Persistence of user data, service information, bookings, and messages

### Database Schema

The database includes tables for:
- Users and authentication
- Service profiles and details
- Bookings and reservations
- Chat messages and conversations
- User profiles and preferences

Hibernate will automatically create and manage these tables on first run.

## API Documentation

### Accessing API Documentation

Once the backend is running, access the Swagger UI at:
```
http://localhost:8080/swagger-ui.html
```

This provides interactive API documentation where you can test all endpoints.

### Generated JavaDoc

Complete JavaDoc documentation is available in:
- [Documents/APIFrontend/javadoc/index.html](Documents/APIFrontend/javadoc/index.html) - Main API documentation
- [Documents/outputs-Ldutta/javadoc/index.html](Documents/outputs-Ldutta/javadoc/index.html) - Additional team documentation

Generate fresh JavaDoc with Maven:
```bash
mvn javadoc:javadoc
```

## Testing

### Backend Testing

The project includes comprehensive test suites using JUnit and REST-Assured.

**Run all tests:**
```bash
cd Backend/springboot_example
mvn test
```

**Run specific test class:**
```bash
mvn test -Dtest=YourTestClassName
```

**Test reports** are available in [Documents/Test Results/](Documents/Test%20Results/)

### Testing with JavaScript Client

A JavaScript-based test client is available for manual API testing:
- File: [Backend/springboot_example/Client_JS/index.html](Backend/springboot_example/Client_JS/index.html)
- Static HTML test client: [Backend/springboot_example/testClient.html](Backend/springboot_example/testClient.html)

Open these files in a browser to test the API with WebSocket support.

## Team & Contributors

ServiceHub is a collaborative project with contributions from multiple team members:

- **ec3** - [Experiments/ec3/](Experiments/ec3/)
- **Ldutta** - [Experiments/Ldutta/](Experiments/Ldutta/)
- **npathuri** - [Experiments/npathuri/](Experiments/npathuri/)
- **yvarun79** - [Experiments/yvarun79/](Experiments/yvarun79/)

Each team member has their own experimental directory containing specialized implementations and variations of the ServiceHub platform.

## Support & Troubleshooting

### Common Issues

**Database Connection Failed**
- Ensure MySQL is running: `mysql -u root -p`
- Verify credentials in `application.properties`
- Check MySQL server is accessible at configured host/port

**Port 8080 Already in Use**
- Change port in `application.properties`: `server.port=8081`
- Or kill the process using port 8080

**Android Build Failures**
- Update Android SDK: Open SDK Manager in Android Studio
- Clear Gradle cache: `./gradlew clean`
- Rebuild project: `./gradlew build`

### Getting Help

- Check API documentation at `http://localhost:8080/swagger-ui.html`
- Review test files for usage examples
- Check generated JavaDoc for API details
- Review team member experiments for alternative implementations

## Future Enhancements

Potential areas for expansion:
- Payment integration for service bookings
- Rating and review system
- Advanced search and filtering
- Push notifications
- Analytics dashboard
- Third-party service integrations

## License

This project is part of an educational initiative at Iowa State University (CS 309 Course).

---

**Last Updated**: March 2026
**Version**: 1.0.0
