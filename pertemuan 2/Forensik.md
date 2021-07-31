# Berkenalan Dengan Forensik ^^

## **Daftar Isi**

- [**Pengertian Forensik**](#pengertian-forensik)
- [**List Format File**](#list-format-file)
- [**Manipulasi Data Binari**](#manipulasi-data-binari)
- [**Konsep Forensik**](#konsep-forensik)

## Pengertian Forensik

Forensik dalam kompetisi CTF adalah salah satu kategori CTF yang fokus pada analisis file untuk mendapatkan informasi-informasi yang digunakan dalam mendapatkan flag. File yang dimaksud bisa berupa gambar, audio, video, file dump, dan lain-lain. Tidak seperti forensik dalam CTF, forensik dalam dunia nyata hampir hampir tidak akan pernah melibatkan penguraian skema byte yang dikodekan, data tersembunyi, file-dalam-file seperti mastroshka, atau teka-teki asah otak lainnya. Forensik dunia nyata biasanya mengharuskan seorang praktisi menemukan bukti tidak langsung dari kejahatan: baik jejak penyerang pada sistem, atau jejak perilaku "ancaman orang dalam". Forensik komputer dunia nyata sebagian besar tentang mengetahui di mana menemukan petunjuk yang memberatkan dalam log, dalam memori, dalam sistem file/registri, dan metadata file dan sistem file terkait.

## List Format File

Berikut adalah list format file yang popular dalam lomba CTF kategori forensik

- Archive files (ZIP, TGZ)
- Image file formats (JPG, GIF, BMP, PNG)
- Filesystem images (especially EXT4)
- Packet captures (PCAP, PCAPNG)
- Memory dumps
- PDF
- Video (especially MP4) or Audio (especially WAV, MP3)
- Microsoft's Office formats (RTF, OLE, OOXML)

## Manipulasi Data Binari

## Konsep Forensik

**1. Identifikasi File Format**  
Identifikasi file format digunakan untuk mengetahui format file apakah yang diberikan di soal, hal ini sangat perlu dilakukan karena terkadang di soal tidak diberitahu file apakah yang ada disoal. Untuk mengidentifikasi format file bisa menggunakan linux command "file". Ketikan "**sudo apt-get install file**" jika belum memiliki package "file" di linux Anda.

```
file Untitled.png
Untitled.png: PNG image data, 641 x 68, 8-bit/color RGB, non-interlaced
```

Perintah diatas bermakna kalau pengguna sedang mengidentifikasi file Untitled.png.

**2. File Carving**  
Dalam Kompetisi CTF sering kita jumpai "Files-within-files" atau file di dalam file. File carving sendiri adalah istilah untuk mengekstrak file yang ada di dalam file tersebut. Tool yang popular untuk melakukan file carving adalah **binwalk** dan **foremost**. Ketika "**sudo apt-get install binwalk**" untuk menginstall package di linux Anda.  
contoh gambar : https://mega.nz/file/qbpUTYiK#-deNdQJxsQS8bTSMxeUOtpEclCI-zpK7tbJiKV0tXYY

```
binwalk PurpleThing.jpeg
binwalk -e PurpleThing.jpeg
```

```
foremost PurpleThing.jpeg
```

perbedaan mendasar antara binwalk dan foremost adalah /////////  
list perintah menggunakan binwalk : https://github.com/ReFirmLabs/binwalk/wiki/Usage

**3. Initial Analysis**  
Initial analysis biasanya digunakan untuk mendapatkan clue dari file berupa string. Beberapa tool yang sering digunakan adalah "**string**", "**grep**", "**hexdump**", "**hex editor**" (di windows), atau dapat melalui **https://hexed.it/**.

```
strings PurpleThing.jpeg
strings PurpleThing.jpeg | grep aaa
```

list perintah hexdump

```
hexdump -b namafile.format : untuk input data file dalam bentuk hex
hexdump -c namafile.format : hex dan juga char
hexdump -C namafile.format : hex dan ascii
hexdump -d namafile.format : hex dan decimal
hexdump -o namafile.format : hex dan octal
hexdump -x namafile.format : hex dan hexadecimal
```

penggunaan hexdump sangat penting dalam memahami soal file header yang akan dipelajari pada pertemuan forensik ke dua ^^.

**4. Binary-as-text encodings**  
Binary-as-text encodings adalah konsep untuk mengubah data ke text. Untuk lebih lengkapnya bisa dilihat di https://en.wikipedia.org/wiki/Binary-to-text_encoding. Tentunya tidak semua data yang ada dilist tersebut ada di perlombaan CTF, yang sering adalah ASCII, binary, hex, base64, base32. Untuk melakukan encoding dapat menggunakan python maupun konverter online.

**5. Analisis File Format Gambar**  
File gambar merupakan file paling umum yang sering keluar dari kompetisi CTF. Oleh karena itu, penggunaan beberapa tool analisis file gambar sangat diperlukan untuk mendapatkan informasi-informasi dalam mencari flag. Salah satu tool yang popular adalah exiftool. Untuk menginstall package dapat menjalankan perintah "**sudo apt install libimage-exiftool-perl**".
contoh gambar : https://mega.nz/file/SDpF0aYC#fkkhBJuBBtBKGsLTDiF2NuLihP2WRd97Iynd3PhWqRw

```
exiftool exiftool.jpg
```

Dengan command exiftool maka akan diperoleh informasi-informasi file gambar meliputi file name, file type, file size, x resolution, y resolution dan terkadang informasi atau clue untuk mendapatkan flag. Beberapa tools lain yang dapat digunakan **pngcheck** untuk verifikasi kebenaran file dan memperbaiki file PNG yang corrupt, **stegsolve** ini adalah perintah untuk mengatur warna gambar (seperti gimp, photoshop), **zsteg** adalah tool yang digunakan untuk mendeteksi data tersembunyi pada file PNG & BMP, dan tools lainnya yang teman-teman harus explore dengan mengerjakan soal soal forensik sebanyak-banyaknya ^^.
