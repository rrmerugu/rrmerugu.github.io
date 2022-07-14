---
title: "Automating python tasks with Celery"
tags: ["Celery", 'Python',]
categories: Code
date: 2018-02-14
---

The example will use mongodb as broker and  results backend  

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

app = Celery('tasks', broker='mongodb://127.0.0.1:27017/tasksdb', backend='mongodb://127.0.0.1:27017/tasksdb')


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
