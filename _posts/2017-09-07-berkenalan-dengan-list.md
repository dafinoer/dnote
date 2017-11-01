---
layout: post
title:  "Berkenalan Dengan List"
tags:
- python
- code
---
kalau kita bicara array pasti yg kita ingat itu tanda `[]`, nah di python sebuah list itu serupa kayak array. Ketika kalian menggunakan list di python, maka kalian
bisa mengisinya dengan semua jenis type variable, ga cuma itu kalian bisa melakukan sebuah iterasi pada list ini.
<!–-break-–>
disini ane coba kasih contoh buat list
~~~python
lst = []
lst.append(1)
lst.append(2)
lst.append(3)

prints(lst)
~~~
hasilnya adalah `[1, 2, 3]`, karena pada method append kita memasukan angka(add) kedala list. gimana kalau mau ambil bedasarkan index ? pertama kita
udh punya data list yang di atas, maka contoh ambil bedasarkan index itu ini ane kasih contohnya:

~~~python
a = lst[1]
print (a)
~~~

pada object `A` ane panggil list bedasarkan index pertama yang ane tulis pake `lst[1]` yang artinya. `oi list tolong ambil donk deretan di dalam diri ente yang no 1` dan dia keluarin angka `2` karena si list ini menghitungnya dari angka 0.

Ahh capek klo mau nambahin ke list ketik append berkali kali, gimana caranya masukin list datanya tanpa tulis berkali2, oke kita bicara soal looping.

nantikan post tentang looping :)


salam .....
