# LMS Backend (Django REST Framework)

A professional Learning Management System (LMS) backend built with Django and Django REST Framework. This project covers user management, hierarchical educational materials, payment integration, and automated documentation.

## 🚀 Key Features

### 👤 User Management & Security
- **Email Authentication**: Custom user model using email as the primary identifier.
- **JWT Authentication**: Secure token-based access using `SimpleJWT`.
- **RBAC (Role-Based Access Control)**:
    - **Moderators**: Can view and edit all materials but cannot create or delete.
    - **Owners**: Full CRUD access to their own educational materials.

### � Educational Materials (`materials` app)
- **Courses & Lessons**: Hierarchical structure with nested serializers.
- **Course Subscriptions**: Users can toggle subscriptions to track course updates.
- **YouTube Validator**: Custom validator ensures educational videos are strictly from `youtube.com`.
- **Pagination**: Optimized API responses with 10 items per page.

### � Stripe Integration
- **Automated Payments**: Integrated with the Stripe API to handle course/lesson purchases.
- **Payment Lifecycle**: Create product -> Create price -> Create checkout session -> Retrieve status.
- **Checkout Links**: Returns a direct Stripe payment link for users in the response.

### 📖 API Documentation
Full documentation is automatically generated using `drf-spectacular` (OpenAPI 3.0):
- **Swagger UI**: `/api/docs/swagger/`
- **Redoc**: `/api/docs/redoc/`
- **Schema**: `/api/schema/`

## 📦 Tech Stack
- **Framework**: Django 5.x, DRF
- **Auth**: SimpleJWT
- **Payments**: Stripe API
- **Docs**: drf-spectacular
- **Database**: SQLite (Default)

## 🛠️ Setup & Installation

1. **Clone & Install**:
   ```bash
   pip install -r requirements.txt
   ```

2. **Environment Configuration**:
   Add your Stripe key to `config/settings.py`:
   ```python
   STRIPE_API_KEY = 'sk_test_...'
   ```

3. **Migrations & Data**:
   ```bash
   python manage.py migrate
   python manage.py fill_payments  # Optional: Seed initial payment data
   ```

4. **Run Server**:
   ```bash
   python manage.py runserver
   ```

## 🔗 API Endpoints

| Resource | Method | Endpoint | Description |
| :--- | :--- | :--- | :--- |
| **Auth** | POST | `/api/users/login/` | Obtain JWT tokens |
| **Auth** | POST | `/api/users/token/refresh/` | Refresh JWT tokens |
| **Courses** | GET/POST | `/api/materials/courses/` | List/Create Courses |
| **Lessons** | GET | `/api/materials/lessons/` | List Lessons (Paginated) |
| **Subscription** | POST | `/api/materials/course/subscribe/` | Toggle Subscription |
| **Payments** | POST | `/api/users/payments/create/` | Generate Stripe Checkout Link |
| **Payments** | GET | `/api/users/payments/status/<id>/` | Check Stripe Payment Status |

## 🧪 Testing
- **Local Tests**: `python manage.py test`
- **Coverage**: `coverage run manage.py test`

---
*Created as part of the DRF Learning Path.*
