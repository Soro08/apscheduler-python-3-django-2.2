# apscheduler-python-3-django-2.2
configuration django apscheduler

# Installation

```
pip install APScheduler
```
# Configuration


```
#yourproject/yourapp/autotask/tasks.py

def hello():
    print("hello world")

#yourproject/yourapp/autotask/updater.py


from apscheduler.schedulers.background import BackgroundScheduler
from .tasks import hello


def start():
    #intitialise
    scheduler = BackgroundScheduler()
    
    #Create jod
    scheduler.add_job(hello, 'interval', minutes=1) #this job is excecute every one minutes
    
    #start job
    scheduler.start()
    
    

#yourproject/yourapp/apps.py


from django.apps import AppConfig

class YourappConfig(AppConfig):
    name = 'yourapp'

    # new code for call apscheduler
    def ready(self):
        from .autotask import updater
        updater.start()
        
        
      
      
scheduler = BackgroundScheduler()
scheduler.add_job(quizz.submit_quizz, 'date', run_date=quizz.quizz.datetime_valide)
scheduler.start()


```
# test

```
python manage.py runserver

```



# SEND MAIL NAN API

```
def sendnanmail(fromemail, to, subject, message):
    url = 'https://nan.nan.ci/nanmail'
    try:

        messagehtml =  message 

        donner = {
            'subject':subject,
            'message':messagehtml,
            'to':to,
            'key':'NAN_MAIL_KEY'
        }
        req = requests.post(url, data = donner)
        if req.status_code == 200:
            return True
        else:
            return False
    except:
        return False
```
