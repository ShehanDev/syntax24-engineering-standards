# Architecture

## System Overview
User
  ↓
Next.js Frontend
  ↓
Server / API Layer
  ↓
Supabase Database

## Tech Stack & External Services
* **Authentication:** Clerk
* **Payments:** Stripe
* **Email:** Resend
* **Analytics:** PostHog
* **Error monitoring:** Sentry
* **Deployment:** Vercel

## Project Structure
* `/app` — Routes and pages
* `/components` — Reusable UI
* `/lib` — Utilities and configuration
* `/services` — API and external services
* `/types` — TypeScript types
* `/public` — Static assets
* `/docs` — Project documentation

## Data Flow
1. User interacts with the UI
2. Frontend sends validated request
3. Server verifies authentication/authorization
4. Database or external service processes request
5. Response returns to the UI
6. UI handles success, loading and error states

## Database & Storage
*(Define where specific tables, schemas, and media uploads live)*

## Scalability Notes
*(Outline caching strategies, queues, monitoring, background jobs, and future considerations)*