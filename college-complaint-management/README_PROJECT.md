# CampusVoice – College Complaint Management System

## Run
1. MySQL: create database `complaint_management_db` (credentials in `backend/src/main/resources/application.properties`).
2. `cd backend && ./mvnw spring-boot:run`  → http://localhost:8080
3. `cd frontend && npm install && npm run dev` → http://localhost:5173

First start auto-creates: **admin@college.edu / Admin@123**, 6 departments, 6 categories. Change the admin password after first login.
Students self-register on the login page (role is always STUDENT; admins can only be created via the seeder/DB).

## Roles
**Student**: register/login, submit complaint, track status + admin replies, withdraw (reason required, only while OPEN / IN_PROGRESS).
**Admin**: view all complaints, edit, assign department, change status, reply, delete; full CRUD on departments and categories; view/delete students.

## API
| Method & path | Who |
|---|---|
| POST /students/register, /students/login | public |
| POST /complaints, GET /complaints/mine, PUT /complaints/{id}/withdraw `{reason}` | student |
| GET /complaints/{id}, GET /complaints/{id}/responses | owner or admin |
| GET /complaints, PUT /complaints/{id}, PUT /complaints/{id}/status, DELETE /complaints/{id}, POST /complaints/{id}/responses | admin |
| GET /departments, /complaint-categories | any logged-in user |
| POST/PUT/DELETE /departments, /complaint-categories | admin |
| GET/PUT/DELETE /students/** | admin |
