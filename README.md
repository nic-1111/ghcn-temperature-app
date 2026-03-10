# Installation Guide

This project consists of a backend (API) and a frontend. Both are executed with Docker.

## Prerequisites
- Docker must be installed. If not, download it from [docker.com](https://www.docker.com/) and install it.
- Node.js and npm must be installed (required for the frontend build).

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

### Step 1: Build Frontend
The frontend **must** be built before Docker is started, so that the current changes and assets are available correctly.

```bash
cd ../ghcn-temperature-frontend/frontend
npm install
npm run build
```

### Step 2: Back to Main Folder
```bash
cd ../../ghcn-temperature-app
```

### Step 3: Start Docker Services
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
- **Order is important**: Frontend must be built before Docker is started so that the current build artifacts are available.
- The first start may take a while as the images are being built.
- Make sure ports 8000 and 8080 are free.
- When making changes to the frontend: Run `npm run build` again before restarting Docker.