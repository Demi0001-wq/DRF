# LMS Backend (Django REST Framework)

A robust Learning Management System (LMS) backend built with Django and Django REST Framework. This project features a custom user model, a dedicated materials application with hierarchical lesson structure, and demonstration of multiple API architectural patterns.

## 🚀 Features

### 👤 Custom User Management
- **Email Authentication**: Replaces the default Django username with email-based login.
- **Extended Profiles**: Includes fields for `telephone`, `city`, and `avatar`.

### 💰 Payments System (`users` app)
- **Payment Tracking**: New `Payment` model tracks user payments for courses or individual lessons.
- **Advanced Filtering**: Built-in payment list API with filtering by course, lesson, and payment method (cash/transfer).
- **Sorting**: Flexible sorting by payment date.

### 🛠️ API Architecture
- **ViewSet Pattern**: `Course` CRUD is implemented using `ModelViewSet`.
- **Generic View Pattern**: `Lesson` CRUD is implemented using granular Generic views.
- **Enhanced Serializers**: 
    - `CourseSerializer` now includes `lessons_count` and nested `lessons` details.
- **Filtering**: Integrated `django-filter` for the Payments API.

## 📦 Tech Stack
- **Framework**: Django 5.x
- **API**: Django REST Framework (DRF)
- **Filtering**: django-filter
- **Image Handling**: Pillow
- **Database**: SQLite (Default)

## 🛠️ Setup & Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Demi0001-wq/DRF.git
   cd DRF
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Run migrations**:
   ```bash
   python manage.py migrate
   ```

4. **Populate Data**:
   ```bash
   python manage.py fill_payments
   ```

5. **Start the server**:
   ```bash
   python manage.py run_server
   ```

## 🔗 API Endpoints

### Courses
- `GET /api/materials/courses/` - List all courses (includes nested lessons)
- `POST /api/materials/courses/` - Create a course

### Lessons
- `GET /api/materials/lessons/` - List all lessons
- `POST /api/materials/lessons/create/` - Create a lesson

### Payments
- `GET /api/users/payments/` - List payments with filtering support.
  - Query params: `paid_course`, `paid_lesson`, `payment_method`, `ordering=payment_date`.

## 🧪 Testing
A comprehensive **Postman Guide** is available in the project documentation for local endpoint verification.
