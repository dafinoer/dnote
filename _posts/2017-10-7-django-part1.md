---
layout: post
title:  "django part 1"
tags:
- Django
- Python
- Code
- Blog
---
<img src="https://media.licdn.com/media/AAEAAQAAAAAAAAl0AAAAJDBhYTEyMTI0LWQ2ODMtNGVmZi04NGEwLWRhYjdiYzcwNjRhNw.png" alt="">
## Apa itu Django ?
Django adalah sebuah web framework yang ditulis menggunakan Python. Web Framwork adalah sebuah software yang membantu kita dalam membuat dynamic web, aplikasi dan service.<!–-break-–> Pada web framework banyak tools yang bisa digunakan untuk menyelesaikan beragam masalah pada saat membangun Web, seperti fitur security, akses database, session dan template, routing sebuah url dll.

Salah satu framework seperti Django yang memungkinkan kita membuat sebuah aplikasi web yang secure dan dapat diandalkan. Pada situs web [Django](https://www.djangoproject.com/) mereka menawarkan sebuah keunggulan antara lain:
1. Cepat
Django sangat simple dan membantu developer cepat dalam mengembangkan aplikasi
2. Secure
Django dibangun 12 tahun lebih, dan web framework in sangat serius untuk masalah security
3. Scalable
Terbukti dipakai diantara web yang sibuk seperti Instagram dan Pinterest.

## Benefit Spesial
Jadi ketika saya menggunakan Django apa benefit spesialnya ? jika kamu seorang developer awal python maka nanti akan banyak library yang bisa digunakan diluar sana. Pada bulan ini tersedia 118994 package yang bisa diliat [Python Package Index](https://pypi.python.org/pypi). Jadi kalau kalian butuh sebuah solve problem, mungkin package tersebut bisa membantu kalian.

## Project
untuk awal kita membuat project maka, kita perlu running script di command line dibawah ini:
~~~
django-admin startprojects movies
~~~

Pada scripts diatas `movies` itu adalah sebuah nama project, kalian bisa bebas menentukan namanya sesuai project yang ingin kalian buat. Command Line `django-admin` itu otomatis terinstall di django.

Pada saat kita sudah merunning script di atas di Command Line kita, maka akan mengenerate sebuah structure folder Django Project

```
movie
 |--movie/
 |    |--movie/
 |       |--__init__.py
 |       |-- settings.py
 |       |-- urls.py
 |       |-- wsgi.py
 |    +--manage.py
 +--venv/

```

1. __manage.py__ adalah digunakan untuk memanagement sebuah perintah yang berhubungan dengan project kita. Nantinya kita akan menggunakan ini untuk membangun sebuah server, run test, create migrations dan masih banyak lagi.
2. __init.py__ adalah sebuah package python
3. __setting.py__ file yang berisi semua configuration project kita.
4. __urls.py__ file yang bertanggung jawab pada semua mapping route yang ada di project kita. contohnya gini, misalnya agan mau ke sebuah url `/about/`, maka agan perlu memetakannya di file ini.
5. __wsgi.py__ file simple gateway interface yang digunakan untuk deployment.

Django hadir simple web server installed yang kalau memudahkan selama mengembangkan, kalau kita tidak menginstall apapun di project local km tentu masih bisa menjalankan command `python manage.py runserver`.

Setelah menjalankan script yang tadi maka kemudian buka browser ketik `http://127.0.0.1:8000/`.

![400x200](https://simpleisbetterthancomplex.com/media/series/beginners-guide/1.11/part-1/it-worked.png "Medium example image")

## Django Apps
Framework Django mempunyai beberapa konsep:

1.__app.py__ web aplikasi yang melakukan sesuatu. biasanya susunannya yaitu models(database table), views, templates, test
2.__project__ kumpulan konfigurasi dan apps. satu project bisa terdiri dari multiple app atau singel apps

jadi penerapan filosofi ini sangat penting gan, ente nggak bisa jalanin apps tanpa sebuah project

Kita ilustrasikan untuk membuat apps movies. Untuk membuat apps, silahkan kalian ke directory dimana tempat project yg kita buat tadi, didalam sebuah project maka akan ada sebuah file __manage.py__. kemudian cara execute codenya yaitu:

`django-admin startapp movies`

atau bisa juga

`python manage.py startapp movies`

Dibawah ini adalah bentuk structure dari sebuah apps yang kita buat tadi:

<img src="static/img/str.png" alt="Test Image" style="width:500px;height:250px "/>

1. __migrations__ disini Django menyimpan file yang memantau perubahan yang terjadi pada __models.py__ file.
2. __admin.py__ digunakan untuk konfigurasi file apps di django admin.
3. __apps.py__ konfigurasi untuk apps itu sendiri.
4. __models.py__ disini kita membuat entitas untuk web aplikasi kita, dan di model ini. nantinya django akan mentranslate secara otomatis ke database table.
5. __tests.py__ untuk unit test di apps.
6. __views.py__ di file ini untuk menghandle sebuah request dan respone di web aplikasi kita.

dan setelah kita membuat sebuah app maka setelah itu kita harus mensettingnya di file
`setting.py`

ketika kita membuat app maka kita perlu menambahkan nama appnya ke dalam sebuah `INSTALLED_APPS` contohnya seperti berikut:

```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    'movies'
]
```

## Hello world

mari kita lakukan ini di views. maka pertama2 buka dulu directory app kalian lalu kemudian pilih file `views.py`

__views.py__
```
from django.http import  HttpResponse

def hello_world(request):
    return HttpResponse("hello world")
```
views di python function itu menerima sebuah httprequest dan kemudia kita merespone menggunakan http respone, request adalah parameter, dan respone adalah hasilnya.

setelah itu kita perlu mapping url di `urls.py`

```
from django.conf.urls import url
from django.contrib import admin
from movies import views

urlpatterns = [
    url(r'^admin/', admin.site.urls),
    url(r'^hello/$', views.hello_world, name='hello')
]
```

django menggunakan regex untuk mencocokan pola request URL. saya menggunakan regex `'^hello/$'` yang mana nantinya urlnya adalah `(http://localhost:8000/hello/)`

untuk melihat hasilnya maka kita perlu menjalankan

`python manage.py runserver`

<img src="static/img/gb.png" alt="Test Image" style="width:750px;height:500px "/>
