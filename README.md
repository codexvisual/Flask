# ⚡ Flask Projects

Collection of Flask microservices and web applications demonstrating lightweight and flexible backend development.

## 📋 Overview

This repository contains Flask projects showcasing:
- Microservice architecture
- Lightweight web applications
- Flask extensions (SQLAlchemy, WTForms, etc.)
- Blueprint-based modular design
- Custom middleware and error handling
- RESTful API development
- Authentication and authorization
- Database integration

## 🛠️ Technologies Used

- **Framework**: Flask 2.0+
- **Language**: Python 3.8+
- **Database ORM**: SQLAlchemy
- **Validation**: Flask-WTF, Marshmallow
- **Authentication**: Flask-Login, Flask-JWT-Extended
- **API Documentation**: Flask-RESTX, Flasgger
- **Database**: PostgreSQL, SQLite

## 📁 Project Structure

```
flask_app/
├── app.py
├── requirements.txt
├── .env.example
├── config.py
├── blueprints/
│   ├── __init__.py
│   ├── auth/
│   │   ├── __init__.py
│   │   ├── routes.py
│   │   └── forms.py
│   ├── api/
│   └── main/
├── models/
│   ├── __init__.py
│   └── user.py
├── templates/
├── static/
│   ├── css/
│   ├── js/
│   └── images/
└── tests/
```

## ✨ Key Features

- ✅ Lightweight and flexible architecture
- ✅ Modular design with blueprints
- ✅ SQLAlchemy ORM integration
- ✅ API-first development
- ✅ Template rendering with Jinja2
- ✅ Session management
- ✅ Error handling and logging
- ✅ Form validation
- ✅ Authentication systems
- ✅ Database migrations with Alembic

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- pip
- Virtual environment

### Installation

```bash
# Clone repository
git clone https://github.com/codexvisual/Flask.git
cd Flask

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Setup environment variables
cp .env.example .env

# Run application
python app.py
```

### Access
- Application: http://localhost:5000

## 📚 Flask Concepts

### Basic App

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return 'Hello, Flask!'

if __name__ == '__main__':
    app.run(debug=True)
```

### Blueprints

```python
from flask import Blueprint

user_bp = Blueprint('users', __name__, url_prefix='/users')

@user_bp.route('/')
def list_users():
    return {'users': []}

app.register_blueprint(user_bp)
```

### Database Models

```python
from flask_sqlalchemy import SQLAlchemy

db = SQLAlchemy()

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(80), unique=True, nullable=False)
    email = db.Column(db.String(120), unique=True, nullable=False)
    
    def __repr__(self):
        return f'<User {self.username}>'
```

### Routes

```python
from flask import request, jsonify

@app.route('/api/users', methods=['GET', 'POST'])
def users():
    if request.method == 'POST':
        data = request.get_json()
        # Process data
        return jsonify({'success': True}), 201
    return jsonify({'users': []})
```

### Error Handling

```python
@app.errorhandler(404)
def not_found(error):
    return jsonify({'error': 'Not found'}), 404

@app.errorhandler(500)
def internal_error(error):
    return jsonify({'error': 'Internal server error'}), 500
```

## 🧪 Testing

```bash
# Run tests
pytest

# With coverage
pytest --cov=.
```

### Test Example

```python
import pytest
from app import app

@pytest.fixture
def client():
    return app.test_client()

def test_home(client):
    response = client.get('/')
    assert response.status_code == 200
```

## 🌐 API Routes

```
GET    /api/users          - List all users
POST   /api/users          - Create user
GET    /api/users/<id>     - Get user
PUT    /api/users/<id>     - Update user
DELETE /api/users/<id>     - Delete user
```

## 📦 Requirements

```
Flask==2.3.0
Flask-SQLAlchemy==3.0.0
Flask-Migrate==4.0.0
Flask-Login==0.6.0
Flask-JWT-Extended==4.4.0
Marshmallow==3.18.0
Python-dotenv==1.0.0
pytest==7.0.0
```

## 🔒 Security Features

- Password hashing with werkzeug
- CSRF token protection
- Session security
- Input validation
- SQL injection prevention
- XSS protection
- CORS handling

## 🚀 Deployment

### Using Gunicorn

```bash
pip install gunicorn
gunicorn -w 4 -b 0.0.0.0:8000 app:app
```

### Using Docker

```dockerfile
FROM python:3.9
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["gunicorn", "-w", "4", "-b", "0.0.0.0:8000", "app:app"]
```

## 💡 Best Practices

- Use blueprints for organization
- Implement proper error handling
- Use environment variables for configuration
- Write tests for all endpoints
- Implement logging
- Use database migrations
- Validate all inputs
- Implement rate limiting
- Use authentication properly

## 🔗 Extensions

- Flask-SQLAlchemy: Database ORM
- Flask-Migrate: Database migrations
- Flask-Login: User session management
- Flask-CORS: CORS handling
- Flask-RESTful: REST API support
- Flask-JWT-Extended: JWT authentication

## 🤝 Contributing

Contributions are welcome! Please follow Flask conventions.

## 📧 Support

For issues and questions, please open an issue on GitHub.

---

Made with ⚡ for Flask developers