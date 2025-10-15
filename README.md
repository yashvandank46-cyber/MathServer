# Ex.05 Design a Website for Server Side Processing
## Date:02.10.2025

## AIM:
 To design a website to calculate the body mass Index(BMI) in the server side. 


## FORMULA:
BMI = W/H<sup>2</sup>
<br> BMI --> Body mass Index
<br> W --> Weight
<br> H --> Height

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
cyber.html

<html>

<head>
    <title>Body Mass Index</title>
    <style type="text/css">
        body {

            background-color: blue;
        }

        .edge {
            width: 1440px;
            margin-left: auto;
            margin-right: auto;
            padding-top: 250px;
            padding-left: 300px;
        }

        .box {
            display: block;
            border: grey;
            width: 1000px;
            min-height: 300px;
            font-size: 20px;
            background-color: red;
        }

        .formelt {
            color: cyan;
            text-align: center;
            margin-top: 7px;
            margin-bottom: 6px;
        }

        h1 {
            color: skyblue;
            text-align: center;
            padding-top: 20px;
        }
    </style>
</head>

<body>
    <h1 style="color:purple">
        YASHVANDAN K (25017523)</h1>
    <div class="edge">
        <div class="box">
            <h1>Body Mass Index</h1>
            <form method="POST">
                {% csrf_token %}
                <div class="formelt">
                    Weight: <input type="text" name="Weight" value="{{w}}"></input>(in kg)<br />
                </div>
                <div class="formelt">
                    Height: <input type="text" name="Height" value="{{h}}"></input>(in m)<br />
                </div>
                <div class="formelt">
                    <input type="submit" value="calculate"></input><br />
                </div>
                <div class="formelt">
                    BMI: <input type="text" name="BMI" value="{{bmi}}"></input>kg/m<sup>2</sup><br />
                </div>
            </form>
        </div>
    </div>
</body>

</html>
views.py

from django.shortcuts import render

def bmi(request):
    context = {}
    context['bmi'] = "0"
    context['w'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        w = request.POST.get('Weight','0')
        h = request.POST.get('Height','0')
        print('request=', request)
        print('Weight=', w)
        print('Height=', h)
        a=int(w)
        b=int(h)
        bmi=a/(b*b)
        context['bmi']=bmi
        context['w']=w
        context['h']=h
        print('BMI=',bmi)
    return render(request, 'myapp/cyber.html', context)

urls.py

from django.contrib import admin
from django.urls import path
from myapp import views
urlpatterns=[
    path('admin/', admin.site.urls),
    path('bodymassindex/', views.bmi, name="bodymassindex"),
    path('', views.bmi, name="bodymassindexroot")
]

```

## SERVER SIDE PROCESSING:
![alt text](<Screenshot 2025-10-02 141735.png>)

## HOMEPAGE:
![alt text](<Screenshot 2025-10-02 141432.png>)

## RESULT:
The program for performing server side processing is completed successfully.
