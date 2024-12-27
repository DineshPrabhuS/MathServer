# Ex.05 Design a Website for Server Side Processing
## Date:21.12.2024

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

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

**math.html**
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Power of a Bulb</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 20px;
        }
        h1 {
            text-align: center;
            color: #333;
        }
        .container {
            max-width: 400px;
            margin: 0 auto;
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
        }
        .formelt {
            margin: 15px 0;
        }
        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }
        input[type="text"] {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
            box-sizing: border-box;
        }
        input[type="submit"] {
            background-color: #28a745;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
            margin-top: 10px;
        }
        input[type="submit"]:hover {
            background-color: #218838;
        }
        .result {
            margin-top: 20px;
            padding: 10px;
            background-color: #e9ecef;
            border-radius: 4px;
            text-align: center;
            font-size: 1.2em;
            color: #333;
        }
    </style>
</head>
<body>

<div class="container">
    <h1>POWER OF A BULB</h1>
    <form method="POST">
        {% csrf_token %}
        <div class="formelt">
            <label for="intensity"><b>INTENSITY:</b></label>
            <input type="text" id="intensity" name="intensity" value="{{ i }}" required>
        </div>
        <div class="formelt">
            <label for="resistance"><b>RESISTANCE:</b></label>
            <input type="text" id="resistance" name="resistance" value="{{ r }}" required>
        </div>
        <input type="submit" value="COMPUTE">
        <div class="result">
            <label><b>POWER:</b></label>
            <input type="text" name="POWER" value="{{ power }}" readonly>
        </div>
    </form>
</div>

</body>
</html>
```

**views.py**
```
from django.shortcuts import render 
def powerofabulb(request): 
    context={} 
    context['power'] = "0" 
    context['i'] = "0" 
    context['r'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        i = request.POST.get('intensity','0')
        r = request.POST.get('resistance','0')
        print('request=',request) 
        print('intensity=',i) 
        print('resistance=',r) 
        power = (int(i)**2)*int(r) 
        context['power'] = power 
        context['i'] = i
        context['r'] = r 
        print('power=',power) 
    return render(request,'mathapp/math.html',context)

```

**urls.py**
```
from django.contrib import admin 
from django.urls import path 
from mathapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('powerofabulb/',views.powerofabulb,name="powerofabulb"),
    path('',views.powerofabulb,name="powerofabulbroot")]
```


## SERVER SIDE PROCESSING:

![alt text](<Screenshot (173).png>)

![alt text](<Screenshot (174).png>)

## HOMEPAGE:

![alt text](<Screenshot (175).png>)

## OUTPUT:

![alt text](<Screenshot (198).png>)

## RESULT:
The program for performing server side processing is completed successfully.
