# Django Chat - Development Steps

## Installation and Setup

**Note:** I'm using Windows 11, so the commands may vary for other operating systems.

### Download and Install
- [VS Code](https://code.visualstudio.com/)
- [Git](https://git-scm.com/downloads)
- [Python 3.10.11](https://www.python.org/downloads/release/python-31011/)

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

