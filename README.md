# TUGAS AKHIR PRAKTIKUM PEMODELAN OSEANOGRAFI⚓
____
HALOOO...HALLOOOOO 👋:wave::wave:...

Repositori ini dibuat dalam rangka memenuhi tugas akhir Praktikum Pemodelan Oseanografi 2022. Dalam repositori ini memuat terkait dengan pembahasan modul 1 hingga modul 4 beserta script pemodelan yang digunakan dalam praktikum

# Penulis (Kelompok 8)
1. Adnan Izzul Muttaqin    26050120130102 OSE A
2. Dika Surya Pratama
3. Anindita Rahma Candrasekar 26050120130111 OSE A
4. Eldeenio Akeyla Ibrahim
5. Zalfa Karima
6. Nadina Raisa 26050120140161 OSE B
7. Muhammad Aulia Ababil 26050120140112 OSE B

# **Cara Penggunaan Executable File (.exe)💻**

# **Metode Pengerjaan**
  [Modul 1](#modul-1)
    
  [Modul 2](#modul-2)

  [Modul 3](#modul-3)

  [Modul 4](#modul-4)
  
## 🗂️ **MODUL 1**
## :card_index_dividers: **MODUL 2 : ADVEKSI-DIFUSI 2 DIMENSI**

### :label: Pendahuluan 
  ***
✰ Persamaan difusi-adveksi merupakan model matematika yang menggambarkan proses transportasi suatu zat yang dipengaruhi oleh gaya gravitasi dan penyebaran yang sekaligus. Zat yang dimaksud cenderung berupa fluida (gas atau cair).

✰ Penerapan adveksi difusi 2 dimensi dapat dilihat pada pergerakan polutan, pencemaran sungai, maupun kebakaran hutan.

✰ Konsentrasi polutan di dalam air maupun udara pada posisi 𝑥 dan pada saat 𝑡 dapat 
diketahui melalui solusi dari model persamaan difusi-adveksi yang dinotasikan dengan 
u(𝑥,t). 

✰ Dalam adveksi-difusi 2 dimensi ini, digunakan 2 library utama yaitu matplotlib dan numpy. Untuk lebih jelasnya, dapat dijelaskan menggunakan script di bawah ini.
### :label: Langkah Pengerjaan Script Adveksi-Difusi 2 Dimensi
  ***
* Seperti yang telah dijelaskan di pendahuluan, pada modul 2 ini kita perlu menggunakan library berupa matplotlib dan numpy. Matplotlib berfungsi untuk membuat plot grafik dari hasil running script yang telah dilakukan. sedangkan numpy berfungsi untuk melakukan perhitungan data yang akan dianalisis, sehingga langkah awal dalam pemodelan ini perlu dilakukan import kedua library tersebut. script tersebut seperti yang ada dibawah ini.
```python
import matplotlib.pyplot as plt
import numpy as np
import sys
```

## :card_index_dividers: **MODUL 3 : HIDRODINAMIKA 1 DIMENSI**
### :label: Pendahuluan 
  ***
✰ Hidrodinamika adalah cabang ilmu yang berhubungan dengan gerak Liquid atau lebih dikhususkan pada gerak air.

✰ Model hidrodinamika : model yang dibangun dari adanya proses-proses yang mempengaruhi pergerakan massa air. Dengan adanya model hidrodinamika kita dapat mengsimulasikan elevasi muka air laut, dan arus yang dipengaruhi oleh beberapa parameter. 
Fenomena pasang dan surut, membangkitkan arus pasang dan surut, kemudian membawa massa air bersamaan dengan arus.

✰ Kelemahan dari hidrodinamika yaitu memiliki terlalu banyak data dan rentan error serta membutuhkan waktu simulasi yang lama, apabila terdapat perhitungan aliran kritis

✰ Hukum- hukum yang berlaku dalam hidrodinamika 1D adalah
1. Hukum momentum
2. Hukum konservasi massa atau kontinuitas

✰  sehingga persamaan yang digunakan antara lain :

1. Persamaan momentum
2. Persamaan kontinuitas


✰ Pada hasil script kita akan mendapatkan hasil berupa grafik Perubahan Kecepatan Arus dalam grid tertentu di sepanjang waktu; Perubahan elevasi permukaan air dalam grid tertentu di sepanjang waktu; Perubahan kecepatan arus dalam waktu tertentu di sepanjang grid; dan perubahan elevasi permukaan air dalam waktu tertentu di sepanjang grid.

  ### :label: Langkah Pengerjaan Script Hidrodinamika 1 Dimensi
  ***




## :card_index_dividers: **MODUL 4** : **HIDRODINAMIKA 2 DiMENSI**
  
  ### :label: Pendahuluan 
  ***
  * Hidrodinamika adalah cabang dari mekanika fluida, khususnya zat cair inkrompresibel yang dipengaruhi oleh gaya internal dan external. Gaya-gaya penting dalam hidrodinamika laut adalah gaya gravitasi, gaya gesekan, dan gaya coriolis.
  * Dalam pemodlan Hidrodinamika 2 dimensi, kita menggunakan 2 library, yaitu matplotlib dan shipon. Matplotlib berfungsi untuk membuat plot grafik dari hasil running script yang telah dilakukan. sedangkan siphon berfungsi untuk mengunduh data dari layanan data jarak jauh dalam hal ini yaitu data dari NDBC.
  * Dalam Hidrodinamika 2 Dimensi ini bisa dimanfaatkan atau digunakan untuk peninjauan gaya pembangkit arus yang disebabkan angin.
  ### :label: Langkah Pengerjaan Script Hidrodinamika 2 Dimensi
  ***
  * Langkah pertama yang perlu dilakukan apabila belum terdapat library matplotlib dan Siphon kita perlu menginstal library tersebut dengan menggunakan anaconda prompt. Code dibawah merupakan code untuk mengistall library siphon, kemudian jika dituliskan pada anaconda prompt lalu tekan enter dan tunggu hingga berhasil
  
        (base) C:\Users\ACER>pip install siphon
* Kemudian dalam pemodelan di modul 4 berdasarkan data yang telah disedikan oleh NDBC

```python
# Copyright (c) 2018 Siphon Contributors
# Distributed under the terms of the BSD 3-Clause License
# SPDX-License-Identifier : BSD-3-Clause
"""
NDBC Buoy Meteorological Data Request
======================================
The NDBC keeps a 45-day recent rolling file for each buoy. This examples shows how to access
the basic meteorological data from a buoy and make a simple plot.
"""
```
* Seperti yang telah disinggung di pendahuluan bahwassannya kita perlu menggunakan library berupa matplotlib dan siphon. Matplotlib berfungsi untuk membuat plot grafik dari hasil running script yang telah dilakukan. sedangkan siphon berfungsi untuk mengunduh data dari layanan data jarak jauh dalam hal ini yaitu data dari NDBC. jadi langkah awal dalam pemodelan ini perlu dilakukan import kedua library tersebut. script tersebut seperti yang ada dibawah ini.
```python
import matplotlib.pyplot as plt

from siphon.simplewebservice.ndbc import NDBC
```
* Selanjutnya kita perlu mengisikan atau mengkoneksikan data buoy yang kita gunakan berdasarkan pada id stasiun yang diinginkan, berikut script untuk mengkoneksikan data pada id stasiun NDBC yang ingin digunakan.
```python
# Get a pandas data frrame of all of the observations, meteorological data os the default
# observation set query.
df = NDBC.realtime_observations('51003') #Stasiun ID
df.head()
```
* Selanjutnya langkah dalam penulisan script ini kita perlu melakukan ploting untuk kemudian dapat ditampilkan dalam bentuk grafik. dalam hal ini kita juga dapat menentukan size yang akan digunakan dan jumlah grafik yang akan kita buat. Disini kita menggunakan 3 grafik diman ax1 merupakan *#pressure*, ax2 merupakan *Wind Speed, gust, direction*, dan ax3 merupakan *#water temperature* 
```python
# Let's make a simple time series plot to ceckout what the data look like.
fig, (ax1, ax2, ax3) = plt.subplots(3, 1, figsize=(12, 10))
ax2b = ax2.twinx()
```
* selanjutnya kita dapat memberikan label keterangan pada plot grafik yaang akan menjadi output dari pemodelan ini, berikut script untuk ploting labelnya.
```python
# Pressure
ax1.plot(df['time'], df['pressure'], color='black')
ax1.set_ylabel('pressure [hPa]')
fig.suptitle('Tugas Akhir Praktikum Pemos_Kelompok 8', fontsize = 18)


# Wind speed, gust, direction
ax2.plot(df['time'], df['wind_speed'], color='tab:orange')
ax2.plot(df['time'], df['wind_gust'], color='tab:olive', linestyle='--')
ax2b.plot(df['time'], df['wind_direction'], color='tab:blue', linestyle='-')
ax2.set_ylabel('Wind Speed [m/s]')
ax2b.set_ylabel('Wind Direction')


# Water temperature
ax3.plot(df['time'], df['water_temperature'], color='tab:red')
ax3.set_ylabel('water Temperature [degC]')
```
* kemudian langkah terakhir yaitu kita perlu memberikan perintah untuk kemudian menampilkan hasil plotting grafik tersebut
```python
plt.show()
```
* Kemduian setelah itu kita tinggal melakukan running dari script pemodelan tersebut. Simpan hasil grafik yang telah berhasil didapatkan.
* Buka Website NDBC-NOAA

![website buka](https://user-images.githubusercontent.com/105930126/169840854-dd67ad34-84db-41df-a19d-af5cdb0f49d1.jpg)

* Kemudian bisa kita cari id stasiun yang kita gunakan pada script tadi melalui kolom pencarian

![Screenshot 2022-05-23 212335](https://user-images.githubusercontent.com/105930126/169841337-90b7c846-8ccd-4fa4-90ac-5c02b2e34f8a.jpg)

* kemudian kita dapat melakukan analisis terhadap keadaan buoy terkait dengan lokasi dan sebagainnya dari website tersebut.

### :label: Hasil dan Pembahasan
***

* Hasil dari running script tersebut berupa 3 grafik seperti pada gambar dibawah ini

![hasil](https://user-images.githubusercontent.com/105930126/169843509-04ea5ab9-e1b2-451d-ad5a-ca0438dd42e0.jpg)

      
