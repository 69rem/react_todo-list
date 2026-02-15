# React Todo List

My first React project — a simple and interactive Todo List application. It allows you to add, delete, toggle completion of tasks, search through tasks, and view task details. The app uses `localStorage` to persist data (when built with `VITE_STATIC_BACKEND=true`), so your tasks stay even after page reload.

**Live Demo**: [https://69rem.github.io/react_todo-list/](https://69rem.github.io/react_todo-list/)

## Features

- Add new tasks
- Mark tasks as completed / uncompleted
- Delete individual tasks or all tasks at once
- Search tasks by title (case‑insensitive)
- Click on a task to see its details page
- Smooth animations when tasks appear/disappear
- Data persistence via `localStorage` (no backend required)
- Fully responsive design

## Built With

- **React 19** – UI library
- **Vite** – fast build tool and development server
- **CSS Modules** – scoped styling
- **GitHub Pages** – hosting

## Getting Started

### Prerequisites

- Node.js (version 18 or higher)
- npm or yarn

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/69rem/react_todo-list.git
   cd react_todo-list
   ```

2. Install dependencies:
   ```bash
   npm install
   # or
   yarn
   ```

3. Create a `.env` file in the root (optional, for development):
   ```
   VITE_STATIC_BACKEND=false
   ```
   By default, in development the app tries to connect to a local backend (if you set `true`, it uses `localStorage`). For production you'll set it to `true` (see Deployment).

4. Start the development server:
   ```bash
   npm run dev
   ```
   Open [http://localhost:5173](http://localhost:5173) to view it in the browser.

## Building for Production

To create a production build:

```bash
npm run build
```

The output will be in the `dist` folder. The build automatically copies `index.html` to `404.html` to enable client‑side routing on GitHub Pages (see the `build` script in `package.json`).

### Environment Variables for Production

Create a `.env.production` file in the project root with:

```
VITE_STATIC_BACKEND=true
```

This tells the app to use `localStorage` instead of trying to fetch data from a remote server.

## Deployment to GitHub Pages

The project is configured to be easily deployed to GitHub Pages. The `base` in `vite.config.js` is set to `'/react_todo-list/'` for production.

1. Build the project (make sure `.env.production` exists):
   ```bash
   npm run build
   ```

2. Deploy using the `gh-pages` package:
   ```bash
   npx gh-pages -d dist
   ```
   This pushes the contents of the `dist` folder to the `gh-pages` branch.

3. In your repository settings, ensure GitHub Pages is enabled and uses the `gh-pages` branch as the source.

After a few minutes, your app will be live at `https://69rem.github.io/react_todo-list/`.

## Project Structure

```
react_todo-list/
├── public/               # static assets
├── src/
│   ├── assets/           # images, icons
│   ├── components/       # reusable UI components
│   ├── pages/            # page components (Main, TaskDetail, NotFound)
│   ├── shared/           # constants, API, utilities
│   ├── App.jsx           # main app component with routing
│   └── main.jsx          # entry point
├── .env.production       # production environment variables
├── .gitignore
├── index.html
├── package.json
├── vite.config.js        # Vite configuration (base: '/react_todo-list/')
└── README.md
```

## How It Works

- **Routing**: A custom lightweight router (see `shared/router/Router.jsx`) handles navigation without page reloads. It supports dynamic routes like `/tasks/:id`.
- **State Management**: The app uses React hooks (`useState`, `useReducer`, `useContext`) to manage tasks, search query, and UI state.
- **Data Layer**: An API module (`tasksAPI`) switches between a real backend and `localStorage` based on `VITE_STATIC_BACKEND`. In production with `true`, all operations are performed on `localStorage`.
- **Styling**: CSS Modules keep styles component‑scoped and maintainable.

## Author

- GitHub: [@69rem](https://github.com/69rem)

## License

This project is open source and available under the [MIT License](LICENSE).