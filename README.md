# E-Commerce Backend API

A RESTful backend for an e-commerce platform, built with FastAPI — covering product catalog, cart, orders, and user authentication.

## Problem
Most e-commerce learning projects stop at a simple CRUD app. This one models the actual workflow of an online store: browsing products, managing a cart, placing orders, and tracking their status — with proper auth and role separation between customers and admins.

## What it does
- User registration/login with JWT-based authentication
- Role-based access: **customer** vs **admin**
- Product catalog with categories, search, and filtering
- Admin-only endpoints to add/update/remove products and manage stock
- Cart management (add/update/remove items, view cart total)
- Order placement from cart, with order history per user
- Order status tracking (placed → confirmed → shipped → delivered)
- Input validation and consistent error responses across all endpoints

## Tech Stack
- **Backend:** FastAPI
- **Database:** PostgreSQL
- **ORM:** SQLAlchemy + Alembic (migrations)
- **Auth:** JWT (python-jose) + password hashing (passlib/bcrypt)
- **Validation:** Pydantic
- **Testing:** Pytest
- **Containerization:** Docker + docker-compose

## API Design (planned)

| Resource | Endpoint | Method | Access |
|---|---|---|---|
| Auth | `/auth/register` | POST | Public |
| Auth | `/auth/login` | POST | Public |
| Products | `/products` | GET | Public |
| Products | `/products/{id}` | GET | Public |
| Products | `/products` | POST | Admin |
| Products | `/products/{id}` | PUT / DELETE | Admin |
| Cart | `/cart` | GET | Customer |
| Cart | `/cart/items` | POST | Customer |
| Cart | `/cart/items/{id}` | PUT / DELETE | Customer |
| Orders | `/orders` | POST | Customer |
| Orders | `/orders` | GET | Customer (own) / Admin (all) |
| Orders | `/orders/{id}/status` | PATCH | Admin |

## Database Schema (high-level)
- **User** — id, name, email, hashed_password, role
- **Product** — id, name, description, price, stock, category
- **CartItem** — id, user_id, product_id, quantity
- **Order** — id, user_id, status, total_amount, created_at
- **OrderItem** — id, order_id, product_id, quantity, price_at_purchase

## Status
In development.

## Roadmap
- [ ] Upload source code
- [ ] Add setup/run instructions (local + Docker)
- [ ] Add Postman/Swagger collection
- [ ] Add automated test coverage
- [ ] Deploy a live demo link
- [ ] (Stretch) Integrate a payment gateway sandbox (Razorpay/Stripe test mode)

---
*Code coming soon — this repo currently documents the project scope and design.*
