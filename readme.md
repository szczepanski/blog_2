
# the code bit

```

# python pre-reqs 
pip3.8 install Django
pip3.8 install pillow


# create blank new repo on github
szczepanski/blog


# initial django setup 
django-admin startproject blog_core
mv blog_core blog_2
cd blog_2
git init
git remote add origin https://github.com/szczepanski/blog_2.git
git add -A
git commit -m 'new repo init'
git push -u origin master

git branch feature1
git checkout feature1
python3.8 manage.py makemigrations
python3.8 manage.py migrate
git add -A
git commit -m 'applied first db migrations'
git push origin feature1




# init first two apps 
python3.8 manage.py startapp app_blog
python3.8 manage.py startapp app_projects


# add new apps to blog_core/settings.py --> INSTALLED_APPS
'app_blog',
'app_projects',


# check the server
python3.8 manage.py runserver


# migrations - db model changes
# discover new migrations / db model changes (models.py)
python3.8 manage.py makemigrations
# apply the discovered migrations
python3.8 manage.py migrate


# define app gui admin credentials
python3.8 manage.py createsuperuser
# provide username and password, email - optional 
# if needed in future, change password for any admin user
python3.8 manage.py changepassword <username>


# register models to show in admin web gui 
# blog/app_projects/admin.py

# online viewer to see db.sqlite3 file (if no confidential data involved)
http://inloop.github.io/sqlite-viewer/


```

# improvements and fixes

- improvements
    - try other fonts from goole.fonts
    - add details page for projects 
    - change int to slug for human readable urls
        - path('<int:post_id>/', views.detail, name='detail')
    check 'app_blog:path to a file' functionality
    - make function to write posts in .md or .rst

- fixes
    - statc media works ok, but still errors 
    ```
    "GET / HTTP/1.1" 200 4317
    "GET /media/app_projects/images/logo_cloud.png HTTP/1.1" 304 0
    "GET /blog/ HTTP/1.1" 200 4443
    "GET /static/app_proj_static_media/custom.css HTTP/1.1" 304 0
    ```