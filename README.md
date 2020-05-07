# django-sample
Simple repo for a demo Django app based on the django tutorial at https://docs.djangoproject.com/en/3.0/contents/

## How to Run

All commands listed below should be run in django-sample/mysite directory.

### Setup the database

This project uses a simple sqlite database. To initialise it just run the following command:

```
python manage.py migrate
```

### Run the server

Once you have setup the database simply run:
```
python manage.py runserver
```
to start the server. This will set up the server and start listening on 127.0.0.1:8000 for client connections.

### Create some polls/questions

You will be given an app that hosts a number of polls. You need to create these polls in the django environment. Use the followinf command to start the django shell:

```
python manage.py shell
```

Then run the following commands to create a poll with some questions:

```
from polls.models import Choice, Question
from django.utils import timezone

q = Question(question_text="What's new?", pub_date=timezone.now())
q.save()

q.choice_set.create(choice_text='Not much', votes=0)
q.choice_set.create(choice_text='The sky', votes=0)
q.choice_set.create(choice_text='Just hacking again', votes=0)
```

You can verify this worked by running the following command and verifying all of your choices are there:

```
q.choice_set.all()
```

If you navigate to http://127.0.0.1:8000/polls/ in your browser you will see a list with your new poll. Click on it to see your choices.

## Testing

Tests are located in tests.py files. To run all tests simply run

```
python manage.py test
```
