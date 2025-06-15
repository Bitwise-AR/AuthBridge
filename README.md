# 🔐 AuthBridge

A robust and secure **Authentication System** built using **Java Spring Boot** and **React.js**, featuring complete auth flows like **Signup, Login, Email Verification, Password Reset**, and **User Session Handling via Cookies**.

> AuthBridge bridges security and user experience — the right way.

---

## 🚀 Features

- ✅ User Signup and Login
- 📧 Email Verification via OTP
- 🔑 Password Reset with OTP (expiry based)
- 🔒 JWT Token Based Authentication
- 🍪 Cookie Support for Storing Tokens
- 🧾 User Data Stored in MySQL Database
- ⚛️ Beautiful React Frontend with React Router, Hooks & Axios
- 📅 Timestamps for user creation and updates

---

## 🛠️ Tech Stack

### Backend
- Java 24
- Spring Boot
- Spring Security
- JWT Token
- JavaMailSender
- MySQL Workbench
- Maven

### Frontend
- React.js
- Axios
- React Hooks
- React Router DOM
- TailwindCSS *(optional styling)*

---

## 📁 Project Structure
```
AuthBridge/
├── AuthBridge_sb/
│ ├── src/main/java/com/authbridge/
│ │ ├── controller/
│ │ ├── model/
│ │ ├── repository/
│ │ ├── service/
│ │ ├── config/
│ │ └── AuthBridgeApplication.java
│ └── resources/
│ ├── application.properties
│ └── templates/
├── AuthBridge_react/
│ ├── public/
│ └── src/
│ ├── components/
│ ├── pages/
│ ├── App.js
│ └── index.js
├── pom.xml
└── README.md
```

---

## 🧑‍💻 Installation Guide

### 🔧 Backend Setup

1. Clone the repository:
```bash
  git clone https://github.com/your-username/AuthBridge.git
  cd AuthBridge/AuthBridge_sb
```

2. MySQL Database Setup:
```
  CREATE DATABASE authbridge;
  USE authbridge;
  
  CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id VARCHAR(255) UNIQUE,
    name VARCHAR(255),
    email VARCHAR(255) UNIQUE,
    password VARCHAR(255),
    is_account_verified BOOLEAN,
    verify_otp VARCHAR(6),
    verify_otp_expire_at TIMESTAMP,
    reset_otp VARCHAR(6),
    reset_otp_expire_at TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
  );
```

3. Configure application.properties:
```
  spring.datasource.url=jdbc:mysql://localhost:3306/authbridge
  spring.datasource.username=YOUR_DB_USERNAME
  spring.datasource.password=YOUR_DB_PASSWORD
  
  spring.jpa.hibernate.ddl-auto=update
  spring.jpa.show-sql=true
  
  # Mail Config
  spring.mail.host=smtp.gmail.com
  spring.mail.port=587
  spring.mail.username=your_email@gmail.com
  spring.mail.password=your_app_password
  spring.mail.properties.mail.smtp.auth=true
  spring.mail.properties.mail.smtp.starttls.enable=true
  
  # JWT
  jwt.secret=your_jwt_secret_key
```

4. Start the Spring Boot server:
```bash
  ./mvnw spring-boot:run
```

### 🎨 Frontend Setup

1. Navigate to frontend:
```bash
  cd AuthBridge/AuthBridge_react
```
2. Install dependencies:
```bash
  npm install
```
3. Run the frontend:
```bash
  npm run dev
```

---

## 🗃️ MySQL Table Structure

| Column Name                | Description              |
|----------------------------|--------------------------|
| id                         | Auto-incremented primary key             |
| user_id                    | Unique user identifier (UUID or String)        |
| name                       | Full name of the user     |
| email                      | Unique email address      |
| password                   | Hashed password |
| verify_otp                 | OTP for email verification |
| verify_otp_expire_at       | OTP expiry timestamp for verification |
| reset_otp                  | OTP for password reset |
| reset_otp_expire_at        | OTP expiry timestamp for reset OTP |
| created_at                 | Timestamp of account creation |
| updated_at                 | Timestamp of last account update |

---

## API Endpoint Routes

| Method | Endpoint  | Description              |
|--------|-----------|--------------------------|
| POST   | `/register`   | New user registration             |
| POST   | `/login`    | Authenticated login              |
| POST   | `/logout`    | Logout the user              |
| POST   | `/send-reset-otp`    | Reset OTP Email              |
| POST   | `/reset-password`    | Reset Password              |
| POST   | `/send-otp`    | Send OTP              |
| POST   | `/verify-otp`    | Verify OTP             |
| GET    | `/profile`    | Read Profile      |
| GET    | `/is-authenticated`   | Check if user is authenticated  |

---

## 🧠 Future Enhancements
  - Google/GitHub OAuth2 login
  - OTP resend timer with cooldown
  - Brute-force protection
  - Dark mode support

---

## 🤝 Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are greatly appreciated.

If you have a suggestion that would make this project better, please fork the repository and create a pull request. You can also simply open an issue with the tag "enhancement".

- **Fork the Project**
- **Create your Feature Branch (git checkout -b feature/AmazingFeature)**
- **Commit your Changes (git commit -m 'Add some AmazingFeature')**
- **Push to the Branch (git push origin feature/AmazingFeature)**
- **Open a Pull Request**

---

## 📜 Licence

This project is open-source and available under the [MIT License](LICENSE).

----
