# Rick and Morty Explorer — Symfony

A web application built with **Symfony 7** that lets you browse and search characters, episodes, and locations from the Rick and Morty universe using the [Rick and Morty API](https://rickandmortyapi.com/api).

## Tech Stack

- **Backend:** PHP 8.2+, Symfony 7.3, Doctrine ORM
- **Frontend:** Twig, Vue.js 3, Tailwind CSS 3, Stimulus.js, Hotwired Turbo
- **Build Tools:** Webpack Encore, PostCSS
- **Infrastructure:** Docker (PHP-FPM, Nginx, MySQL, Mailpit)

## Features

- Browse all **characters** with images, status, species, gender, origin, and location
- View individual **character profiles** with full episode history
- Browse all **episodes** sorted by air date (newest first)
- View **episode details** with a paginated list of characters that appear in it
- Search characters by **dimension** or **location**
- View **location details** with paginated resident characters
- Pagination support across all list views (20 items per page)

## Routes

| Path | Description |
|------|-------------|
| `/character` | List all characters |
| `/character/{id}` | Character detail page |
| `/episode` | List all episodes |
| `/episode/{id}` | Episode detail page |
| `/location/{id}` | Location detail page |
| `/search/characters/dimension` | Search characters by dimension |
| `/search/characters/location` | Search characters by location |
| `/characters/dimension/{dimension}` | Characters filtered by dimension |
| `/characters/location/{location}` | Characters filtered by location |

## Getting Started

### Prerequisites

- Docker & Docker Compose
- Node.js 18+
- Composer

### Run with Docker

```bash
docker compose -f docker-compose.yml up -d
```

### Install dependencies

```bash
composer install
npm install
```

### Build frontend assets

```bash
npm run dev
```

### Get inside container

```bash
docker exec -it rickandmorty-symfony bash
```

### Clear cache

```bash
php bin/console cache:clear
```

### Access the app

```
http://localhost:8000/search/characters/dimension
```

## Project Structure

```
src/
├── Controller/        # Route handlers (Character, Episode, Location, Search)
├── Service/           # API business logic (Character, Episode, Location, Pagination)
├── Entity/            # Doctrine entities (not used — data fetched from API)
templates/
├── character/         # Character list and detail views
├── episode/           # Episode list and detail views
├── location/          # Location detail and search views
├── components/        # Reusable Twig components (navigation, pagination, search)
assets/
├── controllers/       # Stimulus JS controllers
├── vue/               # Vue.js components
├── styles/            # Tailwind CSS entry
```

## Environment Variables

Copy `.env` and adjust as needed:

```
APP_ENV=dev
DATABASE_URL=postgresql://app:!ChangeMe!@127.0.0.1:5432/app?serverVersion=16&charset=utf8
API_BASE_URL=https://rickandmortyapi.com/api
```

## Notes

- This app is **stateless** — all data is fetched live from the Rick and Morty API with no local persistence.
- No database migrations are needed for core functionality.
