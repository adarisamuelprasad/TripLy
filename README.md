# TripLy

A ride-sharing and carpooling platform built during the **Infosys Springboard Internship 6.0** (Java Technology Stack track), November 2025 to January 2026.

Team: **Adari Samuel Prasad** (team lead) and **Mothkuri Ranvitha**.

Drivers publish rides. Passengers search by route and date, book seats and pay online. Both sides get live updates as bookings and rides change.

## Features

- **Accounts and roles**: JWT authentication with rider, driver and admin roles (Spring Security).
- **Rides**: publish rides, search by route and date, seat availability, and fares calculated from the route distance (OpenRouteService directions API).
- **Booking and payment**: seat booking with per-seat fares, Stripe payments, PDF tickets and payment reports (PDFBox on the server, jsPDF in the browser).
- **Live updates**: booking, status-change and cancellation notifications over WebSockets (STOMP with SockJS).
- **Reminders**: scheduled ride-status updates and email reminders (Spring scheduling, JavaMail).
- **Reviews and ratings**, an analytics dashboard (Recharts) and an admin panel.

## Stack

| Part | Technologies |
|---|---|
| Backend (`triply-backend`) | Java 17, Spring Boot, Spring Security, Spring Data JPA, PostgreSQL, JJWT, WebSocket (STOMP), Stripe Java, PDFBox, Spring Mail |
| Frontend (`triply-frontend`) | React 18, Vite, Tailwind CSS, React Router, Axios, SockJS + STOMP, Recharts, jsPDF |

## Run it locally

Backend (port 8081). Secrets come from environment variables, never from the repository:

```bash
export DB_URL=jdbc:postgresql://localhost:5433/triply   # optional, this is the default host/port
export DB_USERNAME=postgres
export DB_PASSWORD=...
export JWT_SECRET=...            # a long random string
export STRIPE_API_KEY=...        # Stripe test key; payments run in mock mode without it
export OPENROUTE_API_KEY=...     # OpenRouteService key for route distances
export MAIL_USERNAME=... MAIL_PASSWORD=...   # SMTP account for reminder emails (optional)

cd triply-backend
mvn spring-boot:run
```

Frontend:

```bash
cd triply-frontend
npm install
npm run dev
```

## Internship deliverables

`Milestone-3.pdf` is the milestone report submitted for the internship. `task.md` tracks the milestone checklist.
