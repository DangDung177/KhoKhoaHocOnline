# Java Spring Boot Project: Online Course Management System (LMS-lite)

## ✅ Step-by-Step Development Plan

### 🧱 Phase 1: Project Setup

1. **Create the Spring Boot project**
   - Use Spring Initializr or VSCode GUI
   - Dependencies:
     - Spring Web
     - Spring Data JPA
     - PostgreSQL Driver
     - Spring Boot DevTools
     - Spring Security
     - (Optional) Spring Validation, Lombok

2. **Configure `application.properties`**
   ```properties
   spring.datasource.url=jdbc:postgresql://localhost:5432/lms_db
   spring.datasource.username=postgres
   spring.datasource.password=your_password
   spring.jpa.hibernate.ddl-auto=update
   spring.jpa.show-sql=true
   spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
   ```

### 📦 Phase 2: Define Entities & Relationships

3. **Create `User` Entity** (Student or Admin)
   - Fields: id, name, email, password, role
   - Role: Enum (ADMIN, STUDENT)

4. **Create `Course` Entity**
   - Fields: id, title, description, instructorName
   - Relation: @ManyToOne User (Instructor)

5. **Create `Lesson` Entity**
   - Fields: id, courseId, title, content
   - Relation: @ManyToOne Course

6. **Create `Enrollment` Entity**
   - Fields: id, studentId, courseId, enrollmentDate
   - Relations: @ManyToOne Student + Course

7. **Create `Progress` Entity**
   - Fields: id, studentId, lessonId, status (Enum)

### ⚙️ Phase 3: Repositories & Services

8. **Create Repository interfaces**
   - UserRepository, CourseRepository, etc. → extend JpaRepository

9. **Create Service layer**
   - CourseService, EnrollmentService, etc.
   - Business logic like:
     - Prevent duplicate enrollment
     - Auto-create progress entries when student enrolls

### 🔒 Phase 4: Authentication & Role-Based Access

10. **Set up Spring Security**
   - JWT authentication (or basic login with BCryptPasswordEncoder)
   - Define access rules:
     - /api/admin/** → ADMIN
     - /api/student/** → STUDENT

11. **Register & Login**
   - POST /auth/register
   - POST /auth/login → returns token

### 🔁 Phase 5: Controllers & Endpoints

12. **Build API Controllers**
   - UserController (register, login, list)
   - CourseController (CRUD by Admin)
   - LessonController (add/view lessons)
   - EnrollmentController (student enrolls in course)
   - ProgressController (track lesson progress)

### 📄 Phase 6: API Testing & Documentation

13. **Use Postman or Swagger**
   - Test APIs with real requests
   - Add OpenAPI/Swagger (springdoc-openapi-ui) to generate docs

### 🚀 Phase 7: Extras for a Strong CV

14. **Validation**
   - Use @Valid, @NotBlank, etc. in DTOs

15. **DTOs & Mappers**
   - Avoid exposing entities directly in API

16. **Unit Testing (Optional but impressive)**
   - Use @SpringBootTest and JUnit

17. **Dockerize It**
   - Add Dockerfile and docker-compose.yml for backend + PostgreSQL

18. **Deploy (Optional)**
   - Use Render, Railway, or EC2 to host API and PostgreSQL

## 📌 Sample Milestone Timeline

| Day | Task |
|-----|------|
| 1   | Project setup, config, User entity |
| 2   | Course, Lesson, Enrollment models |
| 3   | Repositories, Services, Controllers |
| 4   | Add authentication and login logic |
| 5   | Protect routes by role |
| 6   | Test all APIs with Postman |
| 7   | Polish & document (Swagger, GitHub README, screenshots) |

## ✅ Final Deliverables for CV

- GitHub Repo with:
  - Clear README
  - /api/docs (Swagger)
  - Screenshot of Postman tests
  - Docker setup (optional)
- Deployed demo (bonus)
