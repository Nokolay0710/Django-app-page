1. https://github.com/Nokolay0710/Django-quick-start

2. py manage.py startapp newapp

3. config -> settings.py -> 
    INSTALLED_APPS = [
        'django.contrib.admin',
        'django.contrib.auth',
        'django.contrib.contenttypes',
        'django.contrib.sessions',
        'django.contrib.messages',
        'django.contrib.staticfiles',

        # Apps
        'newapp',
    ]

4. config -> urls.py ->
    from django.urls import include

    urlpatterns = [
        path('admin/', admin.site.urls),
        path('', include('newapp.urls')),
    ]

5. create urls.py to dir newapp
    from . import views
    from django.urls import re_path

    urlpatterns = [
        re_path(r'^$', views.index, name='index'),
    ]

6. newapp -> views.py ->
    from django.shortcuts import render

    def index(request):
        return render(request, 'index.html')

7. create dir templates to dir newapp

8. create index.html to dir templates
    <!-- templates/index.html -->
    <!DOCTYPE html>
    <html lang="en">
    <head>
    <meta charset="utf-8">
    {% block styles %}
    {% endblock %}
    <title>{% block title %}Django index.html{% endblock %}</title>
    </head>
    <body>
    <main>
        <h2>Hello index page!</h2>
    </main>
    </body>
    </html>

9. py manage.py migrate

10. py manage.py runserver

11. Starting development server at http://127.0.0.1:8000/

12. Hello index page!
