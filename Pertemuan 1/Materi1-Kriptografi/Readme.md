# Berkenalan Dengan Kriptografi ^^

## **Daftar Isi**

- [**Pengertian Kriptografi**](#pengertian-kriptografi)
- [**Fungsi Dasar Kriptografi**](#fungsi-dasar-kriptografi)
- [**Algoritma Kriptografi**](#algoritma-kriptografi)
- [**Contoh Implementasi Kriptografi**](#contoh-implementasi-kriptografi)

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
     Contoh implementasi : <a href="./Caesar.md">Caesar Cipher</a>, <a href="./Vigenere.md">Vigenere Cipher</a>, Hill Cipher dll
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

terima kasih ^^
