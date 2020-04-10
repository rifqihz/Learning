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
**@** | Semua argumen yang dimasukkan ke Bash script
**USER** | Username dari user yang menjalankan script
**HOSTNAME** | nama host dari script yang berjalan
**SECONDS**  | waktu(detik) sejak script dijalankan
**RANDOM** | Angka acak 
**LINENO** | Baris variabel ini pada scipt

Cara membuat variabel baru secara manual yaitu dengan format 
```nama_variabel=nilai```
. Tanpa ada spasi pada tanda "=". 
#### Contoh :
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
Apabila kita mempunyai suatu variabel maka kita dapat mengecek panjang dari variabel tersebut dengan format : ```${#variabel}. Kita dapat menggunakannya untuk mengetahui panjang dari kalimat maupun angka. Contohnya :
```bash
#!/bin/bash

a="Ini adalah string"
echo "${#a} #17

b=16423
echo "${#b} # 5
```

## If Statement





















