# Installation Guide

This project consists of a backend (API) and a frontend. Both are executed with Docker.

## Prerequisites
- Docker must be installed. If not, download it from [docker.com](https://www.docker.com/) and install it.

## Project Structure

```
ghcn-temperature-api/         # Backend API (FastAPI/Starlette)
├── app/
│   ├── api/                  # API routes and schemas
│   ├── data/                 # Data fetching and caching
│   ├── logic/                # Business logic (calculations, search)
│   └── test/                 # Tests (pytest + Postman)
│
ghcn-temperature-frontend/    # Frontend (Angular)
├── frontend/
│   ├── src/                  # Angular components, services
│   ├── ui_tests/             # UI tests (Selenium/pytest)
│   └── public/               # Static assets
│
ghcn-temperature-app/         # Docker composition layer
└── docker-compose.yml        # Orchestrates API + Frontend
```

## Installation and Start

### Start Docker Services
```bash
docker-compose up --build
```

This builds the Docker images and starts the services:
- **API**: http://localhost:8000
- **Frontend**: http://localhost:8080

## Stop
Press `Ctrl+C` in the terminal to stop the services.

## Testing

### Backend Tests
```bash
# From ghcn-temperature-api/
pytest app/test/pytest/        # Run all pytest tests
```

### Frontend UI Tests
```bash
# From ghcn-temperature-frontend/frontend/
pytest ui_tests/               # Run all UI tests
```

## Notes
- The first start may take a while as the images are being built.
- Make sure ports 8000 and 8080 are free.