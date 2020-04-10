# Bash Scripting
## Pendahuluan
Shell adalah program yang menjembatani user dengan sistem operasi, kernel. Umumnya disediakan shell sebagai user interface. Selain itu shell memungkinkan user untuk menyusun sekumpulan perintah atau beberapa file untuk dieksekusi sebagai program. Untuk Bash format file yang digunakan adalah .sh.

## Shebang (!#)
Shebang diletakkan pada awal script. Script selanjutnya menjelaskan tentang intrepeter yang akan digunakan untuk menginterpretasikan script sesudahnya. Format Shebang untuk bashscripting adalah `#!/bin/bash` dimana path yang akan digunakan adalah path untuk Bash.

## VIM (optional)
Cara mendownload pada ubuntu yaitu dengan perintah 
```bash
$ sudo apt-get install vim
```

Buat file (misal nama filenya hello) dengan format (.sh) dan edit dengan VIM dengan perintah
```bash
$ vim hello.sh
```

## Print
Untuk melakukan print (menampilkan output di layar) kita dapat menggunakan perintah `echo`. Contohnya pada script berikut :
```bash
#!/bin/bash
echo "Hello World"
```
## Comment
Membuat komentar dengan tanda `#`. Format membuat komentar pada script :
```bash
#!/bin/bash
# isi komentar 
```

## Variabel
Dalam menggunakan variabel kita dapat membuat variabel baru atau menggunakan variabel yang sudah disediakan oleh sistem./
Variabel-variabel yang sudah disediakan oleh sistem antara lain :
Command | Isi
------- | ------
**$0** | Nama dari Bash Script
**$1 - $9** | 9 argumen pertama pada Bash Script
**$#** | Jumlah argumen yang dimasukkan ke Bash Script
**$$** | PID (Process ID) dari script yang dijalankan
**$@** | Semua argumen yang dimasukkan ke Bash script
**$USER** | Username dari user yang menjalankan script
**$HOSTNAME** | nama host dari script yang berjalan
**$SECONDS**  | waktu(detik) sejak script dijalankan
**$RANDOM** | Angka acak 
**$LINENO** | Baris variabel ini pada scipt

Cara membuat variabel baru secara manual yaitu dengan format 
```nama_variabel=nilai```
. Tanpa ada spasi pada tanda "=". 
Contoh inisialisasii:
```bash
#!/bin/bash
name=Zhafrant
```
Contoh penggunaan variabel :

```bash
#!/bin/bash

#Menampilkan nama script dan PID
echo "Nama script ini adalah $0 , PID dari script ini adalah $$"

#Menampilkan baris
echo "Ini merupakan baris ke $LINENO"

#Menampilkan jumlah argumen yang dimasukkan
echo "Jumlah argumen yang dimasukkan adalah $#"

# -n berfungsi agar date diprint di baris yang sama
echo -n "Tanggal hari ini :" ; date

# cal untuk menampilkan kalender
echo "Tampilkan kalender"
cal

#inisialisasi variabel num1 dan num2 dengan argumen 1 dan argumen 2
num1=$1
num2=$2

# menampilkan hasil penjumlahan num1 dan num2
echo " $num1 + $num2 = $(( num1 + num2 )"
```
## Input
### Meminta Inputan dari user
Kita dapat menggunakan perintah `read`, contohnya :
```bash
echo "masukkan nama anda"
read nama
echo "nama anda adalah $nama"
```
masukan dari user akan tersimpan dalam variabel 'nama'.\
Selain itu terdapat beberapa opsi lain dalam menggunakan `read`. Opsi tersebut adalah `-p` dan `-s`. opsi `-p` menspesifikan inputan dan dan opsi `-s` untuk menyembunyikan inputan user. Contoh :
```bashshell
#!/bin/bash

# Di terminal akan menampilkan kalimat "Masukkan username : " lalu meminta input dari user
# Inputan yang diketik oleh user terlihat di layar.
# Setelah itu inputan tersebut disimpan pada variabel userx
read -p "Masukkan username : " userx

# Di terminal akan menampilkan kalimat "Masukkan username : " lalu meminta input dari user
# Inputan yang dimasukkan tidak ditampilkan di layar sehingga terlihat seperti tidak terjadi apa-apa.
# Setelah selsai memasukkan data maka data tersebut akan disimpan di variabel pwdx
read -sp "Masukkan password : " pwdx

```

### Lebih Banyak Inputan
Apabila kita ingin melakukan inputan lebih banyak maka kita dapat menambahkaan lebih banyak variabel baru setelah `read`. Contoh :
```bash
#!/bin/bash

# Inputan pertama akan disimpan di variabel num1 
# Inputan kedua akan disimpan di variabel num 2 begitu seterusnya
read -p "Masukkan 5 angka : " num1 num2 num3 num4 num5

# Jumlah num1 num2 num3 num4 dan num5 disimpan di variabel total
total = $((num1+num2+num3+num4+num)) # 25

echo "angka pertama : $num1"
echo "angka kedua   : $num2"
echo "angka ketiga  : $num3"
echo "angka keempat : $num4"
echo "angka kelima  : $num5"

echo "total = $total" 
````

## Aritmatika
### Operasi aritmatika dalam bash
Tabel operasi aritmatika yang umumnya digunakan :
Operator | Operasi Hitung 
-------- | --------------
+ | Penjumlahan
- | Pengurangan
* | Perkalian
/ | Pembagian
var++ | nilai variabel ditambah 1
var-- | nilai variabel dikurang 1
% | modulus

### Let
Untuk melakukan fungsi aritmatika sederhana kita dapat menggunakan fungsi yang sudah disediakan oleh Bash yaitu `let`. Formatnya yaitu ```let fungsi_aritmatika```. Contoh penggunaan `let` :
```bash
#!/bin/bash

let x=24+16
echo "$a" # 40

let x=173%6
echo "$x" # 5
```

### Expr
`expr` mirip dengan `let` letak perbedaannya adalah apabila `let` hasil operasi aritmatika disimpan pada variabel, pada fungsi `expr` hasil operasi matematika **tidak disimpan** melainkan langsung ditampilkan di layar. Contoh penggunaan `expr` :
```bash
#!/bin/bash

# Harus terdapat spasi antara item dan tidak ada tanda petik
expr 63+17   # menampilkan "63+17
expr 63 + 17 # menampilkan 80

expr "63 + 17" # menampilkan "63 + 17"

expr 77 % 4 # menampilkan 1

# expr digunakan di dalam perintah substitusi dimana hasil perhitungan akan di simpan di variabel x
x=$( expr 4 * 5 )
echo "$x"
```
### Double Parentheses
Kita dapat menggunakan dobel kurung untuk melakukan operasi aritmatika. Format : ```$(( ekspresi ))```. Dimana umumnya terdapat spasi pada setiap kurungnya. Contoh :
```bash
#!/bin/bash

a=$(( 3 * 4 ))
echo "$a" # 12

a=$((4+5))
echo "$a" # 9

b=$(( $a + 5))
echo "$b" # 14

```

### Panjang dari suatu Variabel
Apabila kita mempunyai suatu variabel maka kita dapat mengecek panjang dari variabel tersebut dengan format : ```${#variabel}```. Kita dapat menggunakannya untuk mengetahui panjang dari kalimat maupun angka. Contohnya :
```bash
#!/bin/bash

a="Ini adalah string"
echo "${#a} #17

b=16423
echo "${#b} # 5
```

## Kontrol Percabangan
Di dalam pemrograman terdapat beberapa melakukan percabangan, seperti if-else, nested if, switch case dan ternary. Pada Bash Scripting kita juga dapat membuat kontrol percabangan. Hal ini akan memudahkan kita untuk menentukan mana aksi yang dikerjakan dan mana yang tidak.
### 'If' Dasar
Dalam pemrograman salah satu percabangan menggunakan 'if statement'. Dalam Bash untuk melakukan if maka diperlukan 'kondisi' dan 'aksi'. Format untuk membuat pernyataan if di Bash, sebagai berikut :
```bash
#!/bin/bash

# diberi spasi setelah if dan setiap kurung siku diberi jarak

# apabila penulisan then sejajar dengan if maka diperlukan ';'
if [ kondisi ]; then
  aksi
fi

# Atau

if [ kondisi ]
then
  aksi
fi

```
Pada Bash Scirpting pernyataan if ditutup menggunakan 'fi'. Contoh penerapannya :
```bash
#!/bin/bash

# Menampilkan di layar setelah itu inputan tersembunyi lalu disimpan di variabel pswd
read -sp "Masukkan password : "  pswd

# jika pswd sama dengan 'linux' maka print 'Password Benar'
if [ pswd == "Linux ]; then
  `echo "Password Benar"
fi

```
### Kondisi yang umum digunakan
Operator | Deskripsi
-------- | ------
!kondisi | Jika fungsi bernilai salah maka..
-n String | Panjang String lebih dari 0
-z String | Panjang Strring adalah 0
string1 == string2 | nilai string1 sama dengan nilai string2
string1 != string2 | nilai string1 tidak sama dengan nilai string2
int1 -eq int2 | nilai int1 sama dengan nilai int2
int1 -ge int2 | nilai int1 lebih dari sama dengan nilai int2
int1 -le int2 | nilai int1 kurang dari sama dengan nilai int2
int1 -ge int2 | nilai int1 lebih dari nilai int2
int1 -le int2 | nilai int1 kurang dari nilai int2
-d file | file tersebut ada dan merupakan direktori
-e file | file tersebut ada 
-r file | file tersebut ada dan ada izin untuk membaca file 
-s file | file tersebut ada dan memiliki isi (ukurannya lebih dari 0)
-w file | file tersebut ada dan ada izin untuk mengedit file
-x file | file tersebut ada dan ada izin untuk mengeksekusi file

### If Bersaran (Nested if)
If bersarang merupakan kondisi dimana di dalam suatu if terdapat if yang lainnya. If bersarang biasanya digunakan pada kondisi dimana diperlukan lebih dari satu pengecekan kondisi. Contoh :
```bash
#!/bin/bash

# Menampilkan ke layar setelah itu mengambil inputan dan dimasukkan ke dalam variabel usrnm
read -p "Username : " usrnm

# Menampilkan di layar setelah itu inputan tersembunyi lalu disimpan di variabel paswd
read -sp "Password : " paswd


if [ $usrnm == "Admin" ]; then
  if [ $paswd == "Admin" ]; then
  # Jika usrnm dan paswd benar maka print selamat datang
    echo "Selamat Datang"
  fi
fi
```

### If-Else
If-else biasa digunakan apabila suatu kondisi bernilai salah dan diperlukan tindakan terhadap kondisi yang bernilai salah tersebut. Contoh :
```bash
#!/bin/bash

# Menampilkan ke layar setelah itu mengambil inputan dan dimasukkan ke dalam variabel angka
read -p "Masukkan satu angka random : " angka

# Program ganjil genap
if [ $[angka % 2] == 1 ]; then
# Jika true maka akan print ganjil
  echo "$angka merupakan bilangan ganjil"
else
# Jika false maka akan print genap
  echo "$angka merupakan bilangan genap"
fi
```
### If-Elif-Else
If-Elif-Else biasa digunakann untuk program yang lebih kompleks. Contoh :
```bash
#!/bin/bash

# inputan user
read -p "Berapa umurmu" umur

# jika umur lebih dari 
if [ $umur > 80 ]; then 
  echo "Anda tidak boleh menyetir"
elif [ $umut > 17 ]; then
  echo "Anda boleh menyetir jika sudah memiliki SIM"
else 
  echo "Anda belum memiliki SIM"



Contoh penggunaan : 
```bash
#!/bin/bash

# membuat file bernama file1
touch file1
# membuat direktori bernama dir1
mkdir dir1


file=file1
dir=dir1

if [ -d file1 ]; then
  echo "$file1 adalah";
```  


























