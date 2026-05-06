# Post-Disaster Reconstruction Backend

This repository contains the backend API for a real-time hazard reporting and reconstruction planning system.

## Project Overview

The backend provides secure user authentication, project management, and hazard/resource reporting capabilities. It is designed to support a real-time disaster response workflow where volunteers, coordinators, and responders can:

- register and log in
- create and list reconstruction or relief projects
- submit and retrieve hazard/resource reports
- keep project and response data available for real-time coordination

## Key Features

- FastAPI web framework
- JWT-based authentication
- PostgreSQL for user and project data
- MongoDB for hazard/resource reporting data
- REST API endpoints for auth, projects, and resources

## Architecture

- `backend/app/main.py` — FastAPI application entrypoint
- `backend/app/routes/auth_routes.py` — registration and login endpoints
- `backend/app/routes/projects_routes.py` — project creation and listing
- `backend/app/routes/resources_routes.py` — hazard/resource reporting APIs
- `backend/app/auth.py` — token creation and current-user validation
- `backend/app/database.py` — PostgreSQL and MongoDB connection setup
- `backend/app/models.py` — SQLAlchemy models for users and projects
- `backend/app/schemas.py` — Pydantic schemas for request/response validation

## Getting Started

1. Create and activate the Python virtual environment.

```powershell
cd backend
python -m venv venv
.\\.\venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

2. Configure environment variables in a `.env` file or system environment:

```text
POSTGRES_URL=postgresql://postgres:postgres@localhost:5432/disasterdb
MONGO_URL=mongodb://localhost:27017/
SECRET_KEY=your-secret-key
```

3. Start the API server.

```powershell
uvicorn app.main:app --reload
```

4. Visit the interactive API docs:

```
http://127.0.0.1:8000/docs
```

## API Endpoints

- `GET /` — health check
- `POST /auth/register` — register a new user
- `POST /auth/login` — log in and receive a bearer token
- `POST /projects/` — create a new reconstruction project (authenticated)
- `GET /projects/` — list all projects
- `GET /resources/` — list all hazard/resource reports
- `POST /resources/` — add a new hazard/resource report (authenticated)

## Notes

- Authentication is handled with OAuth2 password bearer tokens and JWTs.
- Projects are stored in PostgreSQL while resource reports are stored in MongoDB.
- This backend is intended to support real-time hazard reporting and reconstruction planning for disaster response scenarios.
