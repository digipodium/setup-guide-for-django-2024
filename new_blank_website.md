# Django website creation
### ❶ Ensure that the Python version installed with Miniconda is greater than 3.9 by running the following command in the Anaconda Prompt:

```bash
python --version
```

### ❷ Install Django using pip and verify the version:

```bash
pip install django
django-admin --version
```

Make sure the Django version is 5 or higher.

### ❸ Open Anaconda Prompt and navigate to the Documents folder:

```bash
cd Documents
```

##### Create a blank directory:

```bash
mkdir my_django_project
cd my_django_project
```

### ❹ Launch VSCode using the following command:

```bash
code .
```

If the above command doesn't work, manually open VSCode and then open the folder `my_django_project`.

### ❺ Config VSCode
#### Check if the Python extension is installed in VSCode by navigating to the Extensions view (`Ctrl+Shift+X`) and searching for "Python".

#### Press `Ctrl+Shift+P` to open the command palette and search for "`Python: Select Interpreter`". Choose the Python interpreter with version 3.9 or higher (miniconda).

#### Switch to the command prompt terminal in VSCode, as PowerShell sometimes doesn't work well with Python environments.

### ❻ Create the Django project folder using the following command:

```bash
django-admin startproject config .
```

This command creates a Django project named `config` in the current directory (`.`).

### ❼ Create the necessary folders for your project structure:

```bash
mkdir templates
cd templates
mkdir base components
cd ..
mkdir assets
cd assets
mkdir css js images videos fonts
cd ..
```
Explanation:
- `mkdir templates`: Creates a directory named 'templates' in the current location.
- `cd templates`: Changes the current directory to 'templates'.
- `mkdir base components`: Creates two directories named 'base' and 'components' inside the 'templates' directory.
- `cd ..`: Moves one directory up (back to the parent directory).
- `mkdir assets`: Creates a directory named 'assets' in the current location.
- `cd assets`: Changes the current directory to 'assets'.
- `mkdir css js images videos fonts`: Creates five directories named 'css', 'js', 'images', 'videos', and 'fonts' inside the 'assets' directory.
- `cd ..`: Moves one directory up (back to the parent directory).

### ❽ Open `settings.py` file located in the `config` folder and make the following changes:

```python
# settings.py
...
TEMPLATES = [
    {
        ...
        'DIRS': [BASE_DIR.joinpath('templates')],
        ...
    },
]
...
TIME_ZONE = 'Asia/Kolkata'

STATIC_URL = '/static/'
STATICFILES_DIRS = [BASE_DIR.joinpath('assets')]
STATIC_ROOT = BASE_DIR.joinpath('staticfiles')

MEDIA_URL = '/media/'
MEDIA_ROOT = BASE_DIR.joinpath('media')
...
```

Explanation:

TEMPLATES Configuration:

- Specifies the directory for template files.
Utilizes BASE_DIR.joinpath('templates') to locate the 'templates' directory within the project's base directory.
TIME_ZONE Configuration:

- Sets the default time zone to 'Asia/Kolkata'.
STATIC_URL Configuration:

- Defines the URL prefix for serving static files.
STATICFILES_DIRS Configuration:

- Lists additional directories for serving static files.
STATIC_ROOT Configuration:

- Specifies the directory where collected static files will be stored during deployment.
MEDIA_URL Configuration:

- Sets the URL prefix for serving media files.
MEDIA_ROOT Configuration:

- Defines the directory where uploaded media files will be stored.

### ❾ Inside `settings.py`, update the database settings to use MySQL and install the required libraries:

##### Install MySQL client using the terminal
```shell 
pip install mysqlclient
```
##### Update the `DATABASES` configuration:
```python
# settings.py

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'your_database_name',
        'USER': 'your_database_user',
        'PASSWORD': 'your_database_password',
        'HOST': 'localhost',
        'PORT': '3306',
    }
}
```

- **DATABASES Configuration**:
  - Configures the database connection for the project using a dictionary.
  - The 'default' key specifies the default database connection.

- **ENGINE Configuration**:
  - Defines the database engine to be used, set to 'django.db.backends.mysql' indicating MySQL database backend.

- **NAME, USER, PASSWORD, HOST, and PORT Configuration**:
  - Specifies the database name, username, password, host, and port respectively.
  - These values should be replaced with appropriate credentials for the MySQL database.

- **Connection Details**:
  - Establishes a connection to a MySQL database named 'your_database_name' hosted on 'localhost' with port '3306'.
  - Utilizes provided username and password for authentication.

- **Purpose**:
  - Enables Django to interact with the MySQL database for storing and retrieving data required by the web application.

### ❿ Now you can create apps within website

---
### 🥳 You have successfully set up a Django project on Windows

--- 
created by `team digipodium` with ❤️ & `python`
