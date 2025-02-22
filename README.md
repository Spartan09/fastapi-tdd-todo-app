# FastAPI Todo Application

A robust REST API for managing todos with user authentication and role-based access control, built using FastAPI and SQLAlchemy.

## Features

- User authentication with JWT tokens
- Role-based access control (Admin and Regular users)
- CRUD operations for todos
- User management with password hashing
- Database migrations using Alembic
- SQLite database integration

## Tech Stack

- FastAPI
- SQLAlchemy
- Alembic
- Pydantic
- PassLib
- Python-Jose
- SQLite

## Getting Started

### Prerequisites

- Python 3.7+
- pip

### Installation

1. Clone the repository
```bash
git clone https://github.com/yourusername/fastapi-todo-app.git
cd fastapi-todo-app
```

2. Create a virtual environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
```

3. Install dependencies
```bash
pip install -r requirements.txt
```

4. Run database migrations
```bash
alembic upgrade head
```

5. Start the server
```bash
uvicorn todoapp.main:app --reload
```

The API will be available at `http://localhost:8000`

## API Documentation

Once the server is running, you can access:
- Interactive API documentation: `http://localhost:8000/docs`
- Alternative API documentation: `http://localhost:8000/redoc`

## API Endpoints

### Authentication
- `POST /auth/` - Create new user
- `POST /auth/token` - Login and get access token

### Todos
- `GET /` - Get all todos for authenticated user
- `GET /todo/{todo_id}` - Get specific todo
- `POST /todo` - Create new todo
- `PUT /todo/{todo_id}` - Update todo
- `DELETE /todo/{todo_id}` - Delete todo

### Users
- `GET /user/` - Get user information
- `PUT /user/password` - Change password

### Admin
- `GET /admin/todo` - Get all todos (admin only)
- `DELETE /admin/todo/{todo_id}` - Delete any todo (admin only)

## Database Schema

### Users Table
- id (Primary Key)
- email (Unique)
- username (Unique)
- first_name
- last_name
- hashed_password
- is_active
- role
- phone_number

### Todos Table
- id (Primary Key)
- title
- description
- priority
- complete
- owner_id (Foreign Key to Users)

## Security Features

- Password hashing using bcrypt
- JWT token authentication
- Role-based access control
- Token expiration
- Secure password validation
