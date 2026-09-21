# ShopSphere - Full-Stack Production-Ready E-Commerce Platform

ShopSphere is a high-performance, responsive e-commerce web application built using **Django 5**, **Bootstrap 5.3**, and **IntersectionObserver Lazy Loading**. It includes a companion **Spring Boot 3** REST microservice architecture.

---

## Key Features

1. **Responsive Mobile-First UI**
   - Built with Bootstrap 5.3 and custom design tokens (Glassmorphic navbar, gradient hero, badge indicators).
   - Fully responsive across mobile phones (375px+), tablets, laptops, and ultra-wide desktops.

2. **Lazy Loading Engine ("Loading Lazy Future")**
   - Native HTML `loading="lazy"` on all image assets.
   - Progressive blurred placeholder fade-in transitions via `lazyload.js`.
   - Infinite scroll / Lazy pagination loading for product catalog grids.

3. **E-Commerce Modules**
   - **Catalog & Filtering**: Real-time category switching, search bar, min/max price filter, and sorting.
   - **Shopping Cart**: Session-persistent cart for guests and logged-in users with AJAX dynamic quantity updates.
   - **Multi-Step Checkout**: Shipping address, billing breakdown, payment selection, and invoice generation.
   - **User Accounts & Orders**: Registration, Login, Logout, Profile timeline, and order status tracking.
   - **Customer Reviews**: Star ratings and customer comments.

4. **Production Readiness**
   - **Security**: Environment variables via `.env`, CSRF protection, secure cookie handling.
   - **Static Assets**: Configured with `WhiteNoise` for compressed static file serving.
   - **Docker Support**: Ready for zero-configuration containerization (`Dockerfile` & `docker-compose.yml`).
   - **Database Seeding**: Management command `python manage.py seed_shop` populates categories, products, images, and reviews.

---

## Quick Start Instructions

### 1. Setup Virtual Environment & Dependencies
```bash
python -m venv venv
# On Windows PowerShell:
.\venv\Scripts\Activate.ps1
# On Linux/macOS:
source venv/bin/activate

pip install -r requirements.txt
```

### 2. Run Database Migrations & Seed Data
```bash
python manage.py makemigrations shop
python manage.py migrate
python manage.py seed_shop
```

### 3. Start Development Server
```bash
python manage.py runserver
```
Access the application in your browser at `http://127.0.0.1:8000`.

### 4. Admin Access
Create an admin superuser:
```bash
python manage.py createsuperuser
```
Access Django Admin at `http://127.0.0.1:8000/admin/`.

---

## Running with Docker (Production Mode)

```bash
docker-compose up --build
```
The production stack will compile static assets and launch Gunicorn on port `8000`.

---

## Companion Spring Boot Microservice

Inside `spring_boot_service/`:
```bash
cd spring_boot_service
mvn spring-boot:run
```
Access the Spring Boot REST API at `http://localhost:8080/api/products/status`.
