# CampusVoice — College Complaint Management System

CampusVoice is a full-stack college complaint management platform that helps students submit and track grievances while allowing administrators to manage, assign, update, and resolve complaints efficiently.

## Features

- Student registration and login
- Admin authentication and dashboard
- Submit complaints with category, department, priority, and description
- Upload image, video, and document attachments
- Track complaint status and progress
- Withdraw complaints with a reason
- Admin complaint search, filtering, editing, assignment, and deletion
- Admin responses and official feedback
- Department and complaint-category management
- Student account management
- Responsive desktop, tablet, and mobile UI
- Role-based navigation menus
- Complaint-focused branding with a Document + Pencil logo

## Technology Stack

### Frontend

- React
- Vite
- React Router
- Axios
- Responsive CSS

### Backend

- Java
- Spring Boot
- Spring Data JPA
- Spring Security
- MySQL

## Project Structure

```text
college-complaint-management/
├── backend/     # Spring Boot REST API
├── frontend/    # React + Vite client
├── postman_collection.json
└── README.md
```

## Requirements

- Java 21 or later
- Node.js 18 or later
- npm
- MySQL 8 or later

## Database Setup

Create a MySQL database named:

```sql
CREATE DATABASE complaint_management_db;
```

Update the database username, password, and connection settings in:

```text
backend/src/main/resources/application.properties
```

Do not commit real database passwords or production secrets to GitHub.

## Run the Backend

From the `backend` directory:

### Windows

```bash
mvnw.cmd spring-boot:run
```

### macOS / Linux

```bash
./mvnw spring-boot:run
```

The backend runs at:

```text
http://localhost:8080
```

## Run the Frontend

From the `frontend` directory:

```bash
npm install
npm run dev
```

The frontend runs at:

```text
http://localhost:5173
```

## Default Admin Login

Use these credentials for local development:

```text
Email: admin@college.edu
Password: Admin@123
```

Change the admin password before using the application in production.

## Production Build

```bash
cd frontend
npm run build
```

## Separate Deployment

### Frontend on Vercel

Set the Vercel root directory to `frontend` and use:

```text
Build command: npm run build
Output directory: dist
Environment variable: VITE_API_URL=https://your-backend-url
```

### Backend on Railway or Render

Set the service root directory to `backend` and use:

```bash
./mvnw clean package -DskipTests
java -jar target/*.jar
```

Configure these backend environment variables:

```text
DB_URL=jdbc:mysql://your-mysql-host:3306/complaint_management_db
DB_USERNAME=your_database_user
DB_PASSWORD=your_database_password
FRONTEND_URL=https://your-frontend.vercel.app
PORT=8080
```

The backend reads `FRONTEND_URL` for CORS and `DB_*` variables for the production database connection.

### Current Deployment URLs

```text
Frontend: https://cybershield-workspace.vercel.app/app/team
Backend:  https://cybershield-api-production-9275.up.railway.app
```

Set this variable in Railway before redeploying the backend:

```text
FRONTEND_URL=https://cybershield-workspace.vercel.app
```

## API Overview

| Method | Endpoint | Access |
|---|---|---|
| POST | `/students/register` | Public |
| POST | `/students/login` | Public |
| POST | `/complaints` | Student |
| GET | `/complaints/mine` | Student |
| PUT | `/complaints/{id}/withdraw` | Student |
| GET | `/complaints` | Admin |
| PUT | `/complaints/{id}` | Admin |
| PUT | `/complaints/{id}/status` | Admin |
| POST | `/complaints/{id}/responses` | Admin |
| GET | `/departments` | Authenticated user |
| GET | `/complaint-categories` | Authenticated user |

See `postman_collection.json` for additional API examples.

## Security

Before deploying this project:

- Change all default credentials.
- Store database credentials in environment variables or a secrets manager.
- Configure a production JWT secret.
- Restrict CORS to trusted frontend domains.
- Enable HTTPS in production.
- Review file upload size and type restrictions.

## License

This project is intended for educational and institutional project use.
