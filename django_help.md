<h1> Django Help </h1>
A guide for creating a Django project for use

<b>Start A Project</b>

```
mkdir FolderName
cd FolderName
virtualenv .
source bin/activate
pip install django
django-admin.py startproject ProjectName
python manage.py migrate
python manage.py runserver
python manage.py createsuperuser
python manage.py migrate
python manage.py runserver
```

<b>Some common installations(optional)</b>

```
# for a postgresql database
pip install psycopg2

# for a mysql database
pip install MySQL-python

# for use on heroku
pip install gunicorn dj-database-url

pip install django-crispy-forms
pip install pillow

```
<b>Changes in settings.py</b>

```
# set template directory

os.path.join(BASE_DIR, 'templates')
```


```
#set PostgreSQL as Database

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'dbname',
        'USER': 'user',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '',
    }
}
```

```
#set timezone

TIME_ZONE = 'Asia/Dhaka'
```



```
# Static files (CSS, JavaScript, Images)

PROJECT_ROOT = os.path.dirname(os.path.abspath(__file__))
STATIC_ROOT = os.path.join(PROJECT_ROOT, 'staticfiles')
STATIC_URL = '/static/'

STATICFILES_DIRS = (
    os.path.join(BASE_DIR, 'static'),
)
```


```
# Serve media files uploaded by users

MEDIA_URL = '/media/'
MEDIA_ROOT = os.path.join(BASE_DIR, 'media/') 
```



<b>Build An App</b>
```
python manage.py startapp AppName
python manage.py migrate
```