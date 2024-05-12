# Ex.05 Design a Website for Server Side Processing
## Date:11/05/2006

## AIM:
To design a website to find surface area of a Right Cylinder in server side.

## FORMULA:
Surface Area = 2Πrh + 2Πr<sup>2</sup>
<br>r --> Radius of Right Cylinder
<br>h --> Height of Right Cylinder

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
math.html
<html>
<head>
<meta charset='utf-8'>
<meta http-equiv='X-UA-Compatible' content='IE=edge'>
<title>Area of Surface</title>
<meta name='viewport' content='width=device-width, initial-scale=1'>
<style type="text/css">
body {
    background-color: #82d3eef2;
}
.edge {
    width: 100%;
    padding-top: 180px;
    text-align: center;
}
.box {
    display: inline-block;
    border: thick dashed rgb(250, 230, 244);
    width: 500px;
    min-height: 300px;
    font-size: 20px;
    background-color: rgb(192, 230, 255);
}
.formelt {
    color: black;
    text-align: center;
    margin-top: 8px;
    margin-bottom: 6px;
}
h1 {
    color: black;
    padding-top: 20px;
}
</style>
</head>
<body>
<div class="edge">
    <div class="box">
        <h1>Surface Area of Right Cylinder</h1>
        <h3>AMEESHA JEFFI J(212223220007)</h3>
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Radius: <input type="text" name="radius" value="{{r}}"></input>m<br/>
            </div>
            <div class="formelt">
                Height: <input type="text" name="height" value="{{h}}"></input>m<br/>
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate"></input><br/>
            </div>
            <div class="formelt">
                Area: <input type="text" name="area" value="{{area}}">m<sup>2</sup><br/>
            </div>
        </form>
    </div>
</div>
</body>
</html>
```
```
views.py
from django.shortcuts import render
def surfacearea(request):
    context = {}
    context['area'] = "0"
    context['r'] = "0"
    context['h'] = "0"
    if request.method == 'POST':
        print("POST method is used")
        print('request.POST:', request.POST)
        r = request.POST.get('radius', '0') 
        h = request.POST.get('height', '0') 
        print('radius =', r)
        print('height =', h)
        area = 2 * 3.14 * int(r) * int(h) + 2*3.14*int(r)*int(r)
        context['area'] = area
        context['r'] = r
        context['h'] = h
        print('Area =', area)
    
    return render(request, 'mathapp/math.html',context)
```
```
urls.py

from django.contrib import admin
from django.urls import path
from mathapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('surfacearea/',views.surfacearea,name="surfacearea"),
    path('',views.surfacearea,name="surfcaearea")
]
```
## SERVER SIDE PROCESSING:

![328604720-150670aa-0158-4981-9eec-8e0364f42dd4](https://github.com/ameeshajeffi/MathServer/assets/150773598/c6790b9d-abcb-4b8d-9410-2f6fb469b256)

## HOMEPAGE:

![89112021-0426-4d03-b182-b1730ba23163](https://github.com/ameeshajeffi/MathServer/assets/150773598/609cdfb3-4339-4e17-9344-7912247a234d)


## RESULT:
The program for performing server side processing is completed successfully.
