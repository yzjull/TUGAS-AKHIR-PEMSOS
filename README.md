# TUGAS AKHIR PRAKTIKUM PEMODELAN OSEANOGRAFI⚓
____
HALOOO...HALLOOOOO 👋:wave::wave:...

Repositori ini dibuat dalam rangka memenuhi tugas akhir Praktikum Pemodelan Oseanografi 2022. Dalam repositori ini memuat terkait dengan pembahasan modul 1 hingga modul 4 beserta script pemodelan yang digunakan dalam praktikum

# Penulis (Kelompok 8)
1. Adnan Izzul Muttaqin    26050120130102 0SE A
2. Dika Surya Pratama
3. Anindita Rahma Candrasekar 26050120130111 OSE A
4. Eldeenio Akeyla Ibrahim
5. Zalfa Karima
6. Nadina raisa 26050120140161 OSE B
7. Muhammad Aulia Ababil 26050120140112 Ose B

# **Cara Penggunaan Executable File (.exe)💻**

# **Metode Pengerjaan**
     Modul 1
    
     Modul 2

     Modul 3

     Modul 4
## 🗂️ **MODUL 1**
## :card_index_dividers: **MODUL 2**

✰ Persamaan difusi-adveksi merupakan model matematika yang menggambarkan proses transportasi suatu zat yang dipengaruhi oleh gaya gravitasi dan penyebaran yang sekaligus. Zat yang dimaksud cenderung berupa fluida (gas atau cair).

✰ Penerapan adveksi difusi 2 dimensi dapat dilihat pada pergerakan polutan, pencemaran sungai, maupun kebakaran hutan.

## :card_index_dividers: **MODUL 3 : HIDRODINAMIKA 1 DIMENSI**

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

