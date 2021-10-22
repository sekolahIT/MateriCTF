# Kriptografi Modern (RSA) ^^

## **Daftar Isi**

## Pendahuluan

Berbeda dengan kriptografi klasik seperti Caesar, Vigenere, dan algoritma kriptografi klasik lainnya yang biasanya memiliki operasi pada mode karakter, Kriptografi modern adalah kriptografi yang dalam penggunaannya beroperasi pada mode bit. Dalam kriptografi modern ini, baik *key*, *plaintext*, maupun *ciphertext* akan diproses dalam rangkaian bit alih-alih diproses sebagai karakter. Biasanya, kriptografi modern didasari pada teori-teori matematis dan memiliki ketahanan komputasional yang tinggi sehingga sulit dipecahkan oleh penyerang. Biasanya dalam kriptografi modern dibagi dua jenis dalam konteks kunci yang dipakai yaitu algoritma kunci simetris dan algoritma kunci publik.

## Algoritma Kunci Simetris

Algoritma ini menggunakan kunci yang sama pada proses enkripsi dan dekripsi. Contoh Algoritma yang termasuk algoritma kunci simetris seperti DES, Triple DES, AES, dan beberapa algoritma lainnya yang menggunakan Feistel Network.

![kunci-simetris](./resource/kunci-simetris.png)

## Algoritma Kunci Publik (Asimetris)

Seperti yang telah dijelaskan pada [Materi 1 Kriptografi](../../Pertemuan%201/Materi1-Kriptografi/Readme.md). Pada algoritma kunci publik ini, kunci yang digunakan untuk melakukan enkripsi dan dekripsi merupakan kunci yang berbeda yang terdiri dari *public key* atau kunci yang bersifat publik dan boleh disebarluaskan dan *private key* atau kunci yang rahasia. Namun, meskipun kuncinya berbeda bukan berarti antara *public key* dan *private key* tidak memiliki keterkaitan satu sama lain.

![kunci-asimetris](./resource/kunci-asimetris.png)

Contoh dari algoritma yang menggunakan skema kunci ini adalah RSA, Diffie-Hellman dan ECC. Karena skema kunci algoritma ini lebih mahal secara komputational, biasanya digunakan sebagai salah satu algoritma yang digunakan dalam pertukaran kunci(*key exchange*) pada algoritma kunci simetris. Pada pertemuan kali ini, kita akan membahas lebih dalam lagi di algoritma kunci publik khususnya pada algoritma RSA dan beberapa teknik kriptanalisisnya dalam CTF.

## RSA

Rivest-Shamir-Addleman atau biasa disingkat menjadi RSA merupakan algoritma pertama yang menerapkan skema kunci publik secara menyeluruh. Pada RSA, keamanan yang dimiliki berkutat pada kesulitan untuk melakukan faktorisasi bilangan komposit yang sangat besar yang bisa dikatakan merupakan "hard problem" hingga sekarang. Meskipun merupakan Hard Problem, kenapa RSA masih memiliki banyak celah? Pada kasus ini, biasanya kelemahan RSA yang ada bukanlah dikarenakan algoritmanya yang lemah tetapi dikarenakan mudahnya kesalahan dalam implementasinya.

### Bagaimana RSA bekerja

Pada dasarnya, RSA bekerja dengan memanfatkan modular exponentiaton. Modular expontiation sering digunakan dalam kriptografi dan bisa ditulis sebagai berikut.

```python
m ** e % n
```

atau

```python
pow(m, e, n)
```

Dalam algoritma RSA, dengan penggunaan modular expontiation dan faktorisasi bilangan prima memungkinkan algoritma ini bekarja dengan menciptakan *"trapdoor function"*. Fungsi *trapdoor* ini yang membuat RSA mudah untuk dihitung pada satu arah dan sulit untuk dilakukan reverse kecuali memiliki beberapa informasi yang terkait.

## Kriptanalisis pada RSA

Dalam memecahkan problem yang terkait dengan RSA ada beberapa teknik yang biasa digunakan yaitu sebagai berikut.

### Basic (Easy Factorization)

Pada teknik pertama ini kita lakukan secara *straight forward* sesuai dengan *trapdoor* yang ada di RSA. Bila diberikan public key **n** dan kita dapat melakukan faktorisasi n, maka kita dapat melakukan recovery pada nilai **d** dengan mudah.

- FactorDB
Cara pertama untuk melakukan faktorisasi primanya adalah dengan menggunakan FactorDB. Contoh penggunaannya sebagai berikut bila menggunakan module **factordb-pycli**.

```python
from factordb.factordb import FactorDB
from Crypto.Util.number import *

# Public Key
e = 17
n = 3233

# Factorization
f = FactorDB(n)
f.connect()
if f.get_status() == 'FF':
    p, q = f.get_factor_list()

# Recover d value
phi = (p - 1) * (q - 1)
d = inverse(e, phi)
```

- Fermat Factorization

Bila diketahui bahwa p dan q memiliki gap yang kecil yaitu p dan q memiliki separuh nilai bit yang sama misal |p - q| < sqrt(p) maka bisa kita lakukan faktorisasi dengan metoda fermat. Sebagai contoh implementasinya sebagai berikut.

```Python
from gmpy2 import *

def fermatfactor(N):
    if N <= 0: return [N]
    if N % 2 == 0:
        return [2, N//2]
    a = isqrt(N)
    while not is_square(a ** 2 - N):
        a = a + 1
    b = isqrt(a ** 2 - N)
    return [int(a - b), int(a + b)]

print(fermatfactor(115792089237316195423570985008721211221144628262713908746538761285902758367353))
```

Outputnya sebagai berikut.

```STDOUT
[340282366920938463463374607431817146293, 340282366920938463463374607431817146421]
```

Note : Dengan menggunakan fermat faktorization pada p dan q yang berdekatan memungkinkan untuk dilakukan faktorisasi prima dengan sangat cepat tetapi performanya akan turun drastis menjadi sangat lama ketika p dan q nya tidak memiliki separuh bit awal yang sama.

### Nth Root Attack

### Wiener Attack

### Coppersmith Attack 