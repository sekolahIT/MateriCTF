# Reverse Engineering

- [Reverse Engineering](#reverse-engineering)
  - [Apa itu Reverse Engineering](#apa-itu-reverse-engineering)
  - [Disassemblers](#disassemblers)
  - [Command `file`](#command-file)
  - [Command `strings`](#command-strings)
  - [Command `ltrace` dan `strace`](#command-ltrace-dan-strace)
  - [Operasi XOR](#operasi-xor)
  - [Referensi](#referensi)

## Apa itu Reverse Engineering
Reverse engineering di CTF biasanya jenis soal yang meminta kita untuk bisa memahami bagaimana suatu program berjalan untuk bisa mendapatkan flagnya. Biasanya kita diberikan file executable dan dimintai input, lalu dilakukan pengecekan terhadap input tersebut. Tugas kita adalah mencari input yang benar dan bisa saja inputan yang diminta adalah flag yang kita cari.
Terkadang kita diberikan juga source code dari binary filenya jadi kita bisa memahami alur programnya berjalan, namun seringnya source code tersebut tidak diberikan. Untuk mengetahui cara program tersebut bekerja kita bisa menggunakan disassembler, yang akan mengubah program yang sudah tercompile menjadi machine code.

## Disassemblers
Disassembler ini akan menjadi tools yang paling sering digunakan ketika mengerjakan soal RE. Disassembler ini akan membantu kita untuk menganalisis suatu program. Keluaran yang diberikan bisa berupa assembly code, hingga psuedo code yang lebih mudah dibaca manusia. Kalau ingin mengetahui lebih lanjut tentang assembly, bisa menonton video ini oleh Liveoverflow: [Link](https://www.youtube.com/watch?v=VroEiMOJPm8)
Di video ini kita dapat melihat gdb digunakan. gdb atau GNU Debugger adalah debugger yang dapat kita gunakan untuk mendebug suatu program. gdb juga biasanya digunakan bersamaan dengan [peda](https://github.com/longld/peda), [pwndbg](https://github.com/pwndbg/pwndbg), dan [GEF](https://github.com/hugsy/gef).
Selain gdb, ada beberapa disassembler yang biasa digunakan, seperti IDA Pro, ghidra, radare2, dsb.

## Command `file`
Biasanya hal pertama yang dilakukan ketika mengerjakan soal RE adalah menggunakan command `file` pada file binary yang diberikan untuk mengetahui jenis file binary nya. Beberapa jenis binary file yaitu :
- PE File (.exe or .dll)
- ELF File (elf)
- APK File (apk)
- .NET File (exe)
- Java file
- Python File (pyc or py)
Untuk tiap jenis file yang diberikan, cara untuk melakukan diasassembly nya juga berbeda. Untuk jenis file seperti PE dan ELF, kita dapat menggunakan disassembler seperti IDA atau ghidra, untuk file APK dan Java kita bisa menggunakan JADX, untuk .NET bisa menggunakan dnSpy, dan untuk file python bisa menggunakan uncompyle6.

## Command `strings`
Dengan command ini, kita dapat menemukan clue pada program karena command ini akan mengambil semua readable string pada file binary, yang kemudian bisa kita gabungkan dengan command `grep`, sehingga kita bisa mencari string yang menurut kita penting, contohnya seperti format flag yang kita cari.

## Command `ltrace` dan `strace`
Dengan command `ltrace` kita bisa melihat library calls pada program. Dengan command `strace` kita bisa melihat system calls pada program.

## Operasi XOR
XOR atau exclusive or merupakan operasi binary yang biasa digunakan untuk mengecek input yang dimasukkan oleh user pada soal RE. Jadi hasil yang diberikan operasi xor ini akan bernilai benar apabila hanya salah satu dari bit bernilai benar.
```
a | b | a ^ b
--|---|------
0 | 0 | 0
0 | 1 | 1
1 | 0 | 1
1 | 1 | 0
```
Contoh operasinya seperti ini, jika kita melakukan `7 ^ 10`, dalam binary akan berbentuk `0111 ^ 1010`
```  0111
^ 1010
======
  1101 = 13
```
Biasanya pada soal RE, input kita akan dilakukan pengecekan dengan suatu key yang berulang. Misalnya inputan kita `sesuatu` key nya adalah `hai`, jadi biasanya program akan melakukan operasi xor antara `sesuatu` dengan `haihaih`. Operasi xor ini berlaku kebalkan, jadi kalau hasil dari `A^B = C`, `A^C` akan menghasilkan `B`.

## Referensi
- https://yohan.es/ctf/reverse-engineering/
- https://andhikadipto.wordpress.com/2018/02/10/apa-itu-lomba-hacking-capture-the-flag-ctf/
- https://d00mfist1.gitbooks.io/ctf/content/forensics/reverse-engineering.html
- https://fareedfauzi.gitbook.io/ctf-checklist-for-beginner/reverse-engineering
- https://ctf101.org/reverse-engineering/what-are-disassemblers/
- https://www.youtube.com/watch?v=VroEiMOJPm8
- https://stackoverflow.com/questions/14526584/what-does-the-xor-operator-do#14526640
