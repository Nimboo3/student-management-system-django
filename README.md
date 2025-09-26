
# Student Management System

A comprehensive **Student Management System** built with **Django**, designed to efficiently manage student information, enrollment, authentication, and administrative functionalities. This application provides a streamlined solution for educational institutions to manage student data with role-based access control.

## Features

- **Student Management**: Complete student enrollment, registration and profile management
- **Parent Information**: Comprehensive parent/guardian details management
- **Custom Authentication**: Role-based access control with custom user model
- **Password Reset**: Secure password reset functionality with token-based verification
- **Responsive Dashboard**: Mobile-friendly admin dashboard with statistics
- **Media Management**: Student photo upload and management
- **Notification System**: Built-in notification system for users
- **REST API Ready**: Structured for easy API integration

## Technologies Used

- **Backend**: Django 5.1.1, Python 3.10+
- **Frontend**: HTML5, CSS3, JavaScript, Bootstrap 4+
- **Database**: SQLite (development), PostgreSQL ready
- **Media Handling**: Pillow for image processing
- **Deployment**: Docker, Gunicorn, Whitenoise for static files
- **Version Control**: Git
- **Containerization**: Docker & Docker Compose

## Project Structure

```
django-project/
│
├── manage.py                  # Django management script
├── requirements.txt           # Python dependencies
├── Dockerfile                # Docker configuration
├── docker-compose.yml        # Docker Compose setup
├── README.md                 # Project documentation
│
├── Home/                     # Main Django project
│   ├── __init__.py
│   ├── settings.py           # Django settings
│   ├── urls.py              # Main URL configuration
│   ├── wsgi.py              # WSGI application
│   └── asgi.py              # ASGI application
│
├── home_auth/               # Authentication app
│   ├── models.py            # Custom user model & password reset
│   ├── views.py             # Authentication views
│   ├── urls.py              # Authentication URLs
│   └── migrations/          # Database migrations
│
├── student/                 # Student management app
│   ├── models.py            # Student & Parent models
│   ├── views.py             # Student CRUD operations
│   ├── urls.py              # Student URLs
│   └── migrations/          # Database migrations
│
├── school/                  # School administration app
│   ├── models.py            # Notification model
│   ├── views.py             # Dashboard views
│   └── urls.py              # School URLs
│
├── templates/               # HTML templates
│   ├── authentication/      # Auth templates
│   ├── Home/               # Dashboard templates
│   └── students/           # Student templates
│
├── static/                  # Static files
│   └── assets/             # CSS, JS, Images
│
└── media/                   # User uploaded files
    └── students/           # Student photos
```

## Installation

### Prerequisites
- Python 3.8+ 
- pip (Python package manager)
- Git

### Method 1: Local Development (Without Docker)

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/django-project.git
   cd django-project
   ```

2. **Create virtual environment**
   ```bash
   python -m venv venv
   
   # On Windows
   venv\Scripts\activate
   
   # On macOS/Linux
   source venv/bin/activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run database migrations**
   ```bash
   python manage.py makemigrations
   python manage.py migrate
   ```

5. **Create superuser**
   ```bash
   python manage.py createsuperuser
   ```

6. **Collect static files**
   ```bash
   python manage.py collectstatic --noinput
   ```

7. **Run the development server**
   ```bash
   python manage.py runserver
   ```

   Visit http://127.0.0.1:8000 to access the application.

### Method 2: Docker Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/django-project.git
   cd django-project
   ```

2. **Build and run with Docker Compose**
   ```bash
   docker-compose up --build
   ```

   The application will be available at http://localhost:8000

## Configuration

### Environment Variables

Create a `.env` file in the root directory for environment-specific configurations:

```env
DEBUG=True
SECRET_KEY=your_secret_key_here
DATABASE_URL=sqlite:///db.sqlite3

# For production with PostgreSQL
# DATABASE_URL=postgres://user:password@localhost:5432/dbname

# Email settings (optional)
# EMAIL_HOST=smtp.gmail.com
# EMAIL_PORT=587
# EMAIL_USE_TLS=True
# EMAIL_HOST_USER=your-email@gmail.com
# EMAIL_HOST_PASSWORD=your-app-password
```

### Database Configuration

The project is configured to use SQLite by default. For production, update the `DATABASES` setting in `Home/settings.py` to use PostgreSQL:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'your_db_name',
        'USER': 'your_db_user',
        'PASSWORD': 'your_db_password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

## Running the Project

### Development Server
```bash
python manage.py runserver
```

### Production with Gunicorn
```bash
gunicorn --bind 0.0.0.0:8000 Home.wsgi:application
```

### Docker Production
```bash
docker-compose -f docker-compose.prod.yml up --build
```

## API Endpoints

- `/admin/` - Django admin interface
- `/` - Dashboard home
- `/student/` - Student management
- `/authentication/` - User authentication
- `/student/add/` - Add new student
- `/student/edit/<slug>/` - Edit student details

## Testing

Run the test suite:
```bash
python manage.py test
```

Run tests for specific app:
```bash
python manage.py test home_auth
python manage.py test student
python manage.py test school
```

## Common Development Tasks

### Create new migrations
```bash
python manage.py makemigrations
```

### Apply migrations
```bash
python manage.py migrate
```

### Create superuser
```bash
python manage.py createsuperuser
```

### Collect static files
```bash
python manage.py collectstatic
```

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Support

For support, email support@example.com or create an issue on GitHub.
Follow the steps below to get the project up and running on your local machine:

### **1. Clone the Repository**
```bash
git clone https://github.com/yourusername/student-management-system.git
cd student-management-system
```

### **2. Create a Virtual Environment**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### **3. Install Dependencies**
```bash
pip install -r requirements.txt
```

### **4. Set Up Database**
Make sure to set up your database (e.g., PostgreSQL) and update the `DATABASES` configuration in `student_management/settings.py`.

### **5. Run Migrations**
```bash
python manage.py migrate
```

### **6. Create Superuser**
```bash
python manage.py createsuperuser
```

### **7. Run the Application**
```bash
python manage.py runserver
```
Visit `http://localhost:8000` to access the app.

## **Configuration**
You'll need a `.env` file for environment-specific configurations. Example:

```bash
DEBUG=True
SECRET_KEY='your_secret_key'
DATABASE_URL=postgres://user:password@localhost:5432/your_db_name
```

Make sure to configure settings like database, static files, and email backend properly for production.

## **Running the Project with Docker (Optional)**
If you've Dockerized the project, you can run it as follows:

```bash
docker-compose up --build
```
This will build the Docker image and run the Django application and the PostgreSQL service.

## **Video Links**
Watch the videos to learn in proper way.
https://youtu.be/mM6vMMLYJHY


## **Testing**
You can run the unit tests with Django's built-in testing framework:

```bash
python manage.py test
```

This will run all the tests located in the `tests.py` files of your Django apps.

## **Contributing**
If you want to contribute to this project, please follow the steps below:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature-name`).
3. Commit your changes (`git commit -am 'Add a new feature'`).
4. Push to the branch (`git push origin feature/your-feature-name`).
5. Create a pull request.

## **License**
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


