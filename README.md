# Files Manager

## Overview

A file hosting REST API built with **Node.js and Express**. Users authenticate with a token, upload files or images, manage their visibility, and download them. Data is persisted in **MongoDB**, sessions and temporary data are cached in **Redis**, and image thumbnails are generated asynchronously by a **background worker** (Bull queue).

This project is the back-end trimester capstone of the Holberton School curriculum: it brings together authentication, NoSQL storage, caching, pagination and background processing in a single service.

## Features

- Token-based authentication (sign-in / sign-out, hashed passwords)
- File and image upload with public/private visibility control
- File listing with pagination, and per-file publish/unpublish
- File content download with MIME-type detection
- Asynchronous thumbnail generation for images (Bull + Redis queue)
- Service health and statistics endpoints

## Technologies

| Layer | Stack |
|---|---|
| Runtime / framework | Node.js, Express, Babel (ES modules) |
| Database | MongoDB |
| Cache / queue | Redis, Bull |
| Images | image-thumbnail, mime-types |
| Tests & quality | Mocha, Chai, Sinon, ESLint (Airbnb config) |

## Installation

```bash
git clone https://github.com/Abbassimedayoub/holbertonschool-files_manager.git
cd holbertonschool-files_manager
npm install
```

MongoDB and Redis must be running locally (default ports).

## Usage

```bash
# Start the API server
npm run start-server

# Start the thumbnail worker (separate terminal)
npm run start-worker
```

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/status` | Redis and MongoDB health check |
| GET | `/stats` | Number of users and files |
| POST | `/users` | Create a new user |
| GET | `/connect` | Sign in (returns an auth token) |
| GET | `/disconnect` | Sign out |
| GET | `/users/me` | Current user profile |
| POST | `/files` | Upload a file |
| GET | `/files/:id` | Get a file's metadata |
| GET | `/files` | List files (paginated) |
| PUT | `/files/:id/publish` | Make a file public |
| PUT | `/files/:id/unpublish` | Make a file private |
| GET | `/files/:id/data` | Download file content |

## Tests

```bash
npm test        # Mocha/Chai test suite
npm run lint    # ESLint (Airbnb style)
```

## Skills Demonstrated

Back-end API design with Express, NoSQL data modeling (MongoDB), caching and session management with Redis, asynchronous background processing (Bull), token-based authentication, and automated testing.

## Author

**Mohamed Ayoub Abbassi** — Holberton School Paris

- GitHub: [@Abbassimedayoub](https://github.com/Abbassimedayoub)
- LinkedIn: [mohamed-ayoub-abbassi](https://www.linkedin.com/in/mohamed-ayoub-abbassi)
