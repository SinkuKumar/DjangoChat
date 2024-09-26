# Django Chat - Development Steps

## Installation and Setup

**Note:** I'm using Windows 11, so the commands may vary for other operating systems.

### Download and Install
- [VS Code](https://code.visualstudio.com/)
- [Git](https://git-scm.com/downloads)
- [Python 3.10.11](https://www.python.org/downloads/release/python-31011/)
- [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)

### Create and Activate Virtual Environment
```bash
python -m venv venv
```
```bash
venv\Scripts\activate
```

**Install Django**
```bash
pip install django
```

**Freeze Requirements**
```bash
pip freeze > requirements.txt
```

## Getting Started
**Create Django Project**
```bash
django-admin startproject django_chat
```

**Create Django App**
```bash
python manage.py startapp chat
```

**Run Server**
```bash
python manage.py runserver
```

**Commit:** Create and setup project

### Setup Database

**Install Packages**
```bash
pip install python-dotenv
pip install mssql-django
```

**Freeze Requirements**
```bash
pip freeze > requirements.txt
```

**Create .env file** in the root directory and add the following
```env
# Django settings
SECRET_KEY = 'Your-secret-key'
DEBUG = True

# Database settings
DB_NAME = 'database-name'
DB_USER = 'database-user'
DB_PSWD = 'database-password'
DB_HOST = 'database-host'
```

**Update settings.py**
- Use `python-dotenv` to load environment variables
- Update `INSTALLED_APPS` with `chat` app
- Update `TIME_ZONE` to `Asia/Kolkata`
- Update `DATABASES` with SQL Server settings
```python
    "default": {
        "ENGINE": "mssql",
        "NAME": os.getenv("DB_NAME"),
        "USER": os.getenv("DB_USER"),
        "PASSWORD": os.getenv("DB_PSWD"),
        "HOST": os.getenv("DB_HOST"),
        "PORT": "1433",
        "CONN_MAX_AGE": None,
        "OPTIONS": {
            "driver": "ODBC Driver 18 for SQL Server",
            "host_is_server": True,
            "extra_params": "TrustServerCertificate=yes",
            # "debug": True,  # Enable query logging
        },
    }
```
- **Note**: If you're using SQL Server, you can use `ODBC Driver 17 for SQL Server`. Depends on which driver you have installed in your system(client).

**Create Database**
```bash
python manage.py migrate
```

**Commit:** Setup database