# CS Department Website

A professional static website for the Computer Science Department, built and deployed using a complete DevOps workflow.

## Live Environments

| Environment | Branch | URL |
|-------------|--------|-----|
| Production | `main` | https://cs-dept-production.onrender.com |
| Staging/QA | `release` | https://cs-dept-staging.onrender.com |
| Development | `develop` | https://cs-dept-development.onrender.com |

## Pages

| Page | File | Developer |
|------|------|-----------|
| Home | index.html | Ahmed Qureshi |
| Courses | courses.html | Ahmed Qureshi |
| Faculty | faculty.html | Ahmed Qureshi |
| Admissions | admissions.html | Ahmed Qureshi |
| Contact | contact.html | Ahmed Qureshi |

## Tech Stack

- **Frontend:** HTML5, CSS3
- **Web Server:** Nginx (Alpine)
- **Containerization:** Docker
- **CI/CD:** GitHub Actions
- **Hosting:** Render.com
- **Version Control:** Git Flow

## Branch Strategy

| Branch | Purpose | Auto Deploy |
|--------|---------|-------------|
| `develop` | Development environment | Yes |
| `release` | Staging/QA environment | Yes |
| `main` | Production environment | Yes |

## CI Pipeline (per environment)

1. Lint HTML with HTMLHint
2. Lint CSS with Stylelint
3. Build Docker image

## CD Pipeline (per environment)

Triggers automatically after CI passes. Calls Render deploy hook via API.

## Local Development

### Run with Docker
```bash
docker build -t cs-department-website .
docker run -p 8080:80 cs-department-website
```
Visit http://localhost:8080

## Project Structure
cs-department-website/
├── src/
│   ├── css/
│   │   └── style.css
│   ├── index.html
│   ├── courses.html
│   ├── faculty.html
│   ├── admissions.html
│   └── contact.html
├── .github/
│   └── workflows/
│       ├── ci-development.yml
│       ├── ci-staging.yml
│       ├── ci-production.yml
│       ├── cd-development.yml
│       ├── cd-staging.yml
│       └── cd-production.yml
├── Dockerfile
├── nginx.conf
└── README.md


## GitHub Environments

Three environments configured with protected secrets:
- `development` — RENDER_API_KEY, RENDER_SERVICE_ID
- `staging` — RENDER_API_KEY, RENDER_SERVICE_ID
- `production` — RENDER_API_KEY, RENDER_SERVICE_ID