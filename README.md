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

## Save json data to model using POST
```
@api_view(['POST'])
def post_request(request):
    data = request.data
    serializer = StudentSerializers(data = request.data)

    if not serializer.is_valid():
        return Response({'status':403,'message':'Something went wrong!', 'errors':serializer.errors})
    
    serializer.save()

    return Response({'status':200 , 'payload':serializer.data, 'message':'data sent'})
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


## User validation 
```
def validate(self,data):
        
        if data['age'] < 18:
            raise serializers.ValidationError({'error':"age cannot be less than 18"})
        
        if not data['name'].isalpha():
            raise serializers.ValidationError({'error': 'name cannot contain digits'})

        return data
```



