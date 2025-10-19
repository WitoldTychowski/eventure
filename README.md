# Eventure

A mobile-first web application for discovering local and free events in your city. Browse a paginated and infinite-scroll list or explore events on an interactive map, filter by type and price, view full details, and enjoy automatic geolocation with manual fallback.

## Table of Contents

- [Eventure](#eventure)
  - [Table of Contents](#table-of-contents)
  - [Tech Stack](#tech-stack)
  - [Getting Started Locally](#getting-started-locally)
    - [Prerequisites](#prerequisites)
    - [Setup](#setup)
  - [Available Scripts](#available-scripts)
  - [Project Scope](#project-scope)
    - [In Scope (MVP)](#in-scope-mvp)
    - [Out of Scope (MVP)](#out-of-scope-mvp)
  - [Project Status](#project-status)
  - [License](#license)

## Tech Stack

- **Frontend**  
  - Astro 5  
  - React 19  
  - TypeScript 5  
  - Tailwind 4  
  - Shadcn/ui  
- **Backend**  
  - Supabase (PostgreSQL, SDK, built-in auth)  
- **CI/CD & Hosting**  
  - GitHub Actions  
  - Docker on DigitalOcean  

## Getting Started Locally

### Prerequisites

- Node.js v22.14.0 (use [nvm](https://github.com/nvm-sh/nvm): `nvm install && nvm use`)  
- npm or yarn  
- A Supabase project with `SUPABASE_URL` and `SUPABASE_KEY`  
- An OpenRouter API key (`OPENROUTER_API_KEY`)  

### Setup

```bash
# Clone the repo
git clone https://github.com/WitoldTychowski/eventure.git
cd eventure

# Use correct Node version
nvm install
nvm use

# Install dependencies
npm install

# Create a .env file in the project root:
# SUPABASE_URL=your_supabase_url
# SUPABASE_KEY=your_supabase_key
# OPENROUTER_API_KEY=your_openrouter_api_key

# Start development server
npm run dev
```

The app will be available at `http://localhost:3000` by default.

## Available Scripts

- `npm run dev` – Start Astro dev server  
- `npm run build` – Build for production  
- `npm run preview` – Preview production build  
- `npm run astro` – Run Astro CLI  
- `npm run lint` – Run ESLint  
- `npm run lint:fix` – Fix lint errors  
- `npm run format` – Run Prettier  

## Project Scope

### In Scope (MVP)

- Infinite-scroll list of events (20 per load)  
- Map view with event markers (latitude, longitude, address)  
- Filters by event type (culture, sport, education, entertainment) and price (free vs paid)  
- Event details: name, rich HTML description with images, address, GPS coordinates, source link  
- Automatic geolocation with manual fallback (text input or city dropdown)  
- Error handling  
  - Empty-state UI with filter suggestions  
  - API error banner with “Refresh” button  

### Out of Scope (MVP)

- Reservations or ticket purchases  
- User accounts, registration, or login  
- Push notifications  
- Payment processing  

## Project Status

Currently in **MVP development**.

## License

This project is released under the [MIT License](LICENSE)  
