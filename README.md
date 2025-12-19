# Docker Compose CI/CD Demo

A complete CI/CD pipeline demonstrating DevOps best practices.

## What it does

- Node.js Express API
- PostgreSQL database
- Dockerized with Docker
- Automated CI/CD pipeline with GitHub Actions
- Auto-push to Docker Hub on every commit

## Endpoints

| Endpoint | Response |
|----------|----------|
| GET / | `{ "message": "Hello from Docker CI/CD!" }` |
| GET /health | `{ "status": "ok" }` |

## Pipeline Flow
```
Push to main
     ↓
GitHub Actions triggers
     ↓
1. Checkout code
2. Build Docker image
3. Start services (app + db)
4. Run health check test
5. Push image to Docker Hub
6. Clean up
```

## Architecture
```
┌─────────────────────────────────────────┐
│              GitHub Actions             │
│                                         │
│  ┌─────────┐    ┌─────────┐            │
│  │  Build  │ →  │  Test   │ → Push     │
│  └─────────┘    └─────────┘            │
└─────────────────────────────────────────┘
                    ↓
            ┌──────────────┐
            │  Docker Hub  │
            └──────────────┘
```

## Run Locally

**Option 1: From Docker Hub**
```bash
docker pull YOUR_USERNAME/docker-compose-ci:latest
docker run -p 3000:3000 YOUR_USERNAME/docker-compose-ci:latest
```

**Option 2: Build locally**
```bash
docker build -t app:test .
docker compose up -d
```

Then visit: http://localhost:3000

## Tech Stack

| Tool | Purpose |
|------|---------|
| Node.js 18 | Runtime |
| Express.js | Web framework |
| PostgreSQL 15 | Database |
| Docker | Containerization |
| Docker Compose | Multi-container orchestration |
| GitHub Actions | CI/CD pipeline |

## Project Structure
```
├── app.js                    # Express API
├── test.js                   # Health check test
├── package.json              # Dependencies
├── Dockerfile                # Image build instructions
├── docker-compose.yml        # Service orchestration
└── .github/workflows/ci.yml  # CI/CD pipeline
```

## DevOps Concepts Demonstrated

- ✅ Containerization with Docker
- ✅ Multi-service orchestration
- ✅ Automated testing in CI
- ✅ Image registry (Docker Hub)
- ✅ Secrets management
- ✅ Infrastructure as Code

## Author

Youssef Laamarti
