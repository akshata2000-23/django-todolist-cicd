# Django-Todolist

[![License][license-image]][license-url] [![Build Status][travis-image]][travis-url]

Django-Todolist is a todolist web application with the most basic features of most web apps, i.e. accounts/login, API and (somewhat) interactive UI.

---
CSS | [Skeleton](http://getskeleton.com/)
JS  | [jQuery](https://jquery.com/)

I've also build a quite similar app in Flask: https://github.com/rtzll/flask-todolist


## Explore
Try it out by installing the requirements. (Works only with python >= 3.8, due to Django 4)

    pip install -r requirements.txt

Migrate:

    python manage.py migrate

And then start the server (default: http://localhost:8000)

    python manage.py runserver


Now you can browse the [API](http://localhost:8000/api/)
or start on the [landing page](http://localhost:8000/)


[license-url]: https://github.com/rtzll/django-todolist/blob/master/LICENSE
[license-image]: https://img.shields.io/badge/license-MIT-blue.svg?style=flat

[travis-url]: https://travis-ci.org/rtzll/django-todolist
[travis-image]: https://travis-ci.org/rtzll/django-todolist.svg?branch=master


-----------------------------------------------------------------------------------------------------------------------------------
**Now lets dockerize the application:**
Step 1: Create a docker image

        docker build -t image_name:tag_name .
This creates a docker image. Verify the image by entering: docker images

Step 2: Run the container using the image created.

        docker run -d -p 8000:8000 --name container_name image_name:tag_name

This creates and starts the container. If you are running this in an EC2 then go to security groups and enable port 8000 in inbound rules.
Also add the IP address of EC2 in todolist/settings.py ALLOWED_HOST=['http://ip_addr']

Verify the site by entering the HTTP://ip_addr:8000


-------------------------------------------------------------------------------------------------------------------------------------------

**Now lets create a CI CD Pipeline which fetched the code from git repo and builds and runs the image in a container automatically**

**Installation of Jenkins on VM**

Run the command:

        docker pull jenkins/jenkins

We are installing jenkins through docker. Next step is running the container

        docker run -d -p 8080:8080 jenkins/jenkins 
This will create a container of Jenkins. So now check the url of the VM : HTTP://ip_addr:8080. Allow access to port 8080 in inbound rules section.
You will see Jenkins page, you will have to enter the password, to find the password enter the following command:

        docker logs container_id ## do docker ps to find container_id

After entering password you will see following page:
![image](https://github.com/akshata2000-23/django-todolist-cicd/assets/70626299/b81a9291-fa51-4d7f-96af-d08f096fd298)






