# JobHuntly

JobHuntly is a full-stack job platform that connects job seekers and employers with dedicated workflows for discovery, applications, communication, and hiring operations.

## Highlights

- Role-based experience for **job seekers** and **companies**
- Job discovery, company browsing, and detailed job/company pages
- Application lifecycle tracking with status updates and follow-ups
- Real-time messaging with WebSocket/STOMP support
- Notification center and profile management
- Company-side tools for job posting, applicant management, and calendar scheduling
- Help center, reporting, saved jobs, and reading list actions

## Tech Stack

### Frontend
- React 19
- Vite 8
- React Router 7
- ESLint 9

### Backend
- Java 17
- Spring Boot 3.2
- Spring Security (JWT)
- Spring Data JPA (MySQL)
- Spring WebSocket (STOMP + SockJS)

## Repository Structure

```text
Job-Huntly/
├── frontend/   # React + Vite client
└── backend/    # Spring Boot REST + WebSocket API
```

## Prerequisites

- **Node.js** 20+ and npm
- **Java** 17+
- **Maven** 3.9+
- **MySQL** 8+

## Local Setup

### 1) Clone and enter the repository

```bash
git clone <your-fork-or-repo-url>
cd Job-Huntly
```

### 2) Configure backend

The backend default configuration is in:

- `/tmp/workspace/harshakumari21/Job-Huntly/backend/src/main/resources/application.yml`

By default it expects:

- MySQL at `localhost:3310`
- Database: `jobhuntly`
- Username: `root`
- Password: `root`
- Server port: `8080`

Update the datasource and other settings as needed for your environment.

### 3) Run backend

```bash
cd backend
mvn spring-boot:run
```

### 4) Configure frontend

The frontend reads the API base URL from:

- `VITE_API_BASE_URL` (optional)

Default value if omitted:

- `http://localhost:8080/api`

### 5) Run frontend

```bash
cd frontend
npm ci
npm run dev
```

Frontend default dev URL: `http://localhost:5173`

## Scripts

### Frontend (`/frontend`)

- `npm run dev` – start development server
- `npm run build` – production build
- `npm run lint` – lint source files
- `npm run preview` – preview production build

### Backend (`/backend`)

- `mvn spring-boot:run` – start API server
- `mvn test` – run tests

## Key API Areas

The backend exposes endpoints under `/api`, including:

- `auth` – registration, login, token refresh, current user
- `jobs` / `companies` – job and company discovery
- `applications` – application CRUD and status workflow
- `company/applications` – company-side candidate pipeline actions
- `chat` – messaging and unread counters
- `notifications` – notification retrieval and read actions
- `profile` / `network` – profile and user discovery
- `help-center` – knowledge articles and support tickets
- `company/calendar` – scheduling, categories/events, Google Calendar integration
- `job-actions` – save, report, reading list, sharing

## WebSocket

WebSocket endpoint:

- `/ws` (SockJS enabled)

Broker destinations:

- `/app` (application destination prefix)
- `/topic`, `/queue`, `/user` (subscriptions)

## Notes

- The frontend currently contains the default Vite README at `/frontend/README.md`; this root README is the main project reference.
- Ensure backend is running before using authenticated frontend features.
