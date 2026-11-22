# Yatri Sathi

**Yatri Sathi** (यात्री साथी, "traveller's companion") is a responsive web app that connects travellers with **verified local cultural hosts** and **licensed trekking guides** in Nepal.

It is a final-year project for module 6CS007 (University of Wolverhampton / Herald College Kathmandu).

## What it does

- **Festival-led discovery:** browse a festival calendar (Dashain, Tihar, Holi, Indra Jatra, …) and find cultural experiences and treks linked to each festival.
- **Layered trust:** hosts and guides go through identity and licence verification. Travellers leave reviews after completed bookings and can chat with a host before booking.
- **Availability-based booking:** pick an open slot, pay with **eSewa**, and the funds are held until the experience is completed.
- **My Memories:** travellers keep a private or public journal of their trips.
- **Admin tools:** verification review, disputes, reports and payout records.

The four user roles are `traveller`, `host` (cultural host), `guide` (trekking guide) and `admin`.

## Tech stack

| Layer | Technology |
| --- | --- |
| Frontend (`client/`) | React, Vite, React Router, Tailwind CSS, FullCalendar, React-Leaflet + OpenStreetMap, Socket.IO client, Axios |
| Backend (`server/`) | Node.js, Express, Mongoose, JWT (HTTP-only cookies), bcrypt, express-validator, Socket.IO, Multer |
| Database | MongoDB Atlas |
| File storage | Amazon S3 (public bucket for photos, private encrypted bucket for ID documents) |
| Payments | eSewa ePay v2 (test environment) |
| Testing | Jest, Supertest, React Testing Library, Cypress |

## Project structure

```
yatri-sathi/
├── client/   # React + Vite frontend
└── server/   # Express REST API + Socket.IO
```

## Getting started

### Prerequisites

- [Node.js](https://nodejs.org/) **22 LTS or newer** (Vite needs Node 20.19+ or 22.12+)
- npm (bundled with Node.js)
- [Git](https://git-scm.com/)
- A [MongoDB Atlas](https://www.mongodb.com/atlas) cluster, or a local MongoDB instance (backend only)

Check your versions:

```bash
node -v
npm -v
```

### 1. Clone the repository

```bash
git clone https://github.com/np03cs4s250020-jpg/yatri-sathi.git
cd yatri-sathi
```

### 2. Install dependencies

The frontend and backend are separate npm projects, so install each one:

```bash
cd client
npm install

cd ../server
npm install
```

### 3. Configure environment variables

The backend reads its secrets from `server/.env`. This file is git-ignored and must **never** be committed. Create it with values like these:

```env
PORT=5000
CLIENT_URL=http://localhost:5173

MONGODB_URI=mongodb+srv://<user>:<password>@<cluster>.mongodb.net/yatri-sathi
JWT_SECRET=<a-long-random-string>

AWS_REGION=ap-south-1
AWS_ACCESS_KEY_ID=<your-key>
AWS_SECRET_ACCESS_KEY=<your-secret>
S3_PUBLIC_BUCKET=<public-photos-bucket>
S3_PRIVATE_BUCKET=<private-documents-bucket>

ESEWA_PRODUCT_CODE=EPAYTEST
ESEWA_SECRET_KEY=<esewa-test-secret>
```

> A `server/.env.example` template will be added as the backend grows. Copy it with `cp server/.env.example server/.env` once it exists.

### 4. Run the app

**Frontend:**

```bash
cd client
npm run dev
```

Then open http://localhost:5173.

**Backend:** the API is under active development. This section will be updated once its start scripts (`npm run dev` with nodemon) are added.

### Other client scripts

| Command | What it does |
| --- | --- |
| `npm run dev` | Start the Vite dev server with hot reload |
| `npm run build` | Build the production bundle into `client/dist/` |
| `npm run preview` | Serve the production build locally |
| `npm run lint` | Run ESLint |

## Author

**Srijan Pokhrel**, Herald College Kathmandu
