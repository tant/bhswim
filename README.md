# BHSWIM Monorepo

This repository contains the source code for the BHSWIM project, organized as a monorepo using Turbo and PNPM workspaces.

## Structure

- `apps/`
  - `backend/`: Medusa backend service
  - `frontend/`: Astro frontend application
- `docs/`: Project documentation
- `supabase-docker/`: Supabase local development setup (Docker)

## Getting Started

### Prerequisites
- Node.js (v18+ recommended)
- PNPM (https://pnpm.io/)
- Docker (for Supabase)

### Install Dependencies
```sh
pnpm install
```

### Development
Start both frontend and backend servers:
```sh
pnpm turbo dev
```
- Frontend: http://localhost:4321/
- Backend: http://localhost:9000/app

### Supabase Local
To start Supabase locally:
```sh
cd supabase-docker
# For standard setup
docker-compose up
# For S3 support
docker-compose -f docker-compose.s3.yml up
```

## Project Scripts
- Backend seed: `pnpm --filter apps/backend run seed`

## Documentation
See the `docs/` folder for more details.

## Contributing
Pull requests and issues are welcome!

## License
See individual folders for license information.
