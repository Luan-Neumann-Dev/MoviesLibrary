# 🎬 Movies Library
 
> Movie catalog built with React 18 + React Router — browse top-rated films, search by title, and view details like budget, revenue and runtime, all powered by the TMDB API.
 
[![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev/)
[![React Router](https://img.shields.io/badge/React_Router-6-CA4245?style=for-the-badge&logo=react-router&logoColor=white)](https://reactrouter.com/)
[![Vite](https://img.shields.io/badge/Vite-5-646CFF?style=for-the-badge&logo=vite&logoColor=white)](https://vitejs.dev/)
[![TMDB](https://img.shields.io/badge/TMDB-API-01B4E4?style=for-the-badge&logo=themoviedatabase&logoColor=white)](https://www.themoviedb.org/)
 
![Preview 1](https://github.com/user-attachments/assets/0266d5d9-403b-4355-94c7-beb8701c4978)
![Preview 2](https://github.com/user-attachments/assets/0e635f97-3dd8-4dc3-ac9a-b3c65084faf7)
![Preview 3](https://github.com/user-attachments/assets/a4963c0b-45e4-4518-9990-c2304c5ee355)
 
**[🚀 View Live Demo](https://movies-library-smoky-nine.vercel.app/)**
 
---

## 🎯 About
 
Movies Library is a React SPA that consumes the TMDB API to display a curated movie catalog. On the home page, users see the top-rated films fetched directly from the API. From there, they can search for any title using the navbar and navigate to a dedicated detail page showing financial and editorial information about each film.
 
The project covers real-world frontend patterns: async data fetching with `useEffect`, client-side routing with React Router, URL-based search params, and environment variables for API key management.
 
## ✨ Key Features
 
- 🏆 **Top-rated movies** — Home page fetches and displays the highest-rated films from TMDB
- 🔍 **Movie search** — Search any title via the navbar, with results updating reactively via URL query params
- 🎬 **Movie detail page** — Dedicated route showing poster, tagline, rating, budget, revenue, runtime, and description
- 🃏 **Reusable MovieCard** — Single component used across home, search, and detail pages via a `showLink` prop
- 🔑 **Environment variables** — API key and endpoints managed via `.env` with Vite's `import.meta.env`
 
## 🛠️ Tech Stack

**Frontend:**
- React 18 — UI and state management via hooks (`useState`, `useEffect`)
- React Router 6 — Client-side routing with `Outlet`, `useParams`, and `useSearchParams`
- React Icons — Icon library for UI elements
- CSS — Plain CSS with per-component files
 
**External API:**
- TMDB API — Movie data, images, search, and financial details
 
**Tools:**
- Vite — Dev server and build tool
- ESLint — Code linting
 
## 🚀 Quick Start
 
### Prerequisites
 
- Node.js 18+
- npm
- A free [TMDB API key](https://www.themoviedb.org/settings/api)
 
### Installation

```bash
# Clone the repository
git clone https://github.com/Luan-Neumann-Dev/movies-library.git
 
# Navigate to the project directory
cd movies-library
 
# Install dependencies
npm install
 
# Set up environment variables
cp .env.example .env
# Then add your TMDB API key to .env
 
# Start the dev server
npm run dev
```

Then open your browser at `http://localhost:5173`.
 
Or check the **[live demo →](https://movies-library-smoky-nine.vercel.app/)**
 
## 📁 Project Structure
 
```
src/
├── components/
│   ├── Navbar.jsx        # Search bar and navigation
│   └── MovieCard.jsx     # Reusable card component (home, search, detail)
├── pages/
│   ├── Home.jsx          # Top-rated movies grid
│   ├── Search.jsx        # Search results via URL query params
│   └── Movie.jsx         # Individual movie detail page
├── App.jsx               # Root layout with Navbar and Outlet
└── main.jsx              # Entry point with router setup
```
 
## 💡 Technical Highlights
 
### URL-based search with `useSearchParams`
Search queries are stored in the URL, making results shareable and browser-history friendly.
 
```jsx
const [searchParams] = useSearchParams()
const query = searchParams.get("q")
 
useEffect(() => {
  const url = `${searchURL}?${apiKey}&query=${query}`
  getSearchMovies(url)
}, [query])
```
 
### Reusable `MovieCard` with conditional rendering
The same card component is used across three different pages. A `showLink` prop controls whether the detail link is rendered, avoiding duplication.
 
```jsx
const MovieCard = ({ movie, showLink = true }) => (
  <div className='movie-card'>
    <img src={imageUrl + movie.poster_path} alt={movie.title} />
    <h2>{movie.title}</h2>
    <p><FaStar /> {movie.vote_average}</p>
    {showLink && <Link to={`/movie/${movie.id}`}>Detalhes</Link>}
  </div>
)
```
 
## 📚 What I Learned
 
**Technical Skills:**
- Consuming a REST API asynchronously with `fetch` and `useEffect`
- Client-side routing with React Router 6 (`Outlet`, `useParams`, `useSearchParams`)
- Managing API keys securely with Vite environment variables
 
**Best Practices:**
- Designing reusable components with configurable props
- Keeping data-fetching logic close to the component that owns the state
- Structuring a multi-page SPA with a shared layout component
 
## 🗺️ Roadmap
 
- [ ] Add favorites list with localStorage persistence
- [ ] Pagination for home and search results
- [ ] Genre filter on the home page
- [ ] Loading skeleton instead of plain text
- [ ] Migrate to TypeScript
 
## 📝 Notes
 
- A valid TMDB API key is required to run the project locally
- This project is not affiliated with TMDB in any way
 
## 📄 License
 
MIT License - see [LICENSE](LICENSE) for details.
 
## 👤 Author
 
**Luan Neumann**
 
[![LinkedIn](https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/luan-neumann-dev/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Luan-Neumann-Dev)
 
---
 
⭐ Found this helpful? Give it a star!
