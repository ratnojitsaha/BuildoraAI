# Buildora AI

Buildora AI is a free-to-use full-stack AI website builder. Users can register, describe the website they want to build, generate a React project with AI, preview and edit the generated files, continue refining the project through chat, export the code, and publish a public preview.

## Features

- User registration, login, logout, and authenticated sessions
- AI-generated React website projects from natural language prompts
- Progressive project generation with planned files, generated files, current file status, and failure states
- Chat-based project revisions using AI-generated file operations
- Live project preview powered by Sandpack
- Manual file editing and project export utilities
- Public publishing flow for sharing generated projects

## Tech Stack

**Client**

- React 19
- Vite
- Tailwind CSS
- React Router
- Axios
- Sandpack
- JSZip and FileSaver
- Lucide React icons

**Server**

- Node.js
- Express
- MongoDB with Mongoose
- JWT authentication
- bcrypt password hashing
- OpenRouter via the AI SDK
- Zod schemas for AI output validation

## Project Structure

```text
BuildoraAI/
  client/                 React/Vite frontend
    public/               Static assets
    src/
      api/                Axios API client
      components/         Builder, chat, preview, and UI components
      context/            App-level React context
      pages/              Route pages
      utils/              Export and Sandpack helpers

  server/                 Express backend
    config/               Database connection
    controllers/          Auth, project, and chat handlers
    middleware/           Authentication middleware
    models/               Mongoose models
    routes/               API route definitions
    services/             AI, prompts, validation, and diff utilities
```

## Prerequisites

- Node.js
- npm
- MongoDB database
- OpenRouter API key

## Environment Variables

Create `server/.env`:

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

Create `client/.env`:

```env
VITE_BASE_URL=http://localhost:3000
```

## Getting Started

Install server dependencies:

```bash
cd server
npm install
```

Install client dependencies:

```bash
cd ../client
npm install
```

Start the backend:

```bash
cd server
npm run dev
```

Start the frontend in a second terminal:

```bash
cd client
npm run dev
```

By default, the server runs on `http://localhost:3000` and the Vite client runs on `http://localhost:5173`.

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

## API Overview

### Auth

- `POST /api/auth/register` - create a new user
- `POST /api/auth/login` - log in
- `POST /api/auth/logout` - log out
- `GET /api/auth/me` - get the current authenticated user

### Projects

- `POST /api/projects` - create a new AI-generated project
- `GET /api/projects` - list the authenticated user's projects
- `GET /api/projects/:id` - get a single project
- `DELETE /api/projects/:id` - delete a project
- `PUT /api/projects/:id/files` - update project files manually
- `POST /api/projects/:id/publish` - publish a project
- `GET /api/projects/public/:id` - get a published public project
- `POST /api/projects/:id/chat` - revise a project through chat

## Notes

- Keep real secrets out of Git. Use local `.env` files for API keys, database URLs, and JWT secrets.
- The backend expects `ORIGINS` to be a comma-separated list of allowed frontend origins.
- Generated projects require a valid OpenRouter API key unless you configure another compatible model provider in `server/services/ai.js`.
