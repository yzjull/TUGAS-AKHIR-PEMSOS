# TUGAS AKHIR PRAKTIKUM PEMODELAN OSEANOGRAFI⚓
____
HALOOO...HALLOOOOO 👋:wave::wave:...

Repositori ini dibuat dalam rangka memenuhi tugas akhir Praktikum Pemodelan Oseanografi 2022. Dalam repositori ini memuat terkait dengan pembahasan modul 1 hingga modul 4, Dengan topik bahasan Adveksi-Difusi 1 dimensi & 2 dimensi dan Permodelan Hidrodinamika 1 dimensi & 2 dimensi Dimulai dari Teori dasar, tools serta script yang digunakan, Serta Hasil dan analisis yang dihasilkan.

Dalam Repositori ini, Script yang digunakan adalah bahasa python Namun Platform untuk menggunakan bahasa pemoggraman  ini dapat menyesuaikan seperti Jupyter notebook, Visual studio code dan lain lain.

# Penulis (Kelompok 8)
1. Adnan Izzul Muttaqin    26050120130102 OSE A
2. Dika Surya Pratama      26050120120011 OSE A
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
* 
Perlu diketahui dengan jelas parameter parameter dasar yang digunakan untuk memodelkan Adveksi-difusi 2 dimensi, yang mana didalam script ini digunakan beberapa parameter berikut 
#C = kecepatan aliran
#Q = kriteria kestabilan
#Dt = perubahan waktu
#Dx = jarak antar grid horisontal
#Dy = jarak antar grid vertikal
#Px = jumlah polutan pada sumbu x
#Py = jumlah polutan pada sumbu y
#Ic = jumlah polutan total
```python

#Lama Simulasi
Tend = 101
dt = 0.5

#Polutan
px = 250
py = 231
Ic = 1010

#Perhitungan U dan V
u = C * np.sin(theta*np.pi/180)
v = C * np.cos(theta*np.pi/180)
dt_count = 1/((abs(u)/(q*dx))+(abs(v)/(q*dy))+(2*ad/(q*dx**2))+(2*ad/(q*dy*2)))

Nx = int(x/dx)  #number of mesh in x direction
Ny = int(y/dy)  #number of mesh in y direction
Nt = int(Tend/dt)

#perhitungan titik polutan di buang
px1 = int(px/dx)
py1 = int(py/dy)

#fungsi disederhanakan
lx = u*dt/dx
ly = v*dt/dy
ax = ad*dt/dx**2
ay = ad*dt/dy**2
cfl = (2*ax + 2*ay + abs(lx) + abs(ly))  #syarat kestabilan CFL

#perhitungan cfl
if cfl >= q:
    print('CFL Violated, please use dt :'+str(round(dt_count,4)))
    sys.exit ()
#%%
```

Setelah semua parameter dihitung didalam script, dilakukan visualisasi hasil, dengan scipt sebagai berikut 

```
#pembuatan grid 
x_grid = np.linspace(0-dx, x+dx, Nx+2) #ghostnode boundary
y_grid = np.linspace(0-dx, y+dy, Ny+2) #ghostnode boundary
t = np.linspace(0, Tend, Nt+1)
x_mesh, y_mesh = np.meshgrid(x_grid,y_grid)
F = np.zeros((Nt+1, Ny+2, Nx+2))

#kondisi awal
F[0,py1,px1]=Ic
#%%

#Iterasi
for n in range (0, Nt):
    for i in range (1,Ny+1):
        for j in range (1, Nx+1):
         F[n+1,i,j]=((F[n,i,j]*(1-abs(lx)-abs(ly))) + \
                (0.5*(F[n,i-1,j]*(ly+abs(ly)))) + \
                (0.5*(F[n,i+1,j]*(abs(ly)-ly))) + \
                (0.5*(F[n,i,j-1]*(lx+abs(lx)))) + \
                (0.5*(F[n,i,j+1]*(abs(lx)-lx))) + \
                (ay*(F[n,i+1,j]-2*(F[n,i,j])+F[n,i-1,j])) +\
                (ax*(F[n,i,j+1]-2*(F[n,i,j])+F[n,i,j-1])))
    #syarat batas
    F[n+1,0,:] = 0 #bc bawah
    F[n+1,:,0] = 0 #bc kiri
    F[n+1,Ny+1,:] = 0 #bc atas
    F[n+1,:,Nx+1] = 0 #bc kanan
#%%
```
Kriteria kestabilan = CFL
Adapun rentangnya adalah 0-1. Semakin mendekati 1 maka akan semakin bagus nilainya. Tapi kalau lewat dari 1 maka hasilnya error
Dan output dari hasil visualisasi ini dibentuk dalam bentuk gambar dengan script sebagai berikut:
```
    #Output Gambar
    plt.clf()
    plt.pcolor(x_mesh, y_mesh, F[n+1, :, :], cmap = 'jet',shading='auto',edgecolor='k')
    cbar=plt.colorbar(orientation='vertical',shrink=0.95,extend='both')
    plt.clf()
    plt.pcolor(x_mesh,y_mesh,F[n+1,:,:],cmap='jet',shading='auto',edgecolor='k')
    cbar = plt.colorbar(orientation='vertical',shrink=0.95,extend='both')
    cbar.set_label(label='Concentration',size = 8)
    #plt.clim(0,100)
    plt.title('Kelompok 8 \n t='+str(round(dt*(n+1),3))+ ', Initial condition='+str(Ic),fontsize=10)
    plt.xlabel('x_grid',fontsize=9)
    plt.ylabel('y_grid',fontsize=9)
    plt.axis([0, x, 0, y])
    #plt.pause(0.01)
    plt.savefig(str(n+1)+'.jpg', dpi=300)
    plt.pause(0.01)
    plt.close()
    print('running timestep ke:' +str(n+1) + ' dari:' +str(Nt) + '('+ percentage(n+1,Nt)+')')
    print('Nilai CFL:' +str(cfl) + 'dengan arah: ' +str(theta))
```
Dari seluruh rangkaian akan didapatkan hasil sebagai beikut

ISI DISINI YA SEKAR 

Berdasarkan permodelan diatas. terlihat bahwa distribusiu polutan diperairan beroperasi sesuai nilai C (kecepatan aliran) dan Ad(Koefisien difusi). Semakin besar koefisien difusi maka semakin cepat proses difusi terjadi. Pada saat yang sama, arah difusi kontaminan sangat ditentukan oleh nilai theta (arah pergerakan arus) yang sesuai untuk pemodelan. Menurut Sampera dkk. (2018), pergerakan dan arah distribusi zat dalam air sangat dipengaruhi oleh konsentrasi zat itu sendiri dan kecepatan aliran air di wilayah tersebut. Di wilayah pesisir, konsentrasi pencemar akan menunjukkan nilai tertingginya di sekitar zona pasang surut. Hal konsentrasi pencemar akan menunjukkan nilai tertingginya di sekitar zona pasang surut. Hal ini dikarenakan banyaknya air laut yang mengalir dari laut ke daerah tersebut karena faktor pasang surut.

Menurut Sampera et al. (2018), permodelan adveksi difusi dapat digunakan untuk 
mengetahui sebaran dan pegerakan polutan di perairan, untuk menyelesaikan kasus 
adveksidifusi 2D pada sebaran konsentrasi polutan dapat digunakan metode analitik sebagai 
pembanding untuk menambah validitas data yang dihasilkan, tidak hanya itu persamaan 2 
dimensi adveksi difusi dapat juga diaplikasikan sebagai tools untuk mengetahui distribusi oil 
spill dilaut.
Dalam pengaplikasian difusi adveksi 2 dimensi ada beberapa metode yang dapat 
dilakukan antara lain adalah Metode beda hingga yang merupakan salah satu metode yang 
dapat diterapkan untuk kasus fenomena transpor di perairan dangkal dan aliran air tanah. 
Metode ini biasanya dinyatakan dengan persamaan adveksi difusi karena metode ini dapat 
memberikan hasil pendekatan yang cukup akurat . Penelitian tentang penyelesaian persamaan 
adveksi difusi 2 dimensi untuk model sebaran polutan pernah dilakukan oleh Alman 
menggunakan metode beda hingga Dufort-Frankle dengan asumsi koefisien difusi dan 
kecepatan aliran yang konstan. Dalam penelitiannya Alman menjelaskan bahwa metode beda 
hingga yang digunakan (Metode Beda Hingga DufortFrankle) dapat dipakai untuk 
menyelesaikan persoalan angkutan polutan dalam aliran air yang mengalir dalam aliran 
terbuka. Persamaan tersebut digambarkan dalam sebuah persamaan differensial parsial yang 
disebut sebagai persamaan adveksi-difusi 2D . Selain itu, berdasarkan metode analitik yang 
dilakukan oleh Aminuddin menjelaskan bahwa simulasi model analitik 2D cocok untuk 
sumber polutan sesaat maupun kontinu sehingga menunjukkan hasil yang sesuai dengan yang 
diharapkan
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
* Sama seperti modul sebelumnya, pada modul 3 ini kita menggunakan dua library utama juga, matplotlib dan numpy. Matplotlib berfungsi untuk membuat plot grafik dari hasil running script yang telah dilakukan. sedangkan numpy berfungsi untuk melakukan perhitungan data yang akan dianalisis, sehingga langkah awal dalam pemodelan ini perlu dilakukan import kedua library tersebut. script tersebut seperti yang ada dibawah ini.

```python
import matplotlib.pyplot as plt
import numpy as np
```

* Selanjutnya kita perlu mengisi paramater apa saja yang memengaruhi model yang akan kita buat

```python
p = 7500 #Panjang Grid
T = 2000 #Waktu Simulasi 
A = 0.1 #Amplitudo
D = 5 #Depth/kedalaman
dt = 2
dx = 100
To = 500 #Periode

g = 9.8
pi = np.pi
C = np.sqrt(g*D) #Kecepatan Arus
s = 2*pi/To #Kecepatan Sudut Gelombang
L = C*To #Panjang Gelombang
k = 2*pi/L #Koefisien Panjang Gelombang
Mmax = int(p//dx)
Nmax = int(T//dt) 

zo = [None for _ in range(Mmax)]
uo = [None for _ in range(Mmax)]

hasilu = [None for _ in range(Nmax)]
hasilz = [None for _ in range(Nmax)]

for i in range(1, Mmax+1):
    zo[i-1] = A*np.cos(k*(i)*dx)
    uo[i-1] = A*C*np.cos(k*((i)*dx+(0.5)*dx))/(D+zo[i-1])
for i in range(1, Nmax+1):
    zb = [None for _ in range(Mmax)]
    ub = [None for _ in range(Mmax)]
    zb[0] = A*np.cos(s*(i)*dt)
    ub[-1] = A*C*np.cos(k*L-s*(i)*dt)/(D+zo[-1])
    for j in range(1, Mmax):
        ub[j-1] = uo[j-1]-g*(dt/dx)*(zo[j]-zo[j-1])
    for k in range(2, Mmax+1):
        zb[k-1] = zo[k-1]-(D+zo[k-1])*(dt/dx)*(ub[k-1]-ub[k-2])
        hasilu[i-1] = ub
        hasilz[i-1] = zb
    for p in range(0, Mmax):
        uo[p] = ub[p]
        zo[p] = zb[p]
        
```

* Langkah dalam penulisan script ini kita perlu melakukan ploting untuk kemudian dapat ditampilkan dalam bentuk grafik. dalam hal ini kita juga dapat menentukan size yang akan digunakan dan jumlah grafik yang akan kita buat. Disini kita menggunakan 4 grafik dimana ax0 merupakan Perubahan Kecepatan Arus Dalam Grid Tertentu di Sepanjang waktu, ax1 merupakan Perubahan elevasi muka air dalamm grid tertentu di sepanjang waktu, ax2 merupakan Perubahankecepatan arus dalam grid tertentu di sepanjang grid, dan ax 3 merupakan perubahan elevasi permukaan air dalam grid waktu tertetu di sepanjang grid

```python
def rand_col_hex_string():
    return f'#{format(np.random.randint(0,16777215), "#08x")[2:]}'

hasilu_np = np.array(hasilu)
hasilz_np = np.array(hasilz)

fig0, ax0 = plt.subplots(figsize=(12,8))
for i in range(1, 16):
    col0 = rand_col_hex_string()
    line, = ax0.plot(hasilu_np[:,i-1], c=col0, label=f'n={i}')
    ax0.legend()

    ax0.set(xlabel='Waktu', ylabel='Kecepatan Arus',
            title=''' Kelompok 8 Pemodelan Oseanografi 2022
            Perubahan Kecepatan Arus Dalam Grid Tertentu di Sepanjang Waktu''')
    ax0.grid()

fig1, ax1 = plt.subplots(figsize=(12,8))
for i in range(1, 16):
    col1 = rand_col_hex_string()
    line, = ax1.plot(hasilz_np[:,i-1], c=col1, label=f'n={i}')
    ax1.legend()

    ax1.set(xlabel='Waktu', ylabel='Elevasi Muka Air',
            title=''' Kelompok 8 Pemodelan Oseanografi 2022
            Perubahan Elevasi Permukaan Air Dalam Grid Tertentu di Sepanjang Waktu''')
    ax1.grid()

fig2, ax2 = plt.subplots(figsize=(12,8))
for i in range(1, 16):
    col2 = rand_col_hex_string()
    line, = ax2.plot(hasilu_np[i-1], c=col2, label=f't={i}')
    ax2.legend()

    ax2.set(xlabel='Grid', ylabel='Kecepatan Arus',
            title=''' Kelompok 8 Pemodelan Oseanografi 2022
            Perubahan Kecepatan Arus Dalam Waktu Tertentu di Sepanjang Grid''')
    ax2.grid()

fig3, ax3 = plt.subplots(figsize=(12,8))
for i in range(1, 16):
    col3 = rand_col_hex_string()
    line, = ax3.plot(hasilz_np[i-1], c=col3, label=f't={i}')
    ax3.legend()
    ax3.set(xlabel='Grid', ylabel='Elevasi Muka Air',
            title=''' Kelompok 8 Pemodelan Oseanografi 2022
            Perubahan Elevasi Permukaan Air Dalam Waktu Tertentu di Sepanjang Grid''')
    ax3.grid()

```

* Terakhir kita perlu memberikan perintah untuk menampilkan hasil plotting grafik tersebut

```python
plt.show()
```

* Selanjutnya kita hanya perlu melakukan running dari script tersebut, kemudian simpan hasil grafik yang berhasil didapatkan.



  ### :label: Hasil dan pembahasan
  ***
* Hasil dari running script yang telah dilakukan akan berupa 4 grafik pada gambar dibawah ini.

![Figure_1](https://user-images.githubusercontent.com/105930996/169948568-537c1352-c104-4289-88a1-fec459410fc5.png)

Grafik menunjukkan bahwa pada waktu antara 0 sampai rentang 200 kecepatan arus bergerak konstan. Hal ini dikarenakan pada rentang waktu tersebut menggunakan nilai parameter cenderung halus atau mempunyi nilai kecil. Nilai kecil dikarenakan asumsi yang kita masukkan. 

![Figure_2](https://user-images.githubusercontent.com/105930996/169948589-9870d51d-e6e9-4be9-8eff-b757b6cadef9.png)

Grafik menunjukkan bahwa pada waktu antara 0 sampai rentang 200 elevasi muka air bergerak konstan. Hal ini dikarenakan pada rentang waktu tersebut menggunakan nilai parameter cenderung halus atau mempunyi nilai kecil. Nilai kecil dikarenakan asumsi yang kita masukkan. 

![Figure_3](https://user-images.githubusercontent.com/105930996/169948610-9ff821d1-2a35-4a66-b9f5-62d0992614b0.png)

Pada grafik perubahan kecepatan arus dalam waktu tertentu di sepanjang grid juga terlihat memiliki nilai yang konstan. Namun, pada akhir grid memiliki nilai yang tidak beraturan karena kecepatan arus dalam waktu berpengaruh pada ruang.

![Figure_4](https://user-images.githubusercontent.com/105930996/169948629-0f92b34c-8739-4c07-942b-0a69d8eb2c19.png)

Pada grafik perubahan elevasi permukaan air dalam waktu tertentu di sepanjang grid juga terlihat memiliki nilai yang konstan. Namun, pada akhir grid memiliki nilai yang tidak beraturan karena perubahan elevasi permukaan air dalam waktu berpengaruh pada ruang.



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

      
