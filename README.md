🎬 Movie App

A modern and fast movie search application built with React + Vite, TMDB API, and Appwrite.

<p align="center"> <img src="https://img.shields.io/badge/React-18-blue?logo=react" /> <img src="https://img.shields.io/badge/Vite-Build%20Tool-purple?logo=vite" /> <img src="https://img.shields.io/badge/Appwrite-Backend-red?logo=appwrite" /> <img src="https://img.shields.io/badge/TMDB-API-green?logo=themoviedatabase" /> </p>
✨ Features

🔍 Search movies with live results

🎭 Display posters, ratings, descriptions

📊 Track search frequency via Appwrite

⚡ Super-fast thanks to Vite

🧩 Clean and modular React components

📦 Installation

1. Clone the repository
   git clone https://github.com/Jack210797/movie-app.git
   cd movie-app

2. Install dependencies
   npm install

3. Create .env file

Create a file named .env in the project root:

VITE_TMDB_API_KEY=your_tmdb_api_key
VITE_APPWRITE_PROJECT_ID=your_project_id
VITE_APPWRITE_DATABASE_ID=your_database_id
VITE_APPWRITE_TABLE_ID=your_collection_id

4. Start development server
   npm run dev

5. Build for production
   npm run build

🧰 Appwrite Setup

1. Create a project

Go to Appwrite dashboard → Create a new project.

2. Create a database

Name can be anything.

3. Create a collection with attributes:
   Attribute Type Required
   searchTerm string ✔️
   count integer ✔️
   movie_id string ✔️
   poster_url string ✔️
4. Permissions

Enable:

Create: role:all

Read: role:all

Update: role:all

(or use authenticated users if needed)

5. Appwrite endpoint

Use the region in your Appwrite console, e.g.:

https://fra.cloud.appwrite.io/v1

📁 Project Structure
movie-app/
├── public/
├── src/
│ ├── components/
│ │ ├── Search.jsx
│ │ ├── MovieCard.jsx
│ │ └── Spinner.jsx
│ ├── lib/
│ │ └── appwrite.js
│ ├── App.jsx
│ └── main.jsx
├── .env
├── package.json
└── README.md

⚙️ How It Works
🔹 Search Flow

User types a movie name

Input is debounced (1 second) via useDebounce

App queries TMDB API

Results are rendered as movie cards

📊 Search Analytics Flow

Every time search results return successfully:

Check if searchTerm exists in Appwrite

If exists → count + 1

If not → create a new document with:

searchTerm

count: 1

movie_id

poster_url

🌍 Environment Variables
Variable Description
VITE_TMDB_API_KEY Your TMDB API key
VITE_APPWRITE_PROJECT_ID Appwrite project ID
VITE_APPWRITE_DATABASE_ID Database ID
VITE_APPWRITE_TABLE_ID Collection ID
