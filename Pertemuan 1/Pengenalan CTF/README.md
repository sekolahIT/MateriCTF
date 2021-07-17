#  Pengenalan CTF
<!-- toc -->
- [Pengenalan CTF](#pengenalan-ctf)
  - [Apa itu CTF](#apa-itu-ctf)
  - [Jenis Lomba CTF](#jenis-lomba-ctf)
    - [Attack Defense](#attack-defense)
    - [Jeopardy](#jeopardy)
      - [Kategori Soal](#kategori-soal)
        - [Cryptography](#cryptography)
        - [Web Exploitation](#web-exploitation)
        - [Forensics](#forensics)
        - [Reverse Engineering](#reverse-engineering)
        - [Programming](#programming)
        - [Miscellaneous](#miscellaneous)
  - [Durasi Lomba](#durasi-lomba)
  - [Salah Satu Cara Belajar CTF](#salah-satu-cara-belajar-ctf)
    - [Cari Lomba CTF](#cari-lomba-ctf)
    - [Coba Kerjain Soal](#coba-kerjain-soal)
    - [Cari Write Up](#cari-write-up)
    - [Repeat](#repeat)
  - [Gunanya Komunitas TCyber](#gunanya-komunitas-tcyber)
  - [Referensi](#referensi)
<!-- /toc -->

## Apa itu CTF
CTF (Capture the flag) atau lebih tepatnya lagi: Security CTF adalah kompetisi dalam bidang security di mana para peserta diminta mencari flag (berupa string tertentu) yang disembunyikan atau dilindungi dengan cara tertentu. Event CTF biasanya gratis, sebagian besar online dan diselenggarakan berbagai pihak. Penyelenggara CTF bisa berupa perusahaan baik kecil maupun besar (seperti Google, Facebook), Universitas, pemerintah, ataupun organisasi lain.
Contoh flag biasanya seperti ini : `CTF{1Ni_c0nT0h_fl46}`

## Jenis Lomba CTF
Ada beberapa jenis lomba CTF, tapi yang populer biasanya dua jenis ini :
### Attack Defense
Pada jenis ini, biasanya masing-masing peserta / tim akan diberikan virtual machine / image server. Yang nantinya peserta akan diminta menghardening sistem tersebut selamat periode waktu tertentu (fase bertahan), lalu nantinya akan masuk ke fase selanjutnya yaitu fase menyerang yang dimana para competitor akan saling meyerang satu sistem dengan yang lainnya.

### Jeopardy
Pada jenis ini, biasanya menggunakan server untuk menyimpan soal, yang dimana soalnya bisa berbentuk web exploitation, reverse engineering, binary exploitation, forensic, cryptography, steganography, programming, dan lain-lain dengan tujuan yang tetap sama yaitu mencari string/flag yang disembunyikan oleh pembuat soal.

#### Kategori Soal
kalo di jeopary, biasanya soal dikategoriin jadi beberapa kategori
##### Cryptography
Biasanya kita akan dikasi pesan rahasia yang harus dibongkar. Nah kita mengenal berbagai macam tipe enkripsi, dan pola dari masing-masing algoritma ini. Untuk menyelesaikan soal crypto bisa menggunakan tools seperti cryptool.
##### Web Exploitation
Untuk CTF dengan kategori Web biasanya kita akan dikasih sebuah alamat web, peserta akan diminta mencari cara untuk mendapatkan akses ke web tersebut. Terdapat berbagai macam cara, bisa dengan SQL injection, XSS injection dll.
##### Forensics
Disini kita akan diberi sebuah data atau file, kemudian kita diminta mengekstrak flag dari data tersebut. Misalnya mengekstrak data dari disk image, dari memory dump dll. Ada juga terkadang kita diminta membongkar pesan yang disembunyikan dengan teknik steganografi. Disini diperlukan pemahaman tentang berbagai macam format data.
##### Reverse Engineering
Disini kita dikasi sebuah file binary, kemudian kita diminta untuk melakukan reverse engineering dan mencari flag yang disembunyikan pada file tersebut. Tapi ada juga lomba yang memberi sebuah source code, kemudian kita diminta mencari flag yang disembunyikan disitu. Disini diperlukan keahlian membaca kode.
##### Programming
Disini biasanya kita biasanya dikasi sebuah permasalahan matematika. Untuk menyelesaikan perhitungannya kita perlu membuat sebuah script. Biasanya disini diperlukan pemahaman tentang membuat script.
##### Miscellaneous
Untuk soal dengan kategori ini biasanya memang soal itu kurang cocok dimasukkan ke kategori manapun, bisa jadi karena memang soalnya sangat "random".
## Durasi Lomba
Untuk durasi lomba CTF biasanya hanya beberapa jam atau hari, tapi ada beberapa CTF yang durasi kontesnya sudah berakhir namun challengenya tetap dibuka, contohnya seperti picoCTF.
## Salah Satu Cara Belajar CTF
Untuk cara belajar CTF ini pastinya ada banyak, langkah-langkah di bawah ini cuma salah satu dari banyak cara belajar tersebut.
### Cari Lomba CTF
Untuk lomba CTF biasanya bisa cari di website seperti ctftime.org. Di ctftime ini biasanya tiap kontes ada weight. Weight ini biasanya menentukan tingkat kesulitannya. Akan ada yang weightnya 0, itu bukan berarti sangat gampang, tapi bisa jadi memang CTFnya baru dan masih dilakukan perhitungan weightnya.
### Coba Kerjain Soal
Pilih kontes bebas, dan di kontes itu pilih beberapa(atau semua juga boleh) untuk dicoba kerjakan. Kalau memang ga bisa selesai ya ga masalah, namanya juga proses belajar.
### Cari Write Up
Dari soal yang tadi sudah dipilih, cari write up nya, bisa lewat website ctftime, google, github, twitter, dan lain-lain. Pastikan write up nya dipahami, karena mungkin ilmunya berguna untuk kedepannya.
### Repeat
Sepertinya cukup self-explanatory langkah ini.
## Gunanya Komunitas TCyber
- Teman Belajar
- Cari Tim
- Tempat Nanya
- dll


## Referensi
https://yohan.es/ctf/
https://socs.binus.ac.id/2018/12/13/mengenal-capture-the-flag/
https://julismail.staff.telkomuniversity.ac.id/belajar-ctf/
https://www.youtube.com/watch?v=Lus7aNf2xDg