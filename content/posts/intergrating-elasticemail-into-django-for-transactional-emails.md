---
layout: post
title: Integrating elasticemail.com into django project for transactional emails.
categories: elasticemail
date: 2017-01-23
---


[Elastiemail](https://www.elasticemail.com) as the website says is a email delivery tools provider,
 you can send transactional as well as promotional emails.

I've written a `EMAILBACKEND` class that allows you to send emails in django project using elasticemail.com


<!--/excerpt-->

Here is how to use it.


 1. Install the package via git `git install -e git+https://github.com/rrmerugu/django_elasticemail`

2. Add `django_elasticemail` to `INSTALLED_APPS`

3. In `settings.py` add `EMAIL_BACKEND = "django_elasticemail.mail.ElasticEmailBackend"`


## Usage


```python
from django.core.mail import EmailMultiAlternatives


email_message = EmailMultiAlternatives(subject=None, body=None,
                            from_email='xxx@gmail.com',  to=['yy@gmail.com', 'zz@outlook.com'])
email_message.template = 'template-name' # template with this name should be created in your elasticemail.com account
email_message.merge_vars = {
    'text': 'Hello World',
}
email_message.send()

```

Try it out. All the very best :)
