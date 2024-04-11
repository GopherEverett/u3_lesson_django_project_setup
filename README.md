# Django Project Setup w/Virtual Environment
---
## Overview
In this lesson we will set up a Django project utilizing a virtual environment for our packages.
--
1. Create a directory for the project and app.
```zsh
mkdir <project name>
```
2. Change into directory and create a virtual environment with `venv`.
```zsh
cd <project name>
python3 -m venv .venv
```
- `.venv` is the name of the virtual environment.

3. Activate the virtual environment.
```zsh
source .venv/bin/activate
```
4. Install `Django` and `psycopg2-binary` packages with `pip`.
```zsh
pip install Django
pip install psycopg2-binary
```
5. Create a `requirements.txt` for the dependencies.
```zsh
pip freeze > requirements.txt
```
6. Create project with `Django`.
```zsh
python3 -m django startproject <project name> .
```
- Don't forget the `.` at the end!

7. Create app via Django's `manage.py`.
```zsh
python3 manage.py startapp <app name>
```
8. Add app name to the `INSTALLED_APPS` list in `settings.py`.
```py
INSTALLED_APPS = [
	'<app name>',
	'django.contrib.admin',
	'django.contrib.auth',
	'django.contrib.contenttypes',
	'django.contrib.sessions',
	'django.contrib.messages',
	'django.contrib.staticfiles',
]
```
9. While in `settings.py` change the database configuration.
```py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': '<database name>',
        # 'HOST': 'localhost',  <-- (optional) some computers might need this line
        # 'USER': 'admin', <-- (optional) postgres user name, if you have to sign into an account to open psql, you will want to add that user name here.
        # 'PASSWORD': 'password123', <-- (optional) postgres user password, if you have to sign into an account to open psql, you will want to add that user password here.
        # 'PORT': 3000 <-- if you desire to use a port other than 8000, you can change that here to any valid port id, some number between 1 and 65535 that isn't in use by some other process on your machine. The reason for this port number range is because of how TCP/IP works, a TCP/IP protocol network(the most widely used protocol used on the web) allocated 16 bits for port numbers. This means that number must be greater than 0 and less than 2^15 -1.
    }
}
```

10. Create a postgres database locally on your machine.
```zsh
createdb <database name>
```

11. Check to make sure the project starts up:
```zsh
python3 manage.py runserver
```
12. There are several migrations pending (i.e., waiting to be applied to the database) - so let’s apply them.
```zsh
python3 manage.py migrate
```
13. Open VSCode.
```zsh
code .
```

14. Create a `.gitignore` file in the root of the project and add `.venv` to it.

15. Initialize a git repo locally and connect to a remote repo created in Github.
```zsh
git init
git remote add origin <ssh URL from Github repo>
```

16. Create a superuser for the admin site.
```zsh
python3 manage.py createsuperuser
```

17. Enjoy!