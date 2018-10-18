### Teori
## Ikhtisar
Di bagian ketiga ini (terakhir) akan dibahas tentang konsep dari framework data engineering dan membedah pola desain untuk membangung framework tersebut, kemudian akan fokus ke beberapa contoh spesifik yang sering digunakan oleh AriBnb, yang bertujuan agar pembaca dapat mengembangkan sendiri untuk abstraksi framework.
## Skenario Umum
1. data modeling and schema design
2. identify relevant fact and dimension tables
3. joining the tables to create a final denormalized table
4. backfill all the historical data
Meski melakukan tahap-tahap diatas sangat bermanfaat, namun melakukan pekerjaan seperti itu dirasa repetitive (berulang-ulang) dan nyatanya pekerjaan ini sudah dilakukan sehari-hari oleh data scientist. Sedangkan, alur kerja ini dapat diotomasikan (setidaknya sebagian).
## From Pipelines To Frameworks
Seperti yang telah dibahas pada bagian 2, DAG milik Airflow bisa jadi sangat kompleks, terkadang, komputasi data bahkan mengikuti aliran kontrol seperti logika. Sebagai contohnya :
1. Untuk membuat percabangan aliran data dapat menggunakan BranchPythonOperator
2. Jika alur kerja dapat berlanjut hanya jika suatu kondisi terpenuhi dapat menggunakan ShortCircuitOpeartor
Operator-operator tersebut, dikombinasikan dengan prinsip configuration as code agar ETL Airflow lebih serba guna dan fleksibel.

Sejauh ini, pembahasan terbatas pada desain single, standalone, pipeline, namun kita dapat menerapkan prinsip yang sama untuk pembuatan pipeline generation adalah sebuah cara untuk menghasilkan GAD secara terprogram dan secara dinamis dengan cepat. Pada dasarnya, inilah yang dikerjakan oleh framework data engineering (menghasilkan instansiasi yang berbeda dari DAG milik Airflow dan mengotomatisasi alur kerja data), sebagaimana yang dikatakan oleh Maxime (pembuat Airflow) :
To build workflows dynamically from code ... A very simple example would be an Airflow script that reads a YAML config file with a list of table names, and creates a little workflow for each table, that may do things like loading the table into a target database, perhaps apply rules from the config file around sampling, data retention, anonymization … Now you have this abstraction … you can create new chunks of workflows without doing much work. It turns out there are tons of use cases for this type of approach.

Tools tersebut sangatlah penting bagi data scientist untuk meningkatkan data value chain[1] lebih cepat.

Implikasi dari kerangka kerja ini sangatlah dalam karena secara drastis meningkatkan cara kerja data scientist. Ini adalah teknologi yang memungkinkan para data scientist untuk memberikan value at scale.
## Pola Desain untuk Framework Data Engineering
1. Incremental Computation Framework
2. Backfill Framework
3. Global Metrics Framework
4. Experimentation Reporting Framework
Kesimpulan
Footnote
value chain

### Praktik
 ## Brief Tour of the Standard Library
 Tur singkat untuk Pustaka Standar Python
 ## Operating System Interface
 Modul os menyediakan lusinan fungsi untuk berinteraksi dengan sistem operasi:

import os
print(os.getcwd()) # Return the current working directory
os.chdir('/home/ayam/Code/bigdata') # Change current working directory
print(os.system('mkdir today')) # Run the command mkdir in the system shell
kode diatas akan mengubah working directory kemudian akan membuat folder bernama "today"

/home/ayam/Code/bigdata
0
Perhatian : gunakan import os jangan from os import * karena akan membuat shadowing os.open() pada fungsi built-in open() dan itu penggunaannya akan jauh berbeda.

Fungsi built-in dir() dan help() berguna sekali untuk bekerja dengan module yang besar seperti os :

print(dir(os)) # <returns a list of all module functions>
print(help(os)) # <returns an extensive manual page created from the module's docstrings>
Untuk mengoperasikan tugas-tugas manajemen berkas, dapat menggunakan module shutil yang menyediakan high-level interface dan mudah untuk digunakan, contoh :

import shutil
shutil.copyfile('data.db', 'archive.db')
shutil.move('/today', 'also-today')

##  File Wildcards
Modul glob menyediakan fungsi untuk membuat daftar file dari pencarian direktori wildcard:

import glob
print(glob.glob('*.py'))
##  Command Line Arguments
Untuk membaca argumen pada command-line yang dijalakan dapat menggunakan module sys

import sys
print(sys.argv)
jalankan kode diatas dengan cara :

$ python minggu-05/praktik/src/10_3-command-line-arguments.py satu dua tiga empat
maka akan menampilkan

['minggu-05/praktik/src/10_3-command-line-arguments.py', 'satu', 'dua', 'tiga', 'empat']
untuk pemrosesan command-line akan lebih powerfull dan fleksibel jika menggunakan module getopt yang disediakan oleh module argparse.
## Error Output Redirection and Program Termination
Modul sys juga memiliki atribut untuk stdin, stdout, dan stderr. stderr digunakan untuk menampilkan pesan kesalahan.

print(sys.stderr.write('Warning, log file not found starting a new one\n'))
jika dijalankan akan menampilkan

Warning, log file not found starting a new one
47
##  String Pattern Matching
Untuk pencocokan dan manipulasi yang kompleks terhadap string, regular expresion (Regex) menawarkan solusi yang ringkas dan optimal:

import re
print(re.findall(r'\bf[a-z]*', 'which foot or hand fell fastest'))
print(re.sub(r'(\b[a-z]+) \1', r'\1', 'cat in the the hat'))
akan menampilkan

['foot', 'fell', 'fastest']
cat in the hat
jika hanya pencocokan dengan string yang sederhana, method string lebih singkat dan mudah

print('tea for too'.replace('too', 'two'))
"""Output
tea for two
"""
## Mathematics
Modul math memberikan akses ke fungsi pustaka C yang mendasari untuk operasi floating point:

import math
print(math.cos(math.pi / 4))
print(math.log(1024, 2))

"""Output
0.7071067811865476
10.0
"""
Modul random menyediakan alat untuk membuat pilihan secara acak:

import random
print(random.choice(['apple', 'pear', 'banana']))
print(random.sample(range(100), 10)) # sampling without replacement
print(random.random()) # random float
print(random.randrange(6)) # random integer chosen from range(6)

"""Output
'apple'
[30, 83, 16, 4, 8, 81, 41, 50, 18, 33]
0.17970987693706186
"""
Modul statistics untuk keperluan menghitung statistika dasar seperti: mean, median, varians, dll. Dari data numerik:

import statistics
data = [2.75, 1.75, 1.25, 0.25, 0.5, 1.25, 3.5]
print(statistics.mean(data))
print(statistics.median(data))
print(statistics.variance(data))

"""Output
1.6071428571428572
1.25
1.3720238095238095
"""
Proyek SciPy mempunyai lebih banyak module untuk komputasi numerik.
## Internet Access
Ada sejumlah modul untuk dapat mengakses internet dan memproses protokol internet. Dua yang paling sederhana adalah urllib.request untuk mengambil data dari URL dan smtplib untuk mengirim email:

from urllib.request import urlopen
with urlopen('https://tycho.usno.navy.mil/cgi-bin/timer.pl') as response:
    for line in response:
        line = line.decode('utf-8')  # Decoding the binary data to text.
        if 'EST' in line or 'EDT' in line:  # look for Eastern Time
            print(line)


import smtplib
server = smtplib.SMTP('localhost')
server.sendmail('soothsayer@example.org', 'jcaesar@example.org',
"""To: jcaesar@example.org
From: soothsayer@example.org

Beware the Ides of March.
""")
server.quit()

"""Output
<BR>Oct. 04, 09:26:26 UTC
"""
Contoh pengiriman email dengan smptplib, membutuhakn mail server dari localhost
  ## Dates and Times
  Modul datetime menyediakan kelas-kelas untuk memanipulasi tanggal dan waktu dengan cara yang sederhana maupun yang rumit.

# dates are easily constructed and formatted
from datetime import date
now = date.today()
print(now)
print(now.strftime("%m-%d-%y. %d %b %Y is a %A on the %d day of %B."))

# dates support calendar arithmetic
birthday = date(1995, 12, 4)
age = now - birthday
print(age.days)

"""Output
2018-10-04
10-04-18. 04 Oct 2018 is a Thursday on the 04 day of October.
8340
"""
## Data Compression
Beberapa modul yang mendukung untuk kompresi data diantaranya : zlib, gzip, bz2, lzma, zipfile dan tarfile.

import zlib
s = b'witch which has which witches wrist watch'
print(len(s))
t = zlib.compress(s)
print(len(t))
print(zlib.decompress(t))
print(zlib.crc32(s))

"""Output
41
37
b'witch which has which witches wrist watch'
226805979
"""
## Performance Measurement
Beberapa pengguna Python mengembangkan minat yang mendalam untuk mengetahui kinerja relatif dari pendekatan yang berbeda untuk masalah yang sama. Python menyediakan alat pengukuran yang menjawab pertanyaan-pertanyaan itu dengan segera. Modul timeit dengan cepat menunjukkan keunggulan kinerja sederhana:

from timeit import Timer
print(Timer('t=a; a=b; b=t', 'a=1; b=2').timeit())
print(Timer('a,b = b,a', 'a=1; b=2').timeit())

"""Output
0.08620166899981996
0.046212379000280635
"""
## Quality Control
##  Batteries Included
## Brief Tour of the Standard Library — Part II
##  Output Formatting
##  Templating
##  Working with Binary Data Record Layouts
##  Multi-threading
##  Logging
##  Weak References
##  Tools for Working with Lists
##  Decimal Floating Point Arithmetic
##  Virtual Environments and Packages
##  Introduction
##  Creating Virtual Environments
##  Managing Packages with pip
