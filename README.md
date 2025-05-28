# Newcomer Navigator

![Newcomer Navigator Logo](images/logo.png) <!-- Replace with actual logo if available -->

**Newcomer Navigator** is a web application designed to assist newcomers in Bhopal, India, such as students, tourists, and visitors, in finding food corners, accommodations near colleges, and popular tourist attractions. The app provides a user-friendly interface to search for restaurants by meal type and location, accommodations by stay type and college proximity, and tourist spots with details like ratings and directions. It includes secure user authentication with login, registration, and OTP-based password reset via email.

This project showcases full-stack development using Java Servlets, JSP, MySQL, and Maven, with dynamic frontend interactions powered by AJAX and jQuery.

## Table of Contents
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Setup Instructions](#setup-instructions)
- [Usage](#usage)
- [Screenshots](#screenshots)
- [Challenges and Learnings](#challenges-and-learnings)
- [Future Improvements](#future-improvements)
- [Live Demo](#live-demo)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## Features
- **Food Corner Search**: Find restaurants in Bhopal by selecting a meal type (e.g., breakfast, lunch) and location, with details like shop name, ratings, specialities, and directions.
- **Accommodation Search**: Discover lodges, hotels, or hostels near colleges, with information on price, location, and ratings.
- **Tourist Attractions**: Explore popular tourist spots with images, ratings, opening hours, and directions.
- **User Authentication**:
  - Login and registration with email and password.
  - OTP-based password reset via email using Jakarta Mail.
- **Dynamic UI**: AJAX-powered searches for seamless user experience without page reloads.
- **Responsive Design**: Built with Bootstrap and CSS for mobile-friendly layouts.

## Tech Stack
- **Backend**: Java Servlets, Jakarta Mail (for OTP emails), Gson (for JSON serialization)
- **Frontend**: JSP, HTML, CSS, JavaScript, jQuery, Bootstrap, Font Awesome, SweetAlert
- **Database**: MySQL (`Newcomer_Navigator` database)
- **Build Tool**: Maven
- **Server**: Apache Tomcat (for local deployment)
- **Dependencies**:
  - `jakarta.servlet:jakarta.servlet-api:6.0.0`
  - `com.mysql:mysql-connector-j:8.1.0`
  - `com.google.code.gson:gson:2.8.8`
  - `jakarta.mail:jakarta.mail-api:2.1.2`
  - `org.eclipse.angus:jakarta.mail:2.0.2`
  - `jakarta.servlet.jsp:jakarta.servlet.jsp-api:3.1.1`

## Project Structure
```
Newcomer_Navigator/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   ├── Bhopal.java
│   │   │   ├── CBhopal.java
│   │   │   ├── Collegeservlet.java
│   │   │   ├── DataServlet.java
│   │   │   ├── House.java
│   │   │   ├── NewPassword.java
│   │   │   ├── OTP.java
│   │   │   ├── Placeservlet.java
│   │   │   ├── Restaurant.java
│   │   │   ├── SDataServlet.java
│   │   │   ├── ValidateOtp.java
│   │   │   ├── generateOTP.java
│   │   │   ├── login.java
│   │   │   ├── registration.java
│   │   ├── webapp/
│   │       ├── WEB-INF/
│   │       │   ├── web.xml
│   │       ├── css/
│   │       ├── images/
│   │       ├── js/
│   │       ├── videos/
│   │       ├── EnterOtp.jsp
│   │       ├── food.jsp
│   │       ├── forgotPassword.jsp
│   │       ├── index.jsp
│   │       ├── newPassword.html
│   │       ├── stay.jsp
│   │       ├── tour.jsp
├── pom.xml
├── README.md
```

## Setup Instructions
To run the project locally, follow these steps:

### Prerequisites
- **Java**: JDK 17 or higher
- **Maven**: 3.8.0 or higher
- **MySQL**: 8.0 or higher
- **Apache Tomcat**: 10.1 or higher
- **Git**: For cloning the repository
- **Gmail Account**: For sending OTP emails (requires an app-specific password)

### Steps
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/newcomer-navigator.git
   cd newcomer-navigator
   ```

2. **Set Up MySQL Database**:
   - Create a database named `Newcomer_Navigator`:
     ```sql
     CREATE DATABASE Newcomer_Navigator;
     ```
   - Import the schema and data (if provided in `newcomer.sql`):
     ```bash
     mysql -u root -p Newcomer_Navigator < newcomer.sql
     ```
   - Update database credentials in servlets (e.g., `DataServlet.java`, `NewPassword.java`):
     ```java
     Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/Newcomer_Navigator", "your-username", "your-password");
     ```

3. **Configure Email for OTP**:
   - In `generateOTP.java`, update the Gmail credentials:
     ```java
     return new PasswordAuthentication("your-email@gmail.com", "your-app-specific-password");
     ```
   - Generate an app-specific password via Google Account > Security > 2-Step Verification > App Passwords.

4. **Build the Project**:
   ```bash
   mvn clean package
   ```

5. **Deploy to Tomcat**:
   - Copy the generated WAR file (`target/ProjectK-1.0-SNAPSHOT.war`) to Tomcat’s `webapps` folder.
   - Start Tomcat:
     ```bash
     ./apache-tomcat-10.1.x/bin/startup.sh  # Linux/Mac
     .\apache-tomcat-10.1.x\bin\startup.bat  # Windows
     ```

6. **Access the Application**:
   - Open a browser and navigate to:
     ```
     http://localhost:8080/projectK
     ```
   - Replace `projectK` with your WAR file’s context path if different.

7. **Test Features**:
   - Register a new user (`index.jsp`).
   - Search for restaurants (`food.jsp`).
   - Find accommodations (`stay.jsp`).
   - Reset password (`forgotPassword.jsp`).

## Usage
- **Homepage**: Log in or register to access features. Browse food, stay, or tour sections.
- **Food Search**: Select a meal type and location to view restaurant details (e.g., ratings, directions).
- **Accommodation Search**: Choose a stay type and college to find nearby lodges or hotels.
- **Tourist Attractions**: Explore Bhopal’s attractions with images and details.
- **Forgot Password**: Enter your email to receive an OTP, verify it, and set a new password.

## Screenshots
<!-- Add screenshots to the `images/` folder and update links -->
| Homepage | Food Search | Accommodation Search | Forgot Password |
|----------|-------------|----------------------|-----------------|
| ![Homepage](images/homepage.png) | ![Food Search](images/food-search.png) | ![Stay Search](images/stay-search.png) | ![Forgot Password](images/forgot-password.png) |

## Challenges and Learnings
- **Dynamic UI**: Implemented AJAX with jQuery to load search results without page reloads, improving user experience.
- **Email OTP**: Configured Jakarta Mail to send OTPs via Gmail’s SMTP server, learning SMTP protocols and session management.
- **Database Consistency**: Fixed a database name mismatch in `NewPassword.java` (from `projectx` to `Newcomer_Navigator`), reinforcing the importance of configuration management.
- **Learnings**: Gained hands-on experience with full-stack Java development, database design, and client-server communication.

## Future Improvements
- **Password Security**: Implement BCrypt to hash passwords instead of storing them in plain text.
- **Database Optimization**: Use a connection pool (e.g., HikariCP) for efficient MySQL connections.
- **External APIs**: Integrate Google Maps API for dynamic directions and SendGrid for reliable email delivery.
- **Frontend Upgrade**: Migrate to a modern framework like React for a more interactive UI.
- **Testing**: Add JUnit tests for servlets and integration tests for database queries.

## Live Demo
<!-- Update with actual link if deployed -->
[Live Demo](https://newcomer-navigator.herokuapp.com) (Coming soon)

## Contributing
Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Make your changes and commit (`git commit -m "Add your feature"`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a pull request.

## License
This project is licensed under the [MIT License](LICENSE).

## Contact
- **Author**: [Your Name]
- **Email**: [your.email@example.com]
- **GitHub**: [github.com/your-username](https://github.com/your-username)
- **LinkedIn**: [linkedin.com/in/your-profile](https://linkedin.com/in/your-profile)

Feel free to reach out with questions or feedback!
