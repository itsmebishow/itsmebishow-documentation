![Django, RabbitMQ & Celery](https://miro.medium.com/v2/resize:fit:1000/1*SbHHsp_llrgXtqNYCTtdzg.png)

>

Yes, you can definitely use RabbitMQ and Celery together without Redis or any other additional message broker. RabbitMQ is a powerful message broker that works seamlessly with Celery.

> What is pyamqp. Do i need to install it ?

The pyamqp in the Celery configuration URL (pyamqp://...) refers to the protocol used by Celery to communicate with message brokers that support the Advanced Message Queuing Protocol (AMQP). AMQP is a messaging standard that allows applications to communicate with each other via message queues.

pyamqp is actually a library that Celery uses to handle the AMQP protocol. It's part of the Celery dependencies, and you don't need to install it separately. When you install Celery using pip install celery, it automatically installs the required dependencies, including pyamqp.

So, in your Celery configuration, when you see pyamqp://..., it specifies the use of the AMQP protocol for communication between Celery and the RabbitMQ message broker. The pyamqp library is included with Celery, and you don't need to explicitly install it.

Here are the steps to use RabbitMQ and Celery:

## Step 1: Install Celery and RabbitMQ

```py
pip install celery
```

Install RabbitMQ by following the instructions on the official RabbitMQ website: RabbitMQ Installation Guide

## Step 2: Configure Django Settings

In your Django project's settings.py, configure Celery to use RabbitMQ:

```py
# settings.py

# Celery configuration
# CELERY_BROKER_URL = 'pyamqp://guest:guest@localhost//'  # Replace with your RabbitMQ URL
# using rabbit mq URL
CELERY_BROKER_URL = 'pyamqp://guest:guest@localhost:5672/#/'
CELERY_RESULT_BACKEND = 'rpc://'
CELERY_ACCEPT_CONTENT = ['json']
CELERY_TASK_SERIALIZER = 'json'
CELERY_RESULT_SERIALIZER = 'json'
CELERY_TIMEZONE = 'UTC'
```

Replace the `CELERY_BROKER_URL` with your RabbitMQ connection details.

## Step 3: Create a Celery Instance

Create a file named `celery.py` in your Django project directory:

```py
# celery.py

from __future__ import absolute_import, unicode_literals
import os
from celery import Celery

# Set the default Django settings module for the 'celery' program.
os.environ.setdefault('DJANGO_SETTINGS_MODULE', 'your_project.settings')

# Create a Celery instance and configure it using the settings from Django.
app = Celery('your_project')

# Load task modules from all registered Django app configs.
app.config_from_object('django.conf:settings', namespace='CELERY')

# Auto-discover tasks in all installed apps
app.autodiscover_tasks()
```

## Step 4: Create Celery Tasks

Create a `tasks.py` file in one of your Django apps and define the tasks you want to execute asynchronously.

```py
# your_app/tasks.py

from celery import shared_task
from time import sleep

@shared_task
def example_task(seconds):
    sleep(seconds)
    return f'Task completed after {seconds} seconds'
```

## Step 5: Use Celery in Django Views or Models (ADDITIONAL)

Now, you can use the Celery task in your Django views, models, or other parts of your application

```py
# views.py

from django.shortcuts import render
from your_app.tasks import example_task

def my_view(request):
    # Trigger the Celery task
    result = example_task.delay(10)  # Run the task asynchronously

    return render(request, 'your_template.html', {'result_id': result.id})
```

## Step 6: Run Celery Worker

Open a terminal and run the Celery worker:

```py
celery -A your_project worker -l info
```

## Step 7: Start Django Development Server (ADDITIONAL)

Run your Django development server:

```
python manage.py runserver
```

Now, when you access the view that triggers the Celery task, the task will be processed by the Celery worker in the background.

Remember to refer to the official documentation for Celery (https://docs.celeryproject.org/) for more advanced configurations and options.

> NOTES

Replace `your_project` with the actual name of your Django project.

Now, you can use Celery as described in your Django views, models, or other parts of your application. Tasks will be processed by the Celery worker, and messages will be exchanged through RabbitMQ.

Remember to refer to the official documentation for Celery and RabbitMQ for more advanced configurations and options:

- Celery Documentation
- RabbitMQ Documentation

---

- [Building Scalable Applications with Django, Celery, and RabbitMQ](https://awstip.com/building-scalable-applications-with-django-celery-and-rabbitmq-1a7c5c375e23)
