# Bench & Bolt

A small e-commerce site: Express.js + SQLite backend, plain HTML/CSS/JS frontend.

## Run it
    npm install
    npm start
Open http://localhost:3000. The database (shop.db) and 8 demo products are created on first run.
Set SESSION_SECRET in production.

## Structure
- server.js: REST API (products, auth, orders), sessions
- db.js: SQLite schema (users, products, orders, order_items) + seed data
- public/: pages (index, product, cart, login, orders), css/style.css, js/app.js

## API
GET  /api/products?q=&category=   GET /api/products/:id   GET /api/categories
POST /api/register  POST /api/login  POST /api/logout  GET /api/me
POST /api/orders (auth)  GET /api/orders (auth)

## Notes
- Passwords are hashed with bcrypt; sessions use an httpOnly cookie.
- The cart lives in the browser. At checkout the server recalculates prices
  and checks stock inside one database transaction.
- Payment is not integrated: orders are saved as "placed". Add Stripe or similar next.
