# Task Manager React Client

This is the front-end application for the Task Manager capstone project. It provides a lightweight task tracking interface where users can create tasks, mark them complete or active, filter by status, and delete items.

The app is built with React and Vite, and it communicates with a backend API exposed through a `VITE_API_URL` environment variable.

## Features

- Add a new task with a title and optional description
- Toggle tasks between active and completed states
- Delete tasks from the list
- Filter tasks by `All`, `Active`, and `Completed`
- Display the number of remaining open tasks
- Handle loading and error states while fetching from the API

## Tech Stack

- React 19
- Vite 8
- React Router DOM
- Vanilla CSS for styling

## Project Structure

```text
task-manager-react/
├── index.html
├── package.json
├── public/
├── src/
│   ├── api/
│   │   └── taskApi.js
│   ├── components/
│   │   ├── TaskFilter.jsx
│   │   ├── TaskForm.jsx
│   │   ├── TaskItem.jsx
│   │   └── TaskList.jsx
│   ├── App.jsx
│   ├── main.jsx
│   ├── style.css
│   └── assets/
└── README.md
```

## How the app works

The main application state lives in `src/App.jsx` and manages:

- the task list
- current filter selection
- loading status
- error messages

The app uses helper functions in `src/api/taskApi.js` to communicate with the backend:

- `getTasks()` fetches all tasks
- `createTask(task)` adds a new task
- `updateTaskStatus(id, completed)` toggles a task state
- `deleteTask(id)` removes a task

## Prerequisites

Before running the app, make sure you have:

- Node.js installed
- a backend API running that exposes the task endpoints

By default, the frontend expects the API at:

```text
http://localhost:5000/api/tasks
```

You can override this in a `.env` or `.env.local` file:

```env
VITE_API_URL=http://localhost:5000/api/tasks
```

## Getting Started

1. Install dependencies:

```bash
npm install
```

2. Start the development server:

```bash
npm run dev
```

3. Open the app in your browser:

```text
http://localhost:5173
```

## Available Scripts

```bash
npm run dev
```
Runs the Vite dev server for local development.

```bash
npm run build
```
Builds the production bundle for deployment.

```bash
npm run preview
```
Serves the production build locally for preview.

## API contract

This client expects the backend to return JSON in a success-response format similar to this:

```json
{
  "success": true,
  "data": [
    {
      "_id": "123",
      "title": "Write project proposal",
      "description": "Draft the first version for review",
      "completed": false
    }
  ]
}
```

API errors are handled by reading `result.message` from failed responses.

## Notes

- The project is intentionally a front-end-only React app and depends on a separate backend service.
- The app uses `BrowserRouter` from `react-router-dom`, but the current UI is a single-page task manager without route-based navigation.
- Styling is contained in `src/style.css`, with responsive layout support for smaller screens.
