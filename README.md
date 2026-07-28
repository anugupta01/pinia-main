# 📮 Pinia Posts App

A small, single-page **Posts Hub** built with Vue 3, Pinia, and Vue Router. It lets you browse a live feed of posts, open any post to read it in full alongside its author and comment count, and navigate through a themed Welcome and About Us experience. Post data is fetched from the free [JSONPlaceholder](https://jsonplaceholder.typicode.com) mock API.
 
The app is organized around four pages, each sharing a consistent dark-gradient, glass-card visual theme:

- **Welcome page (`/`)** — a landing page introducing Posts Hub, with **Home** and **About Us** buttons that route to the posts list and the About page.
- **Posts list / Home (`/home`)** — fetches all posts on mount and renders them as a responsive grid of cards. Each card links to that post's detail page.
- **Single post (`/posts/:id`)** — fetches one post by its route `id`, then loads that post's author and its comments, showing the title, body, author, and a comment count.
- **About Us (`/about`)** — describes the application, shows author cards with LinkedIn / email / Facebook links, and lists contact email and phone.

Every page except Welcome has a **back button in the top-left corner** that returns you to the previous step (the posts list or the Welcome page).

State — the list of posts, the currently open post, and the create-post form — is managed centrally in a **Pinia store**, so any component can read or update it without prop drilling.

---

## Tech stack

| Layer | Technology |
|---|---|
| Framework | Vue 3 (Composition API, `<script setup>`) |
| State management | Pinia 3 |
| Routing | Vue Router 5 |
| Build tool | Vite 8 |
| Styling | Scoped CSS (no external UI library required) |
| Data source | JSONPlaceholder REST API |

---

### The Pinia store (`stores/post.js`)

The store holds `posts`, the active `post` (with its `data`, `user`, and `comments`), and a `form` for creating posts. Its actions are:

- **`getPosts()`** — fetches the full list of posts.
- **`getSinglePost(id)`** — fetches one post, then its author and comments.
- **`createPost()`** — submits the form to the API.

---

## Getting started

### Prerequisites

- **Node.js** 18 or newer (Vite 8 requires a modern Node version)
- **npm** (bundled with Node)

### 1. Install dependencies

```bash
npm install
```

### 2. Start the development server

```bash
npm run dev
```

This launches Vite's dev server with hot-module reloading. By default it prints a local URL (typically `http://localhost:5173`) in the terminal — open it in your browser.

#### Running on port 3000

If you want the dev server on `http://localhost:3000`, either run:

```bash
npm run dev -- --port 3000
```

or set it permanently in `vite.config.js`:

```js
export default defineConfig({
  plugins: [vue()],
  server: { port: 3000 },
  preview: { port: 3000 },
});
```

### 3. Build for production

```bash
npm run build
```

This type-checks and bundles the app into a `dist/` folder, optimized and minified for deployment.

### 4. Preview the production build

```bash
npm run preview
```

Serves the built `dist/` folder locally so you can verify the production output before deploying.

---

## Notes

- **JSONPlaceholder is a mock API.** It returns realistic fake data and simulates writes (e.g. `createPost`), but it does not actually persist changes — a newly "created" post won't appear on later fetches. This is expected behavior of the API, not the app.
- **Post titles** come back lowercase from the API; the UI capitalizes them via CSS for display.
- No API keys or environment variables are required — the app talks to a public endpoint out of the box.

---

## Possible next steps
- Add loading and empty states while data is being fetched.
- Render the actual list of comments on the single-post page (currently only the count is shown).
- Wire up the create-post form to the store's `createPost()` action with a success message.