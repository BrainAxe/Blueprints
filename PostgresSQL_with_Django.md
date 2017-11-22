#How To Use PostgreSQL with Django


<br>

<h3>Install the Components from the Ubuntu Repositories</h3>

First step will be install all of the pieces that we need from the repositories. Install pip, the Python package manager, in order to install and manage our Python components. We will also install the database software and the associated libraries required to interact with them.

The following apt commands will get the needed packages:

```
sudo apt-get update
sudo apt-get install python-pip python-dev libpq-dev postgresql postgresql-contrib
```

With the installation out of the way, Create our database and database user.

<h3>Create a Database and Database User</h3>

By default, Postgres uses an authentication scheme called "peer authentication" for local connections. Basically, this means that if the user's operating system username matches a valid Postgres username, that user can login with no further authentication.

During the Postgres installation, an operating system user named postgres was created to correspond to the postgres PostgreSQL administrative user. 

Change to this user to perform administrative tasks:
```
sudo su - postgres
```
In a shell session for the postgres user. Log into a Postgres session by typing:

```
psql
```

First, Create a database for Django project. Each project should have its own isolated database for security reasons. Database name is myproject in this guide, but it's always better to select something more descriptive:

```
CREATE DATABASE myproject;
```

Remember to end all commands at an SQL prompt with a semicolon.

Next, Create a database user which will use to connect to and interact with the database. Set the password to something strong and secure:

```
CREATE USER myprojectuser WITH PASSWORD 'password';
```

Now, give the database user access rights to the database we created:

```
GRANT ALL PRIVILEGES ON DATABASE myproject TO myprojectuser;
```

Exit the SQL prompt to get back to the postgres user's shell session:

```
\q
```
Exit out of the postgres user's shell session to get back to your regular user's shell session:
```
exit
```

<h3>Install psycopg2</h3> 

Install the psycopg2 package that will allow  to use the database  configured:

```
pip install django psycopg2
```


<h3>Configure the Django Database Settings</h3>


Open the main Django project settings file located within the child project directory:

```
nano ~/myproject/myproject/settings.py
```

Towards the bottom of the file, a DATABASES section that looks like this:

```
. . .

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}

. . .
```
This is currently configured to use SQLite as a database. Change this so that  PostgreSQL database is used instead.


First, change the engine so that it uses the postgresql_psycopg2 backend instead of the sqlite3 backend. For the NAME, use the name of the database (myproject in the example). Add login credentials. Add the username, password, and host to connect to and leave blank the port option so that the default is selected:

```
. . .

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'myproject',
        'USER': 'myprojectuser',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '',
    }
}

. . .
```
When  finished, save and close the file.
