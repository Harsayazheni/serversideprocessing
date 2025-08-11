# Design a Website for Server Side Processing

## AIM:
To design a website to perform mathematical calculations in server side.

## DESIGN STEPS:
Step 1:
Create a new Django project using "django-admin startproject",get into the project terminal and use "python3 manage.py startapp" command.

Step 2:
Define urls.py and views.py for the website .Allow host access and add the app name under installed apps in settings.py

Step 3:
Create a templates folder under the app folder followed by a folder under templates with the app name followed by html file named perimeter.html

Step 4:
Write HTML and CSS code in the file save it and run the app using python manage.py makemigrations and python manage.py migrate commands .Run the Server using "python3 manage.py runserver 0:80" command.

STEP 5:-
The Website is published. Provide user inputs. The server processes the inputs in the terminal and provides output in the client side. The server side processing can be views in the terminal.

## PROGRAM
perimeter.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <title>PERIMETER OF RECTANGLE</title>
    <style>
        form {
            width: 500px;
            margin: 0 auto;
            background-color: white;
            border: 1px solid #ccc;
            border-radius: 5px;
            padding: 20px;
        }
        label {
            display: block;
            font-size: 16px;
            font-weight: bold;
            margin-bottom: 10px;
        }
        input[type="text"],
        input[type="number"] {
            width: 100%;
            padding: 12px 20px;
            margin-bottom: 20px;
            box-sizing: border-box;
            border: 1px solid #ccc;
            border-radius: 4px;
            resize: vertical;
        }
        input[type="submit"] {
            background-color: #FFA2A6;
            color: white;
            padding: 12px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            float: right;
        }
        input[type="submit"]:hover {
            background-color: #FFA2CD;
        }
        .container {
            border-radius: 5px;
            background-color: #f2f2f2;
            padding: 20px;
        }
        .perimeter {
            margin-bottom: 20px;
            color: purple;
            font-size: 20px;
            font-weight: bold;
        }
        h1 {
            text-align: center;
            font-size: 24px;
            color: black;
        }
        body { background-color: #FFD4A2; }
    </style>
</head>
<body>
    <h1>PERIMETER OF RECTANGLE</h1>
    <form method="POST" action="/perimeter/">
        {% csrf_token %}
        
        <label for="length">Enter Length</label>
        <input type="number" name="length" id="length" value="{{ length }}" step="any" required>
        
        <label for="width">Enter Width</label>
        <input type="number" name="width" id="width" value="{{ width }}" step="any" required>
        
        <input type="submit" value="Calculate Perimeter">
        
        <label for="perimeter">Perimeter</label>
        <input type="text" name="perimeter" id="perimeter" value="{{ perimeter }}" readonly>
    </form>
</body>
</html>

```


# Create your views here.
views.py
```
from django.shortcuts import render
def perimeter(request):
    context = {}
    context['length']="0"
    context['width']="0"
    context['perimeter']="0"

    if request.method == 'POST':
        print("POST METHOD IS USED")
        length=request.POST.get("length",0)
        width=request.POST.get("width",0)
        print('Length=',length)

        print('Width=',width)

        length_num = int(length)
        width_num = int(width)
        perimeter=2*(length_num+width_num)
        context['length']=length
        context['width']=width
        context['perimeter']=perimeter
        print('Perimeter=',perimeter)

    return render(request,"serverapp/perimeter.html",context)
```


## OUTPUT:
![WhatsApp Image 2023-01-27 at 11 09 24 PM (1)](https://user-images.githubusercontent.com/118708467/215157121-a45d50da-8468-4c9b-99a7-4a5f9c3aef8b.jpeg)

## Result:
Successfully designed a website to perform mathematical calculations in server side.

