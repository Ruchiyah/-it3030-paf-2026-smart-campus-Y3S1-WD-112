<div align="center">
	<img
		src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=26&duration=2500&pause=900&color=1E88E5&center=true&vCenter=true&width=760&lines=Smart+Campus+Operations+Hub;Resources+Bookings+Tickets+Dashboards"
		alt="Smart Campus Operations Hub"
	/>
	<p>Full-stack smart campus system for resource management, bookings, and maintenance tickets.</p>
	<p>
		<img src="https://img.shields.io/badge/Spring%20Boot-3.2.4-6DB33F?logo=springboot&logoColor=white" alt="Spring Boot" />
		<img src="https://img.shields.io/badge/Java-17-007396?logo=openjdk&logoColor=white" alt="Java 17" />
		<img src="https://img.shields.io/badge/MongoDB-Atlas-47A248?logo=mongodb&logoColor=white" alt="MongoDB" />
		<img src="https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=0B1E2D" alt="React" />
		<img src="https://img.shields.io/badge/Vite-8-646CFF?logo=vite&logoColor=white" alt="Vite" />
		<img src="https://img.shields.io/badge/Tailwind-4-38B2AC?logo=tailwindcss&logoColor=white" alt="Tailwind" />
	</p>
	<p>
		<a href="#overview">Overview</a> | <a href="#features">Features</a> | <a href="#quick-start">Quick start</a> | <a href="#configuration">Configuration</a> | <a href="#services-and-ports">Services</a>
	</p>
</div>

## Overview
Smart Campus Operations Hub is a full-stack web system that centralizes campus operations. It combines resource discovery and booking, maintenance ticket workflows, and role-based dashboards for admins, technicians, and users. The backend is a Spring Boot REST API and the frontend is a React (Vite) SPA.

## Features
- Resource catalog with availability checks
- Booking requests and approvals
- Maintenance ticket lifecycle for users and technicians
- Role-based dashboards (admin, technician, user)
- OAuth2 login (Google, GitHub) and JWT-protected API

## Architecture
- `backend/`: Spring Boot REST API, MongoDB, OAuth2, JWT
- `frontend/`: React + Vite SPA with Tailwind CSS
- MongoDB is the primary datastore
- Frontend calls the API at `http://localhost:8081` by default

## Tech stack
**Backend**
- Java 17, Spring Boot 3.2.4
- Spring Security, OAuth2 Client
- MongoDB (Spring Data)
- JWT (jjwt)
- Maven (wrapper included)

**Frontend**
- React 19, Vite 8
- Tailwind CSS
- React Router
- Axios

## Prerequisites
- Git
- Java 17 (JDK)
- Node.js 18+ and npm
- MongoDB (local or Atlas)
- OAuth apps (optional) for Google and GitHub login

## Clone the project
```bash
git clone https://github.com/<your-org>/-it3030-paf-2026-smart-campus-Y3S1-WD-112.git
cd -it3030-paf-2026-smart-campus-Y3S1-WD-112
```

## Quick start
1) Start MongoDB (local service or Atlas)
2) Start the backend API
3) Start the frontend UI

### Backend setup
1. Configure environment variables or update `backend/src/main/resources/application-local.properties` with your own values.
2. Start the API server:

**Windows**
```bash
cd backend
./mvnw.cmd spring-boot:run
```

**macOS/Linux**
```bash
cd backend
./mvnw spring-boot:run
```

The API will run at `http://localhost:8081`.

### Frontend setup
```bash
cd frontend
npm install
npm run dev
```

The UI will run at `http://localhost:5173`.

## Configuration
### Backend environment variables
You can set these environment variables (recommended) or define them in `application-local.properties`:

| Variable | Description | Default |
| --- | --- | --- |
| `MONGODB_URI` | MongoDB connection string | `mongodb://localhost:27017/smartcampus` |
| `GOOGLE_OAUTH_CLIENT_ID` | Google OAuth client ID | none |
| `GOOGLE_OAUTH_CLIENT_SECRET` | Google OAuth client secret | none |
| `GITHUB_OAUTH_CLIENT_ID` | GitHub OAuth client ID | none |
| `GITHUB_OAUTH_CLIENT_SECRET` | GitHub OAuth client secret | none |
| `APP_JWT_SECRET` | JWT signing secret (32+ chars recommended) | none |

Other useful settings (in `backend/src/main/resources/application.properties`):
- `server.port` (default `8081`)
- `app.frontend-url` (default `http://localhost:5173`)
- `app.admin-emails` (comma-separated admin emails)

### OAuth callback URLs
If you enable OAuth login, set these callback URLs in your OAuth apps:
- Google: `http://localhost:8081/login/oauth2/code/google`
- GitHub: `http://localhost:8081/login/oauth2/code/github`

### Frontend API base URL
The API base URL is currently set in `frontend/src/context/AuthContext.jsx` as `http://localhost:8081`. If you run the backend on a different host or port, update that value.

## Services and ports
| Service | Default port | Notes |
| --- | --- | --- |
| Backend API | 8081 | Spring Boot REST API |
| Frontend UI | 5173 | Vite dev server |
| MongoDB | 27017 | Local default |

## Common scripts
**Backend**
- Run tests: `./mvnw test`
- Build: `./mvnw clean package`

**Frontend**
- Build: `npm run build`
- Preview build: `npm run preview`
- Lint: `npm run lint`

## Project structure
```
backend/   # Spring Boot API
frontend/  # React + Vite UI
```

## Notes
- Do not commit real secrets to version control. Use environment variables for OAuth keys and JWT secrets.
- If you change the frontend URL, update `app.frontend-url` to keep CORS and OAuth redirects working.
