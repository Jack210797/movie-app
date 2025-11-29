# 🎬 Movie App

A modern and fast movie search application built with React + Vite, TMDB API, and Appwrite.

<p align="center"> <img src="https://img.shields.io/badge/React-18-blue?logo=react" /> <img src="https://img.shields.io/badge/Vite-Build%20Tool-purple?logo=vite" /> <img src="https://img.shields.io/badge/Appwrite-Backend-red?logo=appwrite" /> <img src="https://img.shields.io/badge/TMDB-API-green?logo=themoviedatabase" /> </p>

---

# ✨ Features

- 🔍 Search movies with live results
- 🎭 Display posters, ratings, descriptions
- 📊 Track search frequency via Appwrite
- ⚡ Super-fast thanks to Vite
- 🧩 Clean and modular React components

---

# 📦 Installation

1. Clone the repository

```
git clone https://github.com/Jack210797/movie-app.git
cd movie-app
```

2. Install dependencies

```
npm install
```

3. Create <kbd>.env</kbd> file

Create a file named <kbd>.env</kbd> in the project root:

```
VITE_TMDB_API_KEY=your_tmdb_api_key
VITE_APPWRITE_PROJECT_ID=your_project_id
VITE_APPWRITE_DATABASE_ID=your_database_id
VITE_APPWRITE_TABLE_ID=your_collection_id
```

4. Start development server

```
npm run dev
```

5. Build for production

```
npm run build
```

---

# 🧰 Appwrite Setup

1. Create a project

Go to the Appwrite dashboard and create a new project.

2. Create a database

You can name it however you like.

3. Create a collection with the following attributes:

| Attribute  | Type    | Required |
| ---------- | ------- | -------- |
| searchTerm | string  | ✔️       |
| count      | integer | ✔️       |
| movie_id   | string  | ✔️       |
| poster_url | string  | ✔️       |

4. Permissions

Enable:

- Create → <kbd>role:all</kbd>
- Read → <kbd>role:all</kbd>
- Update → <kbd>role:all</kbd>
  (or set up authentication if needed)

5. Appwrite endpoint

Use the region from your Appwrite project, for example:

```
https://fra.cloud.appwrite.io/v1
```

---

# 📁 Project Structure

```
movie-app/
  ├── public/
  ├── src/
  │   ├── components/
  │   │    ├── Search.jsx
  │   │    ├── MovieCard.jsx
  │   │    └── Spinner.jsx
  │   ├── lib/
  │   │    └── appwrite.js
  │   ├── App.jsx
  │   └── main.jsx
  ├── .env
  ├── package.json
  └── README.md
```

# How It Works

## 🔹 Search Flow

1. User enters a movie title
2. Input is debounced for 1 second using useDebounce
3. A request is sent to TMDB API
4. Movies are rendered as cards

## 📊 Search Analytics Flow (Appwrite)

After successfully fetching movie results:

- The app checks whether <kbd>searchTerm</kbd> exists in the Appwrite database
- If it exists → the <kbd>count</kbd> is increased
- If it does not exist → a new document is created with:
  - <kbd>searchTerm</kbd>
  - <kbd>count: 1 </kbd>
  - <kbd>movie_id </kbd>
  - <kbd>poster_url</kbd>

# 🌍 Environment Variables

| Variable                  | Description         |
| ------------------------- | ------------------- |
| VITE_TMDB_API_KEY         | TMDB API key        |
| VITE_APPWRITE_PROJECT_ID  | Appwrite project ID |
| VITE_APPWRITE_DATABASE_ID | Database ID         |
| VITE_APPWRITE_TABLE_ID    | Collection ID       |
