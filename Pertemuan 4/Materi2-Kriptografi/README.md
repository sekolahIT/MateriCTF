# Kriptografi Modern (RSA) ^^

## **Daftar Isi**

- [**Pendahuluan**](#pendahuluan)
- [**Algoritma Kunci Simetris**](#algoritma-kunci-simetris)
- [**Algoritma Kunci Publik**](#algoritma-kunci-publik)
- [**Rivest-Shamir-Addleman**](#rsa)
- [**Kriptanalisis pada RSA**](#kriptanalisis-pada-rsa)

## Pendahuluan

Berbeda dengan kriptografi klasik seperti Caesar, Vigenere, dan algoritma kriptografi klasik lainnya yang biasanya memiliki operasi pada mode karakter, Kriptografi modern adalah kriptografi yang dalam penggunaannya beroperasi pada mode bit. Dalam kriptografi modern ini, baik *key*, *plaintext*, maupun *ciphertext* akan diproses dalam rangkaian bit alih-alih diproses sebagai karakter. Biasanya, kriptografi modern didasari pada teori-teori matematis dan memiliki ketahanan komputasional yang tinggi sehingga sulit dipecahkan oleh penyerang. Biasanya dalam kriptografi modern dibagi dua jenis dalam konteks kunci yang dipakai yaitu algoritma kunci simetris dan algoritma kunci publik.

## Algoritma Kunci Simetris

Algoritma ini menggunakan kunci yang sama pada proses enkripsi dan dekripsi. Contoh Algoritma yang termasuk algoritma kunci simetris seperti DES, Triple DES, AES, dan beberapa algoritma lainnya yang menggunakan [Feistel Network](https://www.youtube.com/watch?v=FGhj3CGxl8I).

![kunci-simetris](./resource/kunci-simetris.png)

## Algoritma Kunci Publik

Seperti yang telah dijelaskan pada [Materi 1 Kriptografi](../../Pertemuan%201/Materi1-Kriptografi/Readme.md). Pada algoritma kunci publik ini, kunci yang digunakan untuk melakukan enkripsi dan dekripsi merupakan kunci yang berbeda yang terdiri dari *public key* atau kunci yang bersifat publik dan boleh disebarluaskan dan *private key* atau kunci yang rahasia. Namun, meskipun kuncinya berbeda bukan berarti antara *public key* dan *private key* tidak memiliki keterkaitan satu sama lain.

![kunci-asimetris](./resource/kunci-asimetris.png)

Contoh dari algoritma yang menggunakan skema kunci ini adalah RSA, Diffie-Hellman dan ECC. Karena skema kunci algoritma ini lebih mahal secara komputational, biasanya digunakan sebagai salah satu algoritma yang digunakan dalam pertukaran kunci(*key exchange*) pada algoritma kunci simetris. Pada pertemuan kali ini, kita akan membahas lebih dalam lagi di algoritma kunci publik khususnya pada algoritma RSA dan beberapa teknik kriptanalisisnya dalam CTF.

## RSA

Rivest-Shamir-Addleman atau biasa disingkat menjadi RSA merupakan algoritma pertama yang menerapkan skema kunci publik secara menyeluruh. Pada RSA, keamanan yang dimiliki berkutat pada kesulitan untuk melakukan faktorisasi bilangan komposit yang sangat besar yang bisa dikatakan merupakan "hard problem" hingga sekarang. Meskipun merupakan Hard Problem, kenapa RSA masih memiliki banyak celah? Pada kasus ini, biasanya kelemahan RSA yang ada bukanlah dikarenakan algoritmanya yang lemah tetapi dikarenakan mudahnya kesalahan dalam implementasinya.

### Bagaimana RSA bekerja

Pada dasarnya, RSA bekerja dengan memanfatkan modular exponentiation. Modular expontiation sering digunakan dalam kriptografi dan bisa ditulis sebagai berikut.

```python
m ** e % n
```

atau

```python
pow(m, e, n)
```

Dalam algoritma RSA, dengan penggunaan modular expontiation dan faktorisasi bilangan prima memungkinkan algoritma ini bekarja dengan menciptakan *"trapdoor function"*. Fungsi *trapdoor* ini yang membuat RSA mudah untuk dihitung pada satu arah dan sulit untuk dilakukan reverse kecuali memiliki beberapa informasi yang terkait.  
#### Teori
- [Modular Exponentiation](https://en.wikipedia.org/wiki/Modular_exponentiation) (`m ** e % n`)
- [Prime Factorization](https://en.wikipedia.org/wiki/Integer_factorization) (`e*d`)
- [Phi Function](https://en.wikipedia.org/wiki/Euler's_totient_function) (`phi(n)`)
    - phi dari `n` adalah jumlah bilangan bulat yang tidak memiliki faktor sama yang lebih dari 1
- [Euler's Theorem](https://en.wikipedia.org/wiki/Euler's_theorem) (`m**phi(n) ≡ 1 mod n`)

```python
m ** e % n = c
```
dimana `c` merupakan _cipher text_, hasil dari enkripsi dengan RSA. Nilai `e` dan `n` merupakan bagian dari _public key_, nilai yang bisa diketahui siapa saja dan digunakan untuk enkripsi, dan `m` adalah plain text kita.

Lalu bagaimana cara kita untuk mengetahui nilai `m` apabila kita hanya memiliki _cipher text_ dan _public key_? Kita memerlukan nilai `d` agar kita bisa membuat persamaan `c ** d % n = m`. Dua persamaan yang ada bisa kita gabungkan menjadi `m ** ed % n = m`.

Jadi karena enkripsi ini bergantung pada nilai `e` dan `d`, kita harus bisa membuat nilai ini sulit diketahui oleh orang lain. Di sinilah kita gunakan faktorisasi prima. Untuk mendapatkan hasil kali 2 angka prima `e` dan `d` sangat mudah, namun untuk mendapatkan faktor dari angka prima sangat sulit.

Lalu dengan Euler's Theorem `m**phi(n) ≡ 1 mod n`, bisa kita ubah menjadi `m**(k*phi(n)+1) ≡ 1 mod n` dengan cara mengkalikan persamaan di kiri kanan dengan `k` dan mengkalikan persamaan di kiri dan kanan dengan `m`.Jadi sekarang kita bisa menemukan persamaan yang menggunakan `e*d`, yaitu `k*phi(n)+1` karena `m**ed mod n = m`. jadi `d = (k*phi(n)+1)/e`.
#### Contoh
p1 = 53
p2 = 59
n = p1 * p2 = 53 * 59 = 3127
phi(n) = phi(p1-1) * phi(p2-1) = 3016
untuk e kita pilih bilangan ganjil yang tidak memilih faktor yang sama dengan phi(n)
e = 3

Untuk penjelasan lebih lengkap ada di [video ini](https://www.youtube.com/watch?v=wXB-V_Keiu8)



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

Nth Root Attack dapat dilakukan ketika kita diberikan sebuah plaintext yang mana memiliki panjang yang cukup kecil dibandingkan dengan modulus N nya. Ketika nilai ```m ** e < N``` maka dengan melakukan akar pangkat n pada nilai c akan menghasilkan message itu sendiri. Sebagai contoh implementasinya sebagai berikut.

```python
from gmpy2 import *
from Crypto.Util.number import *

c = 369417535954737223911867465098263685847000
e = 3
n = 115792089237316195423570985008721211221144628262713908746538761285902758367353

m = int(iroot(c,3)[0])
print(long_to_bytes(m))
```

Outputnya sebagai berikut.
```
ABCDEF
```

### Wiener Attack

Berkebalikan dengan nth root attack, ketika nilai e cukup besar justru ada kemungkinan bahwa nilai d menjadi semakin kecil dimana sesuai dengan persamaan ```ed = k * phi(n) + 1```. Dari hal tersebut, dengan menggunakan Teori Wiener, penyerang dapat menghitung nilai d dengan efektif ketika nilai ```d < (1/3) n ** 4```. Untuk implementasi sederhana dari wiener attack bisa kita gunakan sebuah library bernama owiener pada python yang bisa diinstal pada [link ini](https://github.com/orisano/owiener) atau sebagai berikut.

```python
import owiener

e = 30749686305802061816334591167284030734478031427751495527922388099381921172620569310945418007467306454160014597828390709770861577479329793948103408489494025272834473555854835044153374978554414416305012267643957838998648651100705446875979573675767605387333733876537528353237076626094553367977134079292593746416875606876735717905892280664538346000950343671655257046364067221469807138232820446015769882472160551840052921930357988334306659120253114790638496480092361951536576427295789429197483597859657977832368912534761100269065509351345050758943674651053419982561094432258103614830448382949765459939698951824447818497599
n = 109966163992903243770643456296093759130737510333736483352345488643432614201030629970207047930115652268531222079508230987041869779760776072105738457123387124961036111210544028669181361694095594938869077306417325203381820822917059651429857093388618818437282624857927551285811542685269229705594166370426152128895901914709902037365652575730201897361139518816164746228733410283595236405985958414491372301878718635708605256444921222945267625853091126691358833453283744166617463257821375566155675868452032401961727814314481343467702299949407935602389342183536222842556906657001984320973035314726867840698884052182976760066141
d = owiener.attack(e, n)
print(d)
```

Outputnya sebagai berikut.

```STDOUT
4221909016509078129201801236879446760697885220928506696150646938237440992746683409881141451831939190609743447676525325543963362353923989076199470515758399
```

Terlihat dengan menggunakan penyerangan Wiener, kita tidak perlu melakukan faktorisasi terhadap kunci publik n.

### Common Modulus Attack


