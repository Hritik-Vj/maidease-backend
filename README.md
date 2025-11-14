# MaidEase Backend (FastAPI)

The MaidEase backend powers all core functionality of the platform — authentication, maid profiles, bookings, reviews, and notifications.  
It is built using **FastAPI**, **PostgreSQL**, and **SQLAlchemy**, with JWT-based authentication and a clean service-layer architecture.

---

## Tech Stack
- FastAPI (Python 3.11+)
- PostgreSQL + SQLAlchemy ORM
- Alembic (database migrations)
- Uvicorn (ASGI server)
- Pytest (unit testing)
- Docker + Docker Compose

---

## What This Backend Does (How the System Works)

The MaidEase backend acts as the central engine of the application. Here’s how each part works:

### 1. Authentication & Authorization
- Users register as either **Customer** or **Maid**.
- Passwords are hashed before storing in PostgreSQL.
- On login, the backend issues a **JWT token**.
- This token is required for all protected routes.

### 🧍 2. User + Maid Profile Management
- Customers only have basic profile info (name, email, phone).
- Maids have extended profiles:
  - skills
  - experience
  - hourly rate
  - availability slots
  - average rating

### 3. Booking System
- Customers create bookings by selecting:
  - a maid  
  - a date  
  - a time slot  
  - a service type  
- The booking starts in **pending** status.
- Maids can:
  - accept  
  - reject  
  - mark as completed  

### 4. Reviews
After a job is marked complete:
- The customer can submit a rating + comment.
- The maid’s overall rating updates automatically.

### 5. Notifications System
The backend generates notifications for:
- booking request  
- booking accepted  
- booking canceled  
- job completed  

Notifications can be delivered through email/SMS (in production setups).

---

## Project Structure

app/
├─ api/ # Route handlers
├─ models/ # SQLAlchemy ORM models
├─ schemas/ # Pydantic request/response schemas
├─ services/ # Business logic
├─ db/ # DB session, config
├─ tests/ # Unit tests
└─ main.py # Application entrypoint
