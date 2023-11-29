
# Hosting on PythonAnywhere

This guide will walk you through the process of hosting the backend of the library management system on PythonAnywhere.

## Steps:

### 1. Create a PythonAnywhere Account

If you don't have a PythonAnywhere account, sign up for one at [PythonAnywhere](https://www.pythonanywhere.com/).

### 2. Set Up a New Web App

1. Log in to your PythonAnywhere account.

2. Go to the "Dashboard" and click on the "Web" tab.

3. Click on the "Add a new web app" button.

4. Choose "Manual Configuration."

5. Select the Python version you want to use (e.g., Python 3.8).

6. Choose the option to configure the web app manually.

7. Set the source code directory to your backend project directory.

8. Set the working directory to your backend project directory.

### 3. Install Dependencies

In the PythonAnywhere console, install the required dependencies:

```bash
pip install -r requirements.txt
```

### 4. Set Up Database

If you are using a database, migrate your database:

```bash
python manage.py migrate
```

### 5. Configure Web App

1. Go back to the "Web" tab on PythonAnywhere.

2. Find the section titled "Code" and update the "WSGI configuration file" to point to your `wsgi.py` file:

```bash
import os
import sys

path = '/path/to/your/project'
if path not in sys.path:
    sys.path.append(path)

from django.core.wsgi import get_wsgi_application
from django.contrib.staticfiles.handlers import StaticFilesHandler

os.environ.setdefault("DJANGO_SETTINGS_MODULE", "your_project.settings")

application = StaticFilesHandler(get_wsgi_application())
```

Replace `/path/to/your/project` with the actual path to your project on PythonAnywhere.

### 6. Reload the Web App

Go back to the "Web" tab on PythonAnywhere, find the section titled "General," and click on the "Reload" button to apply the changes.

### 7. Access Your App

Your backend should now be hosted on PythonAnywhere. Access it through the provided PythonAnywhere subdomain (e.g., `yourusername.pythonanywhere.com`).

## Note:

- Ensure your `SECRET_KEY` and sensitive information are kept secure.
