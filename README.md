# TODO Application

A simple TODO application built using Spring Boot, Thymeleaf, JPA (Hibernate), and Bootstrap. This application allows users to add, delete, and toggle tasks (mark as completed or incomplete).

## Features

- Add a new task
- View all tasks
- Toggle task completion status
- Delete a task

## Technologies Used

- **Backend:** Spring Boot, Spring MVC, Spring Data JPA
- **Frontend:** Thymeleaf, Bootstrap 5
- **Database:** MySQL 

## Project Structure

```
- src/main/java/com/app/todoapp/
  - controller/      # Handles HTTP requests
  - models/          # Entity class (Task.java)
  - service/         # Business logic
  - repository/      # Data access layer
- src/main/resources/templates/  # Thymeleaf templates (HTML pages)
- src/main/resources/static/     # Static resources (CSS, JS, etc.)
- src/main/resources/application.properties  # Database configurations
```

## Installation and Setup

1. **Clone the repository:**
   ```sh
   git clone https://github.com/your-username/todo-app.git
   cd todo-app
   ```
2. **Run the application:**
   ```sh
   mvn spring-boot:run
   ```
   The application will be available at `http://localhost:8080`

## Endpoints

| Method | Endpoint       | Description        |
| ------ | -------------- | ------------------ |
| GET    | `/`            | Fetch all tasks    |
| POST   | `/`            | Add a new task     |
| GET    | `/{id}/delete` | Delete a task      |
| GET    | `/{id}/toggle` | Toggle task status |

## Database Configuration

Modify `src/main/resources/application.properties` to use a different database:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/todo_db
spring.datasource.username=root
spring.datasource.password=root
spring.jpa.hibernate.ddl-auto=update
```

## Future Enhancements

- Add user authentication
- Add due dates for tasks
- Implement REST API endpoints
- Deploy on AWS/Heroku

## License

This project is licensed under the MIT License.

---

### Coding Explanation

#### 1. **TaskController.java** (Handles HTTP requests)
   - `@GetMapping` - Retrieves all tasks and passes them to the frontend.
   - `@PostMapping` - Creates a new task with the given title.
   - `@GetMapping("/{id}/delete")` - Deletes a task by ID.
   - `@GetMapping("/{id}/toggle")` - Toggles the completion status of a task.

#### 2. **Task.java** (Entity Model)
   - Annotated with `@Entity` for JPA.
   - `@Id @GeneratedValue(strategy = GenerationType.AUTO)` - Auto-generates task IDs.
   - Has fields `title` and `completed` to store task details.

#### 3. **TaskService.java** (Business Logic)
   - `getAllTasks()` - Fetches all tasks from the repository.
   - `createTask(String title)` - Creates a new task.
   - `deleteTask(Long id)` - Deletes a task by ID.
   - `toggleTask(Long id)` - Flips the `completed` status of a task.

#### 4. **TaskRepository.java** (Data Layer)
   - Extends `JpaRepository<Task, Long>` to provide database access.
   - Allows CRUD operations without writing SQL queries.

#### 5. **tasks.html** (Frontend using Thymeleaf)
   - Displays all tasks.
   - Provides form input for adding a task.
   - Buttons for toggling and deleting tasks.

### Interview Notes

- **Project Overview:**
  - A CRUD-based TODO application.
  - Uses Spring Boot MVC pattern for structuring.
- **Key Challenges Faced:**
  - Understanding Thymeleaf templating.
  - Implementing toggling functionality efficiently.
- **Key Learnings:**
  - How to integrate Thymeleaf with Spring Boot.
  - Handling HTTP requests in a Spring Boot application.
  - Working with JPA (Hibernate) to manage database operations.

