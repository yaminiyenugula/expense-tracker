# Expense Tracker

A minimal production-ready full-stack Expense Tracker application.

## Tech Stack

- **Backend**: Java 17, Spring Boot, Spring Data JPA, SQLite
- **Frontend**: React, Axios, plain CSS

## Features

- Add expenses with amount, category, description, and date
- View list of expenses sorted by date (newest first)
- Filter expenses by category
- Display total amount of visible expenses
- Retry-safe expense creation (avoids duplicates)
- Handles loading states, errors, and multiple submits

## Design Decisions

- **Backend**:
  - Used Spring Boot for rapid development and built-in features like validation and CORS.
  - SQLite for simplicity and file-based persistence (no external DB setup required).
  - BigDecimal for precise money handling to avoid floating-point issues.
  - Idempotent POST /expenses by checking for exact duplicates (same amount, category, description, date).
  - Validation on amount (>0) and date (required) using Bean Validation.

- **Frontend**:
  - React with hooks for state management.
  - Axios for HTTP requests with error handling.
  - Plain CSS for minimal styling (no frameworks to keep it simple).
  - Disabled submit button during API calls to prevent multiple submits.
  - Automatic refresh of list after adding expense.

## Trade-offs

- **SQLite**: Chosen for ease of setup, but not suitable for high-concurrency production (single-writer). For production, consider PostgreSQL or MySQL.
- **No Authentication**: Not implemented as per requirements, but essential for multi-user scenarios.
- **Simple Duplicate Check**: Uses exact match on fields; in production, might need more sophisticated deduplication (e.g., request IDs).
- **No Pagination**: GET /expenses returns all expenses; for large datasets, add pagination.
- **No Error Boundaries**: Basic error handling; in production, add global error boundaries in React.
- **No Tests**: Not implemented due to time constraints; in production, add unit and integration tests.

## What Was Intentionally Not Implemented

- User authentication and authorization
- Expense editing/deletion (only create and read)
- Advanced filtering (e.g., date range)
- Export functionality
- Responsive design (desktop-only)
- Animations or advanced UI components
- Caching or offline support
- API rate limiting
- Logging and monitoring
- Dockerization (though Dockerfile was in original Python backend)

## How to Run Locally

### Prerequisites

- Java 17
- Node.js 16+
- Maven 3.6+

### Backend

1. Navigate to `backend/` directory:
   ```
   cd backend
   ```

2. Install dependencies:
   ```
   mvn clean install
   ```

3. Run the application:
   ```
   mvn spring-boot:run
   ```

   The backend will start on `http://localhost:8080`.

### Frontend

1. Navigate to `frontend/` directory:
   ```
   cd frontend
   ```

2. Install dependencies:
   ```
   npm install
   ```

3. Run the development server:
   ```
   npm run dev
   ```

   The frontend will start on `http://localhost:5173` (default Vite port).

### Usage

1. Open the frontend in your browser.
2. Add expenses using the form.
3. View the list of expenses below.
4. Use the category filter to narrow down expenses.
5. The total of visible expenses is shown at the bottom.

## API Endpoints

- `POST /expenses`: Create a new expense (JSON body: amount, category, description, date)
- `GET /expenses`: Get list of expenses (query params: category for filter)
