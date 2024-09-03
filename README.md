# Create Virtual Environment
python3 -m venv venv

cd venv

source venv/bin/activate

# Start Project:
django-admin startproject project_name

# install all requirenments
pip install -r requirenmnets.txt


# Google SSO

    1. singin gmail
    2. go to https://console.cloud.google.com/
    3. Create a project
    4. Again go to Crentials select Application type.   
        add Authorized redirect URIs http://localhost:8000/admin/login
    5. Click on Generate it will create the cdedentials

# Configure
    1. Add in settings.py

        INSTALLED_APPS = [
        # other django apps
        "django.contrib.messages",
        "django_google_sso"
    ]

    GOOGLE_SSO_CLIENT_ID = "your client id here"
    GOOGLE_SSO_PROJECT_ID = "your project id here"
    GOOGLE_SSO_CLIENT_SECRET = "your client secret here"    

    GOOGLE_SSO_ALLOWABLE_DOMAINS = ["gmail.com"]

    2. Add in urls.py

        path(
        "google_sso/", include("django_google_sso.urls", namespace="django_google_sso")
    ),

    3. python manage.py migrate
