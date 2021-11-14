# Web Exploitation

## SQLi (SQL Injection)

SQL Injection adalah proses "injeksi" query SQL yang diakibatkan input user yang tidak difilter yang dimasukkan secara langsung dalam query SQL.

Sebagai contoh, perhatkan query ini untuk sistem login dengan PHP :

`$query = "SELECT * FROM user WHERE username = '" . $_POST['username'] . "' AND password = " . $_POST['password'] . "'";` 

Perhatikan bahwa variable password dan username tidak difilter terlebih dahulu. Hal ini membuat query tersebut rawan disusupi input yang berbahaya. Sebagai contoh, dengan username adalah `'=''or''#`, query aka berubah menjadi :

`$query = "SELECT * FROM user WHERE username = ''=''or''#' AND password = " . $_POST['password'] . "'";`

Query akan memilih seluruh user di table user, dan tentu saja penyerang dapat masuk dengan mudah.

### Contoh Soal
[http://databasic.hax.w3challs.com/](http://databasic.hax.w3challs.com/) (source code : [https://git.w3challs.com/challenges/hax/-/tree/master/databasic](https://git.w3challs.com/challenges/hax/-/tree/master/databasic))


## LFI (Local File Inclusion)

LFI adalah proses pembacaan file yang ada di direktori web app. LFI biasa terjadi karena adanya fungsi seperti include() atau file_get_contents() (di PHP) yang parameternya bebas dikendalikan oleh user.

Contoh klasik dari eksploitasi LFI adalah kode sebagai berikut :
`<?php include($_GET['page']); ?>` 

Dengan memasukkan nama file yang biasanya tersedia, seperti misalnya `?page=/etc/passwd`, kita dapat melihat isi dari file /etc/passwd tersebut.

Selain untuk kasus tersebut, LFI dapat pula dinaikkan menjadi RCE. Ada banyak referensi untuk meningkatkan LFI ke RCE, seperti contohnya [http://blog.zerobyte.id/2018/11/lfi-to-rce-via-access-log.html](http://blog.zerobyte.id/2018/11/lfi-to-rce-via-access-log.html) (RCE dengan access.log). Selain itu, bisa dicari referensi lain untuk meningkatkan dari LFI ke RCE lainnya.


## RCE (Remote Code Execution)

RCE adalah eksekusi kode di aplikasi sesuai dengan keinginan kita. RCE biasanya terjadi saat adanya fungsi eval atau fungsi yang mengeksekusi shell command seperti `shell_exec()` di PHP, atau `os.system()` di Python.

Contohnya seperti berikut :
`<?php eval($_POST['cmd']); ?>`

Dengan mencoba payload seperti `?cmd=system('ls')`, dapat diperiksa apakah eval berfungsi dengan baik dan RCE dapat dilaksanakan.

Tentu saja, terkadang ada kalanya eval() tidak bisa digunakan untuk mengeksekusi shell command. Pada kasus tersebut, kita dapat melakukan eksekusi fungsi PHP biasa seperti `scandir()` atau `file_get_contents()` untuk melakukan eksplorasi direktori dan membaca isi file-file yang diinginkan.

### Contoh Soal
[http://webcompany.hax.w3challs.com/](http://webcompany.hax.w3challs.com/) (source code : [https://git.w3challs.com/challenges/hax/-/tree/master/webcompany](https://git.w3challs.com/challenges/hax/-/tree/master/webcompany))
