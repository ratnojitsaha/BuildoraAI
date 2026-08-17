# Buildora AI

**Buildora AI** is a full-stack AI-powered web application that transforms natural-language prompts into functional React.js applications. Users can generate projects, preview and edit files in the browser, refine applications through AI-powered chat, export complete source code, and publish projects for public viewing.

### Live Demo

**Frontend:** https://buildoraai.vercel.app

**Source Code:** https://github.com/ratnojitsaha/BuildoraAI

**Developer:** Ratnojit Saha
**LinkedIn:** https://www.linkedin.com/in/saharatnojit/
**GitHub:** https://github.com/ratnojitsaha

---

## Demo Access

You can explore the application using the following demo account:

| Field           | Details              |
| --------------- | -------------------- |
| **Login Email** | `saharatnojit99@gmail.com`    |
| **Password**    | `Mnbv@1234` |

> **Note:** The demo account is provided for evaluation purposes. Please do not modify or delete existing demo projects. Also the AI Model used in this project is free version and have limited Requests per 24 hours.

---

## Overview

Buildora AI provides an interactive environment for generating and working with React applications using natural-language instructions.

Instead of manually creating a project structure and writing every file from scratch, users can describe what they want to build and let the AI generate the required application files.

The generated project can then be:

1. Generated from a natural-language prompt
2. Previewed directly in the browser
3. Inspected through its project structure
4. Edited manually
5. Refined through AI-powered chat
6. Exported as a ZIP archive
7. Published through a public preview link

---

## Key Features

### AI-Powered Project Generation

* Generate functional React.js applications from natural-language prompts
* Uses OpenRouter for AI model access
* Supports configurable AI model selection
* Generates structured project files rather than a single code response
* Validates AI-generated output using Zod schemas

### Interactive Project Builder

* Live application preview using Sandpack
* Project file and folder inspection
* Manual file editing
* Current-file status tracking
* Progressive project generation
* Generation failure-state handling

### AI-Powered Project Revision

* Continue working on generated projects through conversational prompts
* AI generates structured file operations for project modifications
* Supports iterative project refinement without regenerating the entire application

### Authentication & Security

* User registration and login
* JWT-based authentication
* HTTP-only authentication cookies
* Password hashing with bcrypt
* Protected project routes
* Request validation using Zod
* CORS configuration
* Rate limiting for AI-powered API requests

### Project Management

* Create and manage multiple projects
* View individual projects
* Update project files
* Delete projects
* Publish projects for public viewing

### Export & Publishing

* Export generated projects as downloadable ZIP archives
* File packaging using JSZip
* Browser downloads using FileSaver
* Publish projects through public preview URLs

---

## Tech Stack

### Frontend

* **React 19**
* **Vite**
* **Tailwind CSS**
* **React Router**
* **Axios**
* **Sandpack**
* **JSZip**
* **FileSaver**
* **Lucide React**

### Backend

* **Node.js**
* **Express.js**
* **MongoDB**
* **Mongoose**
* **JWT**
* **bcrypt**
* **Zod**
* **Express Rate Limit**

### AI

* **OpenRouter**
* **AI SDK**
* **Cohere's North Mini Code model**
* Structured AI output validation with **Zod**

### Deployment

* **Frontend:** Vercel
* **Backend:** Configure according to your deployed backend provider
* **Database:** MongoDB

---

## Application Architecture

```text
User
 │
 ▼
React / Vite Frontend
 │
 │ Axios
 ▼
Express.js API
 │
 ├── Authentication Middleware
 │
 ├── Rate Limiting
 │
 ├── Request Validation
 │
 ├── Project Controllers
 │
 └── Chat Controller
 │
 ├───────────────┐
 ▼               ▼
MongoDB       AI Service
                  │
                  ▼
              OpenRouter
                  │
                  ▼
              AI Model
```

---

## Project Structure

```text
BuildoraAI/
│
├── client/
│   ├── public/
│   └── src/
│       ├── api/                # Axios API client
│       ├── components/         # Builder, chat, preview & UI
│       ├── context/            # Application state/context
│       ├── pages/              # Application pages
│       └── utils/              # Export & Sandpack utilities
│
├── server/
│   ├── config/                 # Database configuration
│   ├── controllers/            # Request handlers
│   ├── middleware/             # Authentication & rate limiting
│   ├── models/                 # Mongoose models
│   ├── routes/                 # API routes
│   ├── services/               # AI, prompts, validation & diff logic
│   └── server.js               # Express application entry point
│
└── README.md
```

---

## API Overview

### Authentication

| Method | Endpoint             | Description                     |
| ------ | -------------------- | ------------------------------- |
| POST   | `/api/auth/register` | Register a new user             |
| POST   | `/api/auth/login`    | Authenticate a user             |
| POST   | `/api/auth/logout`   | Log out the current user        |
| GET    | `/api/auth/me`       | Retrieve the authenticated user |

### Projects

| Method | Endpoint                    | Description                    |
| ------ | --------------------------- | ------------------------------ |
| POST   | `/api/projects`             | Create an AI-generated project |
| GET    | `/api/projects`             | List the user's projects       |
| GET    | `/api/projects/:id`         | Retrieve a project             |
| DELETE | `/api/projects/:id`         | Delete a project               |
| PUT    | `/api/projects/:id/files`   | Update project files           |
| POST   | `/api/projects/:id/publish` | Publish a project              |
| GET    | `/api/projects/public/:id`  | Retrieve a public project      |
| POST   | `/api/projects/:id/chat`    | Refine a project using AI chat |

---

## Getting Started

### Prerequisites

Make sure you have the following installed:

* Node.js
* npm
* MongoDB
* OpenRouter API key

### 1. Clone the repository

```bash
git clone https://github.com/ratnojitsaha/BuildoraAI.git
cd BuildoraAI
```

### 2. Install backend dependencies

```bash
cd server
npm install
```

### 3. Install frontend dependencies

```bash
cd ../client
npm install
```

---

## Environment Configuration

### Backend

Create:

```text
server/.env
```

```env
PORT=3000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
ORIGINS=http://localhost:5173
OPENROUTER_API_KEY=your_openrouter_api_key
OPENROUTER_MODEL=openrouter/free
AI_MAX_CONCURRENCY=6
NODE_ENV=development
```

### Frontend

Create:

```text
client/.env
```

```env
VITE_BASE_URL=http://localhost:3000
```

> Never commit `.env` files or expose API keys, database credentials, or JWT secrets in source control.

---

## Running Locally

### Start the backend

```bash
cd server
npm run dev
```

The backend will run on:

```text
http://localhost:3000
```

### Start the frontend

Open a second terminal:

```bash
cd client
npm run dev
```

The frontend will run on:

```text
http://localhost:5173
```

---

## Available Scripts

### Server

```bash
npm run dev
npm start
```

### Client

```bash
npm run dev
npm run build
npm run lint
npm run preview
```

---

## Security Considerations

Buildora AI includes several backend security measures:

* JWT-based authentication
* HTTP-only authentication cookies
* bcrypt password hashing
* Protected API routes
* Zod-based request validation
* CORS origin restrictions
* Rate limiting on AI-powered endpoints
* Environment-based secret management

The AI chat endpoint uses request rate limiting to reduce excessive and abusive requests before they reach the AI service.

---

## Deployment

The frontend is deployed on **Vercel**.

### Production deployment checklist

Before deploying:

* Configure production environment variables
* Set the production frontend origin in `ORIGINS`
* Use a strong `JWT_SECRET`
* Keep API keys server-side
* Configure the production MongoDB connection
* Set `NODE_ENV=production`
* Configure the deployed backend URL in `VITE_BASE_URL`
* Verify CORS configuration
* Verify authentication cookies in the production environment
* Test AI generation and chat rate limiting

---

## Important Notes

* A valid OpenRouter API key is required for AI-powered generation and chat.
* Generated applications are React-based projects.
* `ORIGINS` supports multiple comma-separated frontend origins.
* Keep all credentials and secrets inside environment variables.
* Do not commit `.env` files to the repository.
* The demo account should only contain non-sensitive demonstration data.

---

## Future Improvements

Potential improvements include:

* Persistent distributed rate limiting
* Usage and token tracking
* Project version history
* Background generation jobs
* Additional AI model providers
* Team collaboration
* Project sharing permissions
* Custom deployment of generated applications
* Improved project-level resource limits

---

## Author

**Ratnojit Saha**

* **GitHub:** https://github.com/ratnojitsaha
* **LinkedIn:** https://www.linkedin.com/in/saharatnojit/

---

## License

This project is intended for educational and portfolio purposes.
