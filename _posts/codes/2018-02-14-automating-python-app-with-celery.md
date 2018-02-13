---
layout: post
title: "Automating python tasks with Celery"
category: Post
skills: ["Celery", 'Python',]
---


```python
"""
# tasks.py

http://docs.celeryproject.org/en/latest/getting-started/first-steps-with-celery.html
http://docs.celeryproject.org/en/latest/getting-started/next-steps.html#project-layout

http://docs.celeryproject.org/en/latest/userguide/periodic-tasks.html?highlight=add_periodic_task



celery -A tasks worker --loglevel=info
&
python tasks.py # executes the add.delay() things


# runs the periodic tasks
celery worker -l info -A tasks --beat

"""

from celery import Celery
from celery.schedules import crontab
from celery.task import periodic_task
from datetime import timedelta
from random import randint

app = Celery('tasks', broker='redis://localhost:6379')

app.conf.beat_schedule = {
    # Executes every Monday morning at 1:00 a.m.
    'add-every-monday-morning': {
        'task': 'tasks.add',
        'schedule': crontab(hour=1, minute=00, day_of_week=1),
    },
}


@app.task
def add(x, y):
    z = x + y
    print("z is {}".format(z))
    return x + y


@periodic_task(run_every=timedelta(seconds=2))
def periodic_task_example():
    add.delay(randint(22, 55), randint(445, 56666))


if __name__ == "__main__":
    add.delay(4, 4)
    add.delay(2, 5)
    add.delay(1000, 7)
    add.delay(4123, 41231)

```
