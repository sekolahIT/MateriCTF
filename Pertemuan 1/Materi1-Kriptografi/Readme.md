# Berkenalan Dengan Kriptografi ^^

## **Daftar Isi**

- [**Pengertian Kriptografi**](#pengertian-kriptografi)
- [**Fungsi Dasar Kriptografi**](#fungsi-dasar-kriptografi)
- [**Algoritma Kriptografi**](#algoritma-kriptografi)
- [**Contoh Implementasi Kriptografi**](#contoh-implementasi-kriptografi)
- [**Algoritma Kriptografi Klasik**](#algoritma-kriptografi-klasik)

## Pengertian Kriptografi

Kriptografi adalah sebuah proses menyampaikan pesan secara rahasia dan tersembunyi.
Kriptografi berasal dari bahasa Yunani dengan memadukan dua kata, yaitu **kryptos** dan **graphein**.
Kryptos berarti tersembunyi atau rahasia, sedangkan graphein memiliki arti menulis. Dengan adanya
kriptografi diharapkan aman dari pihak ketiga dalam proses pengiriman pesan ke tujuan.

## Fungsi Dasar Kriptografi

Berikut adalah fungsi dasar kriptografi yang mana fungsi dasar ini sangatlah sering digunakan pada proses pembelajaran kriptografi

1. Enkripsi (encryption) = proses penyembunyian data pesan, mengubah plaintext (text biasa) menjadi chipertext (text tersandi)
2. Dekripsi (decryption) = proses mengubah chipertext (text tersandi) menjadi plaintext (text biasa)
3. Kunci (key) = teknik yang digunakan untuk enkripsi atau dekripsi. Kunci ini dibagi menjadi 2 yaitu kunci privasi (private key) dan
   kunci publik (public key)

## Algoritma Kriptografi

Setelah memahami 3 fungsi dasar kriptografi diatas, berikut akan dijelaskan tentang jenis-jenis algoritma kriptografi

1. Jenis-Jenis Algoritma Kriptografi Berdasarkan Kunci

   - Algoritma Kriptografi Simetris  
     ![sim](https://user-images.githubusercontent.com/87466033/125815186-38f22174-faa2-48a9-83b5-96d045144bb6.jpg)  
      Algoritma ini menggunakan kunci yang sama pada proses enkripsi dan dekripsi. Oleh karena itu implementasi dari algoritma kriptografi
     sangat sederhana dan dapat diimplementasikan pada real time karena proses enkripsi dan dekripsi yang cepat. Kelemahan dari algoritma
     ini adalah sistem keamanan yang rentan dikarenakan hanya satu kunci yang digunakan. Sehingga apabila satu kunci diketahui pihak ketiga
     maka plaintext dapat dengan mudah diketahui oleh pihak ketiga.  
      Contoh implementasi : <a href="./AES.md">AES</a>, blowfish, DES, IDEA, dll
   - Algoritma Kriptografi Asimetris  
     ![kriptografi4](https://user-images.githubusercontent.com/87466033/125821944-bde444b9-7613-423b-9b05-0d082c328b7d.png)  
      Algoritma ini menggunakan kunci yang berbeda pada proses enkripsi dan dekripsi. kunci yang digunakan umumnya disebut dengan kunci publik
     dan kunci rahasia. Karena penggunaan kunci yang berbeda tentunya menyebabkan proses enkripsi dan dekripsi lebih rumit dan membutuhkan waktu
     yang lama dibandingkan dengan algoritma kriptografi simetris. Akan tetapi proses enkripsi dan dekripsi yang rumit itu menyebabkan keamanan
     pada algoritma kriptografi asimetris jauh lebih aman dibandingkan algoritma kriptografi simetris.  
      Contoh implementasi : <a href="./RSA.md">RSA</a>, ECC, dll

2. Jenis-Jenis Algoritma Kriptografi Berdasarkan Waktu
   - Algoritma Kriptografi Klasik  
     Algoritma kriptografi klasik digunakan sejak sebelum era komputerisasi dan kebanyakan menggunakan teknik kunci simetris. Selain itu algoritma
     ini hanya berbasis karakter dengan menggunakan pena dan kertas. Metode menyembunyikan pesannya adalah dengan teknik substitusi atau transposisi
     atau keduanya. Teknik substitusi adalah menggantikan karakter dalam plaintext menjadi karakter lain yang hasilnya adalah ciphertext.
     Sedangkan transposisi adalah teknik mengubah plaintext menjadi ciphertext dengan cara permutasi karakter.  
     Contoh implementasi : <a href="./Caesar.md">Caesar Cipher</a>, Vigenere Cipher, Hill Cipher dll
   - Algoritma Kriptografi Modern  
     Algoritma kriptografi modern merupakan suatu perbaikan yang mengacu pada kriptografi klasik. Algoritma ini menggunakan pengolahan simbol biner
     yang dibentuk dari kode ASCII karena berjalan mengikuti operasi komputer digital sehingga membutuhkan pengetahuan dasar matematika untuk
     menguasainya. Algoritma ini memiliki tingkat kesulitan yang kompleks yang menyebabkan kriptanalis sangat sulit memecahkan ciphertext tanpa
     mengetahui kuncinya.  
     Contoh implementasi : MD5, <a href="./AES.md">AES</a>, dll

## Contoh Implementasi Kriptografi

![Sumber-gambar-http fanart tv_](https://user-images.githubusercontent.com/87466033/125800694-230465cb-1ca8-461a-a258-bb1c193b8819.jpg)

- Mesin Enigma
- ATM = Komunikasi antara ATM dengan komputer host ketika verifikasi PIN
- SSL = Secure Socket Layer - menjamin keamaanan data antara client dan server
- 7-Zip = menggunakan AES
- dll

## Algoritma Kriptografi Klasik
Seperti penjelasan diatas, ciri utama dari algoritma kriptografi klasik adalah penggunaan dilakukan sebelum era komputerisasi dan **berbasi karakter**. Oleh karena itu, algoritma kriptografi klasik sering berbentuk penggeseran huruf di dalam plaintext sebanyak n atau merubah plaintext dengan pola tertentu. Berikut adalah jenis-jenis algoritma kriptografi klasik  
1. Monoalphabetic Cipher  
Monoalphabetic adalah teknik kriptografi substutusi yang mengganti setiap karakter plainteksnya menjadi karakter lain pada chiperteks. Huruf yang sama pada plainteks, akan memiliki huruf pengganti yang sama pula pada chiperteksnya. Seperti pada contoh Caesar chiper, huruf A pada plainteks akan selalu diganti dengan huruf D pada chiperteks. Metoda lain pada monoalphabetic chiper adalah ROT13 yang mengganti setiap huruf pada plainteksnya dengan huruf yang letaknya 13 posisi darinya. Oleh karena itu hubungan antara plainteks dengan chiperteksnya mudah diterka, karena huruf yang sering muncul pada palinteks akan sering muncul pula pada chiperteks.  
Dengan informasi bahasa yang digunakan dan konteks pesan, cryptoanalysis dapat menggunakan 2 metode berikut untuk memecahkan pesan:  

* Metode Terkaan  
* Analisis Frekuensi  
   Setiap bahasa memiliki huruf yang sering digunakan atau jarang digunakan. Misalnya huruf a sering sekali digunakan dalam bahasa Indonesia, dan q atau x jarang sekali    
   muncul. Setiap bahasa memiliki pola frekuensi tertentu, yang menunjukkan frekuensi relatif dari digunakannya huruf-huruf dalam bahasa tersebut. Bahasa inggris                    mempunyai tabel frekuensi yang dibedakan dalam tiga kategori yaitu :  
   i. Top 10 huruf yang sering muncul dalam teks Bahasa Inggris: E, T, A, O, I, N, S, H, R, D, L, U  
   ii. Top 10 huruf bigram yang sering muncul dalam teks Bahasa Inggris: TH, HE, IN, EN, NT, RE, ER, AN, TI, dan ES  
   iii. Top 10 huruf trigram yang sering muncul dalam teks Bahasa Inggris: THE, AND, THA, ENT, ING, ION, TIO, FOR, NDE, dan HAS  

   Contoh Monoalphabetic Cipher : Caesar cipher, Atbash Cipher, Pigpen/Masonic Cipher, Polybius Square Cipher  
   
2. Polyalphabetic Cipher  
   Berbeda dengan monoalphabetic cipher, pada polyalphabetic cipher menggunakan kunci yang lebih dari satu alphabet.  
   contohnya  
   plaintext   = KRIPTOGRAFI  
   kunci       = CTF  
   ciphertext  = MKNRMTIKFHB  
   
   Contoh Polyalphabetic Cipher : Vigenere Cipher, Beaufort Cipher, Autokey Cipher, Running Key Cipher 
   
3. Polygraphic Cipher  
   poligraphic cipher adalah metode substitusi yang melibatkan penggantian sekelompok karakter dalam pesan dengan kelompok huruf atau karakter yang berbeda. Subtitusi bisa
   dilakukan berdasarkan pola tabel atau yang lainnya dengan aturan tertentu.  
   
   Contoh Polygraphic Cipher : Playfair Cipher, Bifid Cipher, Trifid Cipher, Four-Square Cipher  
   https://translate.google.com/translate?u=https://en.wikipedia.org/wiki/Substitution_cipher&hl=id&sl=en&tl=id&client=srp&prev=search  
   
4. Transposision Cipher  
   Transposition cipher adalah salah satu jenis teknik pengenkripsian pesan dengan cara mengubah urutan huruf-huruf yang ada di dalam plainteks(pesan yang belum dienkripsi)
   menjadi cipherteks pesan ynag telah dienkripsi) dengan cara tertentu agar isi dari pesan tersebut tidak dimengerti kecuali oleh orang-orang tertentu. Pada dasarnya prinsip 
   pengubahan pesan mirip dengan anagram seperti kata ―melepas diubah menjadi ―saeelpm, tapi tentu saja transposition cipher mempunyai rumus atau kunci tertentu yang diperlukan
   agar pesan bisa dimengerti.  
   
   Contoh Transposision Cipher : Rail Fence Cipher (RFC), Zig-zag Cipher, Rout Cipher, Columnar Transposision
   
