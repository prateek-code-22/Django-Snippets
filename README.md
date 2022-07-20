# Basic Installation

## Install Virtual Environment
```
pip install virtualenv
```

## Create Virtual Environement name: "env"
```
virtualenv env
```

## Activate Virtual Environment
```
env\scripts\activate
```

## Install Django inside virtual env
 ```
 pip install django
 ```
 
## Start django project inside virtual env
 ```
 django-admin startproject Project_Name
 ```
 
## To run your project
```
 python manage.py runserver
```

Create Base app in project
```
python manage.py startapp base
```

# Database

## To saves changes done in model.py
```
python manage.py makemigrations
```

## To reflect the changes in database
```
python manage.py migrate
```

## To create super user for admin panel
```
python manage.py createsuperuser
```
## To register the model in admin
```
from .models import *
admin.site.register(ClassName)
```

# REST FRAMEWORK

## API decorator view serializer
```
@api_view(['GET'])
def home(request):
    return Response({'status':200, 
    'message':'Hello from rest'})
```

```
@api_view(['POST'])
def post_request(request):
    data = request.data
    print(data)
    return Response({'status':200 , 'payload':data, 'message':'data sent'})
```


## Serializer
```
class StudentSerializers(serializers.ModelSerializer):
    class Meta:
        model = Student
        #to serialize fiedls
        # fields = ['name','age']

        # to exclude field 
        # exclude = ['id']

        #to serialize all field
        field = '__all__'
```


##

