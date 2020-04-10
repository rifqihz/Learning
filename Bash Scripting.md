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

# jika umur lebih dari 80 maka print anda tidak boleh menyetir
if [ $umur -gt 80 ]; then 
  echo "Anda tidak boleh menyetir"
# jika umur lebih dari 17 dan kurang dari 80 maka print anda boleh menyetir jika sudah memiliki SIM
elif [ $umur -ge 17 ]; then
  echo "Anda boleh menyetir jika sudah memiliki SIM"
# jika umur selain keterangan diatas maka print Anda belum memiliki SIM
else 
  echo "Anda belum memiliki SIM"
fi
```

### Operasi Boolean
Apabila kita perlu untuk melakukan pengecekan beberapa kondisi maka kita dapat menggunakan operasi logika boolean. Terdapat dua logika operasi boolean, yaitu 
1) operasi **and** ( && )
Operasi 'and' akan bersifat benar apabila **semua kondisi** yang memiliki syarat 'and' benar
1) operasi **or**  ( || )
Operasi 'or' akan bersifat benar apabila **salah satu kondisi** yang memiliki syarat 'or' benar

Contoh :
```bash
#!/bin/bash

a=5

if [ $a -gt 10 ] && [ ech$[a%2] == 1 ] ; then
  echo "semua pernyataan benar"
elif [ $a -le 10 ] || [ $[a%2] == 1 ] ; then
  echo "salah satu pernyataan benar"
else
  echo "Tidak ada yang benar"
fi
```

### Switch case
Switch case biasanya digunakan apabila kita ingin melakukan cek kondisi yang spesifik. Contoh :
```bash
#!/bin/bash

read -p "Sistem operasi yang dipakai? :" os

# setiap selesai case diberi ;; dan apabila selesai ditutup dengan esac

# yang akan di cek adalah var os
case $os in
# apabila os sama dengan Windows maka print biasa
"windows")
        echo "Biasa"
        ;;
# apabila os sama dengan Mac maka print Better 
"Mac")
        echo "Better"
        ;;
# apabila os sama dengan Linux maka print Best 
"Linux")
        echo "Best"
        ;;
# apabila os tidak sama dengan yang terdapat di pilihan maka print OS apa tuh
*)
  echo "OS apa tuh?"
  ;;
esac
```

## Looping
### While Loop
While loop merupakan looping atau perulangan yang cukup mudah. Yaitu apabila suatu kondisi bernilai benar maka akan dilakukan suatu perintah berulang-ulang. Pada penggunaan While loop tidak ada batas looping tertentu, sehingga ini cocok dilakukan apabila kita tidak tau berapa kali kita akan melakukan looping. Format :
```bash
while [ kondisi ] ; do
  aksi
done

# atau
while [ kondisi ] 
do
  aksi
done
```

Contoh :
```bash
#!/bin/bash

i=1

# jika i <= 10
while [ $i -le 10 ]; do
# maka print i dan nilai i berubah menjadi i + 1
  echo "$i"
  i=$((i + 1))
done;
# menampilkan 1 sampai 10
```

### Until Loops
Until loops mirip dengan while loops perbedaannya adalah pada kondisinya apabila while loops akan berhenti jika **false** , maka until loops akan berhenti jika **true**. Format Until loops sama dengan while loops. Contoh : 

```bash
#!/bin/bash

i=1

# Perbedaannya dengan while loops terletak di -ge
# jika while loops akan berhenti jika i lebih dari 10 (kondisi false)
# until loop akan berhenti jika i lebih dari 10 (kondisi true)
# jika i >= 10
while [ $i -ge 10 ]; do
# maka print i dan nilai i berubah menjadi i + 1
  echo "$i"
  i=$((i + 1))
done;
# menampilkan 1 sampai 10
```

### For loops
For loops berbeda dengan looping sebelumnya, pada for loop terdapat batas awal dan akhir dari looping. Sehingga for-loop dilakukan apabila kita mengetahui berapa kali kita melakukan looping. Format :
```bash
#!/bin/bash

for variabel in jangkauan; do
  aksi
done

# atau

for variabel in jangkauan
do
  aksi
done

```

Contoh 1:
```bash
#!/bin/bash

names="John Wick"

# Akan menampilkan setiap kata dari variabel nama
for name in $names ; do
  echo $name
done
```
Output :
```
John
Wick
```

Contoh 2:
```bash
#!/bin/bash

# Menampilkan angka ganjil dari 1 sampai 10

# {1..10} berarti i = 1 sampai i = 10
for i in {1..10}; do
# apabila genap maka akan dilewati
  if [ $[i % 2] == 0 ]; then
    continue;
  else
    echo "$i"
  fi    
done
```
Output :
```
1
3
5
7
9
```

### Break dan Continue
`break` berfungsi untuk menghentikan atau keluar dari looping secara paksa dan `continue` berfungsi untuk melewati suatu aksi pada kondisi tertentu. Contoh :
```bash
#!/bin/bash

# range 1 sampai 20
for i in {1..20}; do
  # jika i bernilai 15 maka looping dihentikan
  if [ $i -eq 15 ]; then
    break
  fi
  # jika i bernilai ganjil maka akan dilewati
  if [ $[i % 2] == 1 ];then
    continue
  else
    echo "$i"
  fi
done  
``` 

### Select
Mekanisme `select` dapat membuat sebuah sistem menu yang simpel. Format :
```bash
#!/bin/bash

select variabel in jangkauan
do
  aksi
done
```
Contoh :
```bash
#!/bin/bash

names="Farrah Klarybel Merris Judyanna Lubenah"

PS3="Choice : "

select name in $names
do
  if [ $name == "Lubenah" ]; then
    break
  fi
  echo "$name"
done
echo "Done"
```
Output :
```
1) Farrah
2) Klarybel
3) Merris
4) Judyanna
5) Lubenah
Choice : 1
Farrah
Choice : 2
Klarybel
Choice : 3
Merris
Choice : 4
Judyanna
Choice : 5
Done
```
**Note** : PS3 merupakan variabel untuk menampilkan perintah input, defaultnya bernilai **#?**, sehingga dapat diganti terlebih dahulu.

## Functions
Fungsi sangatlah diperlukan untuk reuse atau menggunakan kembali suatu script. Fungsi sangat berguna apabila membuat suatu program yang kompleks dan butuh untuk memanggil suatu fungsi berulang ulang. 

### Fungsi
Membuat fungsi cukup mudah, formatnya yaitu :
```bash
nama_fungsi () {
  aksi
}

# atau

function nama_fungsi {
  aksi
}
```

Contoh :
```bash
#!/bin/bash
fungsi () {
  echo "Hello World"
}

fungsi
```
Output :
```
Hello World
```

### Argumen
Untuk pemrograman yang lebih interaktif terkadang kita memerlukan adanya argumen pada fungsi, kita dapat menggunakan argumen tersebut untuk berbagai keperluan. Contoh :
```bash
#!/bin/bash

# Fungsi
gender () {
# Apabila argumen kedua bernilai male maka Mr
  if [ $2 == "male" ]; then 
    echo "Hello , Mr $1"
# Apabila argumen kedua bernilai female maka Mrs
  elif [ $2 == "female" ]; then 
    echo "Hello , Mrs $1"
# Apabila argumen kedua selain itu maka kosong
  else 
    echo "Hello , $1"
        fi      
}

# inputan user 2 kali input pertama disimpan pada variabel a dan input kedua pada variabel b
read -p "Input your name and gender : " a b

# nilai variabel a menjadi argumen pertama dan nilai variabel b menjadi argumen kedua
gender $a $b

```

### Fungsi dengan Nilai Kembalian
Terkadang kita memerlukan fungsi yang berfungsi hanya untuk mengembalikan nilai bukan langsung melakukan print nilai tersebut. Contoh :

```bash
#!/bin/bash
panjang_nama () {
  return ${#1}
}

read -p "Masukkan nama anda : " nama
panjang_nama $nama
echo "Panjang nama anda adalah : $?"
```

**Note** : Argumen yang digunakan adalah argumen 1 yang mana argumen setelah tanda spasi akan dinilai sebagai argumen 2 dan seterusnya.

### Variabel Lokal 
Variabel lokal adalah suatu variabel yang hanya bisa digunakan di dalam suatu lingkup perintah atau fungsi. Contoh :
```bash
#!/bin/bash

variabel () {

# var1 berisi kata "var lokal
  local var1="var lokal"
  var2="var global"
        echo "Di dalam fungsi"
  echo "isi var1 : $var1 , isi var 2: $var2"
}

variabel

# Disini var1 tidak ada isinya karena var 1 merupakan variabel lokal yang isinya hanya berlaku di dalam fungsi 'variabel' saja
echo "Di luar fungsi"
echo "isi var1 : $var1 , isi var 2: $var2"
```

Output :
```
Di dalam fungsi
isi var1 : var lokal , isi var 2: var global
Di luar fungsi
isi var1 :  , isi var 2: var global
```

### Fungsi Override
Ini berfungsi untuk membuat suatu fungsi dengan nama sama namun memiliki parameter atau output yang berbeda. Contohnya :

```bash
#!/bin/bash
# menimpa fungsi 'date' yang sebelumnya sudah ada dengan fungsi 'cal'
date () {
  cal
}
date
# fungsi date yang seharusnya outputnya adalah waktu berubah menjadi memanggil fungsi cal
```

## Source
- https://ryanstutorials.net/bash-scripting-tutorial/








