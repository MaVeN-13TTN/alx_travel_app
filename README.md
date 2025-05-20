# ALX Travel App

A real-world Django application that serves as the foundation for a travel listing platform. This project includes a robust setup with MySQL database integration, Swagger API documentation, and Celery for task processing.

## Key Features

- **Listings Management**: Complete CRUD operations for travel listings
- **REST API**: Built with Django REST Framework
- **API Documentation**: Automatic documentation with Swagger
- **Environment Configuration**: Secure configuration management with django-environ
- **Database**: MySQL integration for robust data storage
- **Background Tasks**: Celery with RabbitMQ for asynchronous task processing

## Tech Stack

- Django 5.2
- Django REST Framework
- MySQL
- Swagger (via drf-yasg)
- Celery and RabbitMQ
- CORS Headers

## Setup Instructions

### Prerequisites

- Python 3.6+
- MySQL
- RabbitMQ (for Celery)

### Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/alxtravelapp.git
cd alxtravelapp
```

2. Create and activate a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Create a .env file in the project root with the following variables (adjust as needed):
```
DEBUG=True
SECRET_KEY=your-secret-key
ALLOWED_HOSTS=localhost,127.0.0.1

DB_NAME=alxtravelapp
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_HOST=localhost
DB_PORT=3306

CORS_ALLOWED_ORIGINS=http://localhost:3000,http://127.0.0.1:3000
```

5. Create the MySQL database:
```sql
CREATE DATABASE alxtravelapp CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

6. Apply migrations:
```bash
python manage.py migrate
```

7. Create a superuser:
```bash
python manage.py createsuperuser
```

8. Run the development server:
```bash
python manage.py runserver
```

9. Access the application:
   - Admin interface: http://127.0.0.1:8000/admin/
   - API root: http://127.0.0.1:8000/api/
   - Swagger documentation: http://127.0.0.1:8000/swagger/
   - ReDoc documentation: http://127.0.0.1:8000/redoc/

### Running Celery (optional)

Start the Celery worker:
```bash
celery -A alx_travel_app.alx_travel_app worker -l info
```

## Project Structure

```
.
├── .env
├── .env.example
├── .gitignore
├── README.md
├── manage.py
├── requirements.txt
├── alx_travel_app/                  # First level package
│   └── alx_travel_app/             # Django project configuration folder
│       ├── __init__.py             # Project __init__ (for Celery)
│       ├── settings.py             # Project settings
│       ├── urls.py                 # Project URLs
│       ├── celery_app.py           # Celery configuration
│       ├── wsgi.py                 # WSGI configuration
│       ├── asgi.py                 # ASGI configuration
│       └── listings/               # Listings app
│           ├── __init__.py
│           ├── admin.py
│           ├── apps.py
│           ├── models.py
│           ├── serializers.py
│           ├── urls.py
│           ├── views.py
│           └── migrations/
└── venv/                           # Virtual environment (typically in .gitignore)
```

## API Endpoints

- Interactive API documentation is available at `/swagger/` endpoint
- ReDoc alternative interface is available at `/redoc/` endpoint

## License

This project is licensed under the MIT License.
