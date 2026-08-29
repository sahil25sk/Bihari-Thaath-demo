# Bihari Thaath — Premium Demo Website

A complete, deployable restaurant demo for **Bihari Thaath, Bihta**.

## Verified business details used in the demo

Current public listings identify Bihari Thaath as a restaurant in Bihta, with North Indian/Kebab cuisine, at/near Gate 1 opposite ITI. The public listings also provide the restaurant phone number and menu categories. Hours shown in the demo are based on the current business listing and include a note to call ahead because restaurant hours can change.

The project intentionally **does not claim poolside dining** because the available current sources reviewed for this build were not strong enough to make that claim confidently. It also does not invent awards, reviews, customer counts or an official logo.

## Architecture

- Node.js built-in `http` server — no native database dependency and no PowerShell/npm-script-specific setup.
- Persistent menu data: `data/menu.json`.
- Uploaded menu images: `public/uploads/`.
- Admin authentication: signed, HTTP-only cookie session.
- No SMTP, SMS, OTP, payment gateway or unnecessary third-party backend services.
- Static frontend served by the same Node process.
- `PORT` and `HOST` are deployment-aware.

## Run locally

```bash
npm install
npm start
```

Open:

`http://localhost:3000`

Admin:

`http://localhost:3000/admin`

Default demo credentials:

- Email: `mrinal@biharithaath.com`
- Password: `mrinaldemo2026`

For any public deployment, set your own `ADMIN_PASSWORD` and a long random `SESSION_SECRET` as environment variables.

## Environment variables

Copy `.env.example` into your deployment provider's environment-variable settings. Node does not automatically load `.env` in this project, so values should be supplied by the hosting environment.

- `PORT` — hosting provider port, default `3000`
- `HOST` — bind address, default `0.0.0.0`
- `ADMIN_EMAIL` — admin email, default `mrinal@biharithaath.com`
- `ADMIN_PASSWORD` — admin password, default demo value `mrinaldemo2026`
- `SESSION_SECRET` — cookie-signing secret

## Admin capabilities

- Add, edit and delete dishes
- Search and filter
- Category
- Price and optional original/discount prices
- Quantity/unit
- Stock quantity
- Automatic out-of-stock state when quantity reaches zero
- Featured state
- Active/hidden state
- Description
- Image upload (JPG/PNG/WEBP/AVIF, max 4MB)
- Live preview
- Persistent server-side data

## Deployment

The application is a single Node service. Set the hosting start command to `npm start`. The service binds to `0.0.0.0` and reads the hosting provider's `PORT`.

For persistent menu changes and uploads, use a hosting environment with a persistent writable filesystem/volume. If a serverless platform does not provide persistent local storage, the JSON/upload architecture should not be used there without adding a persistent storage provider.

## Content and imagery

The menu seed data is based on current public menu listings. Prices are demo seed values drawn from those listings and should be confirmed with the restaurant before public launch because restaurant pricing can change.

The site uses remote food/ambience imagery as visual demo assets. Replace these with Bihari Thaath-owned/licensed photographs before public commercial launch.
