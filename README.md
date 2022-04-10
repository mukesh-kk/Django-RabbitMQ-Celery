# Geographical-Vector

## Validation:

Object-level validation
Sometimes you'll have to compare fields with one another in order to validate them. This is when you should use the object-level validation approach.

Example:


    from rest_framework import serializers
    from examples.models import Movie


    class MovieSerializer(serializers.ModelSerializer):
        class Meta:
            model = Movie
            fields = '__all__'
            
    def validate(self, data):
        if data['us_gross'] > data['worldwide_gross']:
            raise serializers.ValidationError('worldwide_gross cannot be bigger than us_gross')
        return data

## Installation:

### Recommendation:

#### Setup virtual environment

### RabbitMQ Installation:

#### `apt-get install -y erlang`

#### `apt-get install rabbitmq-server`

#### `systemctl enable rabbitmq-server`

#### `systemctl start rabbitmq-server`

### How to run :

##### i) `pip install -r requirements.txt`

##### ii) Database Configuration
###### a) Create a SQL database
###### Reference: https://dev.mysql.com/
###### b) Open setting.py 
###### Path: vector/filled/setting.py
###### b) Add SQL database details

 ```
 DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql', 
        'NAME': 'DB_NAME',
        'USER': 'DB_USER',
        'PASSWORD': 'DB_PASSWORD',
        'HOST': 'localhost',   # Or an IP Address that your DB is hosted on
        'PORT': '3306',
    }
}
```

##### ii) `python manage.py makemigrations`

##### iii) `python manage.py migrate`

##### iv) `python manage.py runserver`

##### v) `Open: http://127.0.0.1:8000/ `

#### Check the status to make sure everything is running smooth:

#### `systemctl status rabbitmq-server`

#### Starting The Worker Process

#### `celery -A vector worker -l info`

#### Reference : https://www.designmycodes.com/python/use-celery-with-django.html
