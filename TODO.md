# Expense Tracker Implementation TODO

## Backend (Java Spring Boot)
- [x] Create pom.xml with Spring Boot dependencies (web, data-jpa, sqlite-jdbc, lombok, validation)
- [x] Create Expense entity (id, amount BigDecimal, category, description, date LocalDate, createdAt LocalDateTime)
- [x] Create ExpenseRepository interface extending JpaRepository
- [x] Create ExpenseService with create (idempotent) and list (filter/sort) methods
- [x] Create ExpenseController with POST /expenses and GET /expenses endpoints, enable CORS
- [x] Create ExpenseTrackerApplication.java
- [x] Configure application.properties for SQLite database and JPA
- [x] Remove old Python backend files (main.py, crud.py, models.py, database.py, requirements.txt, Dockerfile, tests/)

## Frontend (React)
- [x] Update package.json to add Axios dependency
- [x] Create App.jsx with expense form, list/table, filter, sort, total display, loading/error handling
- [x] Create App.css for minimal plain CSS styling
- [x] Update main.jsx to import App.jsx and App.css

## Project Structure & Docs
- [x] Create README.md with design decisions, trade-offs, what not implemented, how to run
- [x] Organize clear folder structure

## Followup
- [ ] Install backend dependencies (Maven)
- [ ] Install frontend dependencies (npm)
- [ ] Run backend locally
- [ ] Run frontend locally
- [ ] Test functionality (add expense, list, filter, sort, total, retries, refresh)
