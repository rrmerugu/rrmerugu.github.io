---
layout: post
title: Django - why ajax for pages ? we have Pjax
categories: django
date: 2017-02-25
---


Pjax(https://github.com/defunkt/jquery-pjax) is a jQuery plugin a standalone JavaScript module
that uses ajax (XmlHttpRequest) and pushState() to deliver a fast browsing experience.

Typically django serves each page with a entire page reload, costing performance. Using Pjax, its we convert our
 django application into a light weight server rendered SPA :) , Lets know how awesome is that..


<!--/excerpt-->

Here is how to use it and code is hosted at [https://github.com/rrmerugu/django-pjaxified](https://github.com/rrmerugu/django-pjaxified).


1. Step1: Fork and Clone  the repo `git clone https://github.com/rrmerugu/django-pjaxified`

2. Step2: Create virtualenv `virtualenv venv`

3. Step3: Activate the `venv` and install the necessary packages
 using `source venv/bin/activate && pip install -r requirements.txt`

4. Step4: start the server :D, all the configs are already added into the `settings`. Just start the server  with
`python manage.py runserver`

5. Check the `djangoajax/settings.py` for the `pjax` settings. there are only 3 settings needed . Check
[https://github.com/nigma/django-easy-pjax](https://github.com/nigma/django-easy-pjax) for settings and implementation
doc.

6. `website/templates/base.html` contains the `js` libraries and code needed to activate the pjax on page :) .


7. In the `url/route of django view` while extending the `base.html` instead of ```{ % extend s "base.html" % }``` use
```{ % extend s "base.html"|pjax:request % }``` and place the `{ % block content % }` of `base.html` in a div container with
id specified in `base.html` which is `pjax-container` in our case.


Try it out, and let me know :)
