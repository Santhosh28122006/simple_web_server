# EX01 Developing a Simple Webserver

# Date:07.10.2024
# AIM:
To develop a simple webserver to serve html pages and display the configuration details of laptop.

# DESIGN STEPS:
## Step 1:
HTML content creation.

## Step 2:
Design of webserver workflow.

## Step 3:
Implementation using Python code.

## Step 4:
Serving the HTML pages.

## Step 5:
Testing the webserver.

# PROGRAM:
```

views.py

from django.shortcuts import render
from http.server import BaseHTTPRequestHandler, HTTPServer
from importlib.resources import contents
from django.http import HttpResponse

content='''<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Laptop Specifications</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: aquamarine;
          
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .specs-container {
            background-color:rgb(247, 243, 243);
            padding: 20px;
            border-radius: 10px;
            box-shadow: rgb(50, 162, 206);
            width: 500px;
        }
        h1 {
            text-align: center;
            color:rgb(29, 205, 245);
        }
        table {
            width: 100%;
            border-collapse: collapse;
        }
        th, td {
            padding: 10px;
            text-align: left;
            border-bottom: 1px solid rgb(243, 234, 234);
        }
        th {
            background-color: #b10f0f;
        }
    </style>
</head>
<body>
    <div class="specs-container">
        <h1>LAPTOP SPECIFICATION</h1>
        <table>
            <tr>
                <th>Specification:</th>
                <th>Details</th>
            </tr>
            <tr>
                <td>Brand:</td>
                <td>LENOVO</td>
            </tr>
            <tr>
                <td>Model:</td>
                <td>ThinkPad E16 Gen 1</td>
            </tr>
            <tr>
                <td>Processor:</td>
                <td>13th Gen Intel(R) Core(TM) i5-1335U   1.30 GHz</td>
            </tr>
            <tr>
                <td>RAM:</td>
                <td>16 GB </td>
            </tr>
            <tr>
                <td>Storage:</td>
                <td>520 SSD</td>
            </tr>
            <tr>
                <td>Graphics:</td>
                <td>NVIDIA GeForce GTX 1650</td>
            </tr>
            <tr>
                <td>Display:</td>
                <td>16inch Full HD(40.64)</td>
            </tr>
            <tr>
                <td>Battery Life:</td>
                <td>Up to 48 hours</td>
            </tr>
            <tr>
                <td>Operating System:</td>
                <td>Windows 11</td>
            </tr>
            <tr>
                <td>Price:</td>
                <td>₹52990 INR</td>
            </tr>
        </table>
    </div>
</body>
</html>'''
class Myserver(BaseHTTPRequestHandler):
    def do_GET(self):
        print("Get request received...")
        self.send_response(200)
        self.send_header("content-type","text/html")
        self.end_headers()
        self.wfile.write(content.encode())
print("This is my webserver")
server_address =('',8000)
Httpd = HTTPServer(server_address,Myserver)
Httpd.serve_forever() 



urls.py

from tempfile import template
from django.contrib import admin
from django.urls import path
from appp.views import Myserver

urlpatterns = [
    path('admin/', admin.site.urls),
    # path('new/',views.trail),
    # path('page/',views.slot),
    # path('home/',template.slot),
    path('server/',Myserver.as_view())
]

```
# OUTPUT:
![Screenshot 2024-12-07 114126](https://github.com/user-attachments/assets/2c5b3e75-0846-4c47-9753-8cc6b8a7c6cc)
![Screenshot 2024-12-07 114221](https://github.com/user-attachments/assets/bba93cc6-6aff-461b-b96d-f70c5e7ea160)

# RESULT:
The program for implementing simple webserver is executed successfully.
