# Student Management System using Django

A Django-based student management app for enrollment, authentication, role-based access, notifications, and student/parent records.

## Features
- Student & Parent CRUD
- Custom user model with role-based access control
- Password reset (token-based)
- Media uploads (student photos)
- Notifications and dashboard
- Responsive templates (Bootstrap)
- Dockerized setup (Gunicorn + WhiteNoise)

## Tech Stack
- Django (Python)
- HTML, CSS, JavaScript, Bootstrap
- SQLite (dev), PostgreSQL-ready
- Docker, Docker Compose, Gunicorn, WhiteNoise
- Git

## Project Structure
```
django-project/
├─ manage.py
├─ requirements.txt
├─ Dockerfile
├─ docker-compose.yml
├─ README.md
├─ Home/
│  ├─ settings.py
│  ├─ urls.py
│  ├─ wsgi.py
│  └─ asgi.py
├─ home_auth/
│  ├─ models.py
│  ├─ views.py
│  ├─ urls.py
│  └─ migrations/
├─ student/
│  ├─ models.py
│  ├─ views.py
│  ├─ urls.py
│  └─ migrations/
├─ school/
│  ├─ models.py
│  ├─ views.py
│  └─ urls.py
├─ templates/
│  ├─ authentication/
│  ├─ Home/
│  └─ students/
├─ static/
│  └─ assets/
└─ media/
   └─ students/
```

## Setup

### Local (no Docker)
```bash
git clone https://github.com/yourusername/django-project.git
cd django-project
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser
python manage.py collectstatic --noinput
python manage.py runserver
```

### Docker
```bash
docker-compose up --build
```

## Configuration
Create a `.env` in project root:
```env
DEBUG=True
SECRET_KEY=your_secret_key_here
DATABASE_URL=sqlite:///db.sqlite3
# For Postgres:
# DATABASE_URL=postgres://user:password@localhost:5432/dbname
```

## URLs
- /admin/ (Admin)
- / (Dashboard)
- /authentication/ (Auth)
- /student/ (Student management)

## Testing
```bash
python manage.py test
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

## Demo

![Dashboard demo](student/Screenshot_2025-09-26_at_12-09-01_Preskool_-_Dashboard.png)


