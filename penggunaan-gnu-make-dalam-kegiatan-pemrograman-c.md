---
layout: post
title: Penggunaan GNU Make dalam Kegiatan Pemrograman C
---

## Pengantar
Bagi orang-orang yang melakukan pengembangan sebuah  perangkat lunak di lingkungan apapun itu, Linux / Unix like systems atau Windows. Dan menggunakan bahasa pemrograman apapun itu. Pastinya membutuhkan tool / alat bantu untuk menggabungkan semua source code yang telah disusun sehingga menjadi satu kesatuan perangkat lunak yang siap dijalankan pada komputer.

Apa yang telah disampaikan diatas adalah sebuah proses, dan proses tersebut biasanya dikenal dengan istilah "Build". Di dalam proses build terdapat kegiatan compile dan linking. Alat-alat untuk melakukan proses build disebut dengan Build Tools. Banyak sekali ada produk-produk build tools. Salah satunya adalah GNU Make.

## Tujuan
Sesuai dengan judul dari tulisan ini, mengenalkan dan mengajarkan dasar-dasar penggunaan GNU Make dengan pendekatan praktis sehingga pembaca memiliki kemampuan minimal untuk melakukan proses build menggunakan GNU Make dengan fitur-fitur yang minimal juga. Sehingga sangat memudahkan kita dalam kegiatan compiling dan linking sebuah program. Sama seperti realita si penulis yang juga baru punya kemampuan minimal dalam penggunaan GNU Make.

Untuk melakukan proses build tentunya harus ada sekumpulan source code yang akan di-build. Jika tidak ada source code, tentunya GNU Make tidak akan berguna karena tidak ada yang di-build. Oleh karena itu kita akan menulis program kecil-kecilan sebangsa "Hello World". Bahasa pemrograman yang dipakai adalah bahasa pemrograman C ANSI menggunakan compiler GCC.

## Persiapan
Untuk dapat mempraktekkan semua hal yang ada di tulisan ini, anda harus memastikan beberapa hal berikut sudah terjadi, yaitu:

* Ada komputer yang bisa menyala dan bisa anda gunakan.
* Menyukai bahasa pemrograman C
* Mengenal dan mengerti cara yang dasar meng-compile source code C menggunakan GCC sehingga menjadi sebuah executable program.
* Di komputer tersebut terinstall sistem operasi Linux. Distro bebas.
* Di dalam sistem operasi Linux anda sudah terinstall paket-paket pengembangan yang lengkap. Umum dikenal dengan nama devel-packages.

Di internet banyak sekali tutorial cara-cara untuk install paket-paket development secara lengkap. Silahkan cari sendiri sesuai dengan distro linux yang anda pakai, melalui mesin-mesin pencari favorit anda. Keywordnya kira-kira seperti ini:
`linux debian how to install complete full development packages`

Ketikkan perintah-perintah berikut di terminal untuk test bahwa paket-paket development yang dibutuhkan sudah terinstall.

* `cc --version`
* `gcc --version`
* `make --version`


## Dasar-dasar GNU Make
Program build tool GNU Make adalah berupa perintah bernama `make`. Lalu, bagaimana GNU Make bekerja? atau bertingkah? Untuk mengetahuinya, mari kita membuat program yang super kecil dan sederhana yang bertujuan hanya untuk mengetahui bagaimana flow kerjanya si GNU Make. Let's go!

Kita namakan file source code kita dengan nama `latihan1.c` dan berikut source codenya. Atau jika anda ingin berkreasi source code sendiri silahkan, yang penting ikuti langkah-langkah untuk menggunakan program `make` nya.

```c
/*
* latihan1.c
* source code ini copy-paste dari sebuah
* thread di stackoverflow
*/
#include <stdio.h>
#include <time.h>

void what_time_is_it()
{
    time_t timer;
    char buffer[26];
    struct tm *tm_info;

    time(&timer);
    tm_info = localtime(&timer);

    strftime(buffer, 26, "%H:%M:%S", tm_info);
    puts(buffer);
}

int main (int argc, char *argv[])
{
    printf("Haayy saya sedang belajar GNU Make!\n");
    printf("by the way, jam berapa ya sekarang? \n");
    printf("Ok.. sekarang jam ");
    what_time_is_it();

    return 0;
}

```
Karena kita belajar GNU Make maka kita pakai perintah `make` untuk compile source code program diatas. Di terminal pastikan anda berada di direktori langsung yg menampung file `latihan1.c` lalu jalankan perintah berikut di terminal:

`make`

Ahhh error sodaraa..sodaraa.. mengapa error? Karena program `make` tidak menemukan soulmate nya yaitu sebuah file bernama `Makefile`. Ok, coba lagi dengan menjalankan perintah berikut:

`make latihan1`

Tarrraaaa terciptalah sebuah file executable bernama `latihan1`. Siap dieksekusi dengan cara `./latihan1` .

Mari coba dengan perintah yang lebih berkombinasi. Jalankan lagi dengan perintah berikut:

`CC="gcc" CFLAGS="-Wall" make latihan1`

Dari output message yang dihasilkan anda bisa simpulkan perbedaannya dengan perintah make yang tanpa kombinasi. Lalu bagaimana flow kerjanya si make ini **TANPA** `Makefile` ? Berikut adalah penjelasannya disadur dari http://c.learncodethehardway.org/book/ex2.html. Berikut flow tanpa Makefile:

* Apakah sudah ada file `latihan1` sebelumnya?
* Tidak ada. Ok, lalu apakah ada file lainnya yang nama filenya dimulai dengan `latihan1`
* Ya, ada. Nama filenya `latihan1.c` . Apakah GNU Make mengetahui cara untuk mem-build file dengan ektensi `.c` ?
* Ya, tentu! Lalu GNU Make otomatis menjalankan perintah `cc latihan1.c -o latihan1`
* GNU Make menggunakan perintah compiler `cc` untuk mem-build executable file program dari source code `latihan1.c`

### Makefile
Adalah sebuah file yang berfungsi sebagai database referensi / informasi untuk agar si program `make` mengetahui apa-apa saja yang harus dia lakukan dalam proses build.

Seperti apa isi dari file Makefile? Mari kita lihat contoh susunan file Makefile berikut supaya anda punya bayangan.

![Makefile introduction](http://res.cloudinary.com/okaprinarjaya/image/upload/v1437314360/makefile_explain_trffcr.png)

Atau anda bisa ber-eksplorasi dengan iseng membuka file Makefile nya project software-sofware open-source di github atau bitbucket. Beberapa contoh project software-sofware open-source yang bisa dipelajari Makefile nya adalah:

1. https://github.com/antirez/redis/blob/unstable/src/Makefile
2. https://github.com/haproxy/haproxy/blob/master/Makefile
3. https://github.com/arduino/Arduino/blob/master/hardware/arduino/avr/firmwares/atmegaxxu2/arduino-usbserial/makefile

"Wowww..seremm banget baaanggg! ruwet bacanya!". Hahaha yaa iseng aja baca supaya keren. Lalu ber-doa, ber-ikhtiar, dan latihan latihan latihan terus agar suatu saat nanti anda bisa membuat software-sofware seperti diatas. Tentunya dengan semangat kolaborasi dan sinergi ya!

Di dalam file `Makefile` terdapat susunan informasi yang salah satunya disebut dengan RULES dan merupakan susunan informasi yang mendasar sekaligus utama. RULES memiliki pola standar dan di dalam pola itu ada item-item berikut ini:

1. TARGET
2. PREREQUISITES
3. RECEIPES

Setelah RULES, satu lagi susunan informasi yang mendasar yang akan saya cover selanjutnya adalah:

* VARIABLES

dan masih ada banyak lagi susunan informasi yang lain, tapi tidak saya jelaskan disini. Susunan informasi yang lain akan langsung saja dipakai (tiba-tiba muncul) tanpa ada penjelasan khusus.

#### Target
Ibaratkan sebuah proses memasak, kita harus mengetahui terlebih dahulu kita ingin membuat / memasak menu apa? Tempe orek? sayur asem? nasi goreng? tahu isi goreng? atau hanya sekedar telor ceplok. Terserah anda mau menghasilkan menu apa.

Dalam konteks GNU Make pada kegiatan pemrograman C, secara umum, target atau apa yang ingin kita hasilkan adalah biasanya file-file object yang ber-ektensi `.o` dan file executable dari program kita.

#### Prerequisites
Ibaratkan sebuah proses memasak, setelah kita mengetahui ingin memasak menu apa, selanjutnya kita butuh daftar bahan-bahan baku dari menu yang ingin kita masak. Umpamanya kita ingin memasak menu gado-gado. Apa saja bahan-bahan baku untuk membuat menu gado-gado? Tentunya ada kacang tanah, bawang putih, gula aren, cabe, ketupat, dan lain-lain.

Dalam konteks GNU Make pada kegiatan pemrograman C, maka bahan-bahan baku dari sebuah file object itu apa saja? kita perlu ketahui itu. Sebagai contoh, file object `hitung.o` bahan-bahannya atau dependency nya adalah file-file berikut: `hitung.c`, `ukur.h`, `timbang.h`, `debug.h`.

#### Receipes
Ibaratkan sebuah proses memasak, setelah kita mengetahui bahan-bahan baku dari menu yang ingin kita masak, maka selanjutnya adalah bagaimana cara memasaknya? bagaimana urutannya? bahan mana yang harus pertamakali diolah? Umpamanya kita memasak menu gado-gado, pertama-tama kacang tanah digoreng hingga matang, lalu kacang tanah yang sudah matang diulek untuk dihaluskan, masukkan bawang putih, ulek lagi, dan seterusnya hingga menjadi sebuah menu gado-gado yang siap untuk dimakan.

#### Variables
Informasi Variables adalah sama dengan variable-variable yang ada pada sebuah bahasa pemrograman. Ada nama variable, dan ada nilai dari variable. Setelah variable di-deklarasikan maka selanjutnya bisa diakses.

Contoh deklarasi:

```
CC = gcc
SRC_DIR = src
VAR_SUKA_SUKA_GUE = value suka suka gue
```

Cara Mengakses variable yang telah dideklarasikan:

```
$(CC)
$(SRC_DIR)
$(VAR_SUKA_SUKA_GUE)
```

### Mulai Menyusun Makefile yang Sederhana
Baik, supaya anda tidak bingung dan mulai takut dengan GNU Make, mari kita mulai untuk menulis Makefile yang sederhana. Dan mari kita lihat dulu pola dasarnya seperti berikut ini:

```
VARIABLE1 = value variable1
VARIABLE2 = value variable2
VARIABLE_X = value variable_X

target : prerequiesites
    receipe1
    receipe2
    receipeX
```

Indentasi dari baris **receipes** adalah HARUS menggunakan character TAB. Jika anda menggunakan spasi 4x maka dijamin ERROR!.

#### Makefile Latihan 1
Baik, Berikut ini adalah the real Makefile yang sudah bisa di-test dijalankan melakukan proses build sebuah program. Silahkan disalin dengan diketik ulang. Berikut Makefile nya:

![Makefile Excercise 1](http://res.cloudinary.com/okaprinarjaya/image/upload/v1437468778/Makefile-excercise1_ximqge.png)

Jika anda telah selesai menyalin file Makefile diatas, lalu lanjutkan dengan menyusun source code program sederhana.

#### Source Code Latihan 1
Lalu, berikut adalah file-file source code dari program sederhana yang nanti akan di-build oleh program `make` berdasarkan informasi file Makefile latihan 1 diatas. Buatlah sebuah direktori baru bebas namanya, contoh bernama `latihan-gnu-make` di mana saja sesuka anda. Contoh di: `/home/nama_user_anda/latihan-gnu-make`. Dan di dalam direktori `latihan-gnu-make` terdapat file-file berikut ini:

* `bebas.h`
* `db.h`
* `dbg.h` https://gist.github.com/okaprinarjaya/422b85131cbe0d3538f3
* `myread.h` https://gist.github.com/okaprinarjaya/72ada6da34eae4e4fd5e#file-myread-h
* `bebas.c`
* `db.c`
* `myread.c` https://gist.github.com/okaprinarjaya/72ada6da34eae4e4fd5e#file-myread-c
* `great-software.c`
* `Makefile`

**File bebas.h , db.h , bebas.c , db.c , great-software.c adalah file-file yang wajib anda salin ulang dengan mengetik ulang. File-file yang lainnya saya sediakan di gist github.**

Berikut ini adalah file-file source code yang perlu ketik ulang:

`bebas.h`

![](http://res.cloudinary.com/okaprinarjaya/image/upload/v1437475870/src-bebas-h_cavtu6.png)

`db.h`

![](http://res.cloudinary.com/okaprinarjaya/image/upload/v1437475872/src-db-h_glxmkg.png)

`bebas.c`

![](http://res.cloudinary.com/okaprinarjaya/image/upload/v1437472898/src-bebas-c_vfruho.png)

`db.c`

![](http://res.cloudinary.com/okaprinarjaya/image/upload/v1437475412/src-db-c_gtbpi5.png)

`great-software.c`

![](http://res.cloudinary.com/okaprinarjaya/image/upload/v1437475656/src-great-soft-c_q2xqa4.png)

Jika anda telah menyusun Makefile dan semua source code dari program sederhana yang dibuat, maka anda sudah bisa menjalankan perintah berikut ini untuk melakukan proses build. Melalui terminal PASTIKAN anda berada di direktori utama dari file-file source code. Contoh anda berada di: `/home/nama_user_anda/latihan-gnu-make`. Berikut perintah yang harus dijalankan:

`make`

Ya! cuma satu perintah itu dan sudah pernah dibahas diatas. Hanya saja sebelumnya perintah `make` tanpa parameter apapun menghasilkan error karena tidak ada file Makefile. Sekarang situasinya adalah sudah ada Makefile dan program GNU Make bekerja sesuai informasi yg ada di dalam file Makefile.

Jalankan program executable hasil dari proses build dengan perintah berikut:

`./great-software`

Proses build menghasilkan file-file object `.o` dan file executable dari main program. Berikut file-file yang dihasilkan

* `bebas.o`
* `db.o`
* `great-software.o`
* `myread.o`
* `great-software` (executable)

Untuk menghapus semua file hasil proses build cukup jalankan perintah:

`make clean`

Bayangkan! tanpa GNU Make, anda harus mengetikkan perintah-perintah berikut ini secara berulang-ulang!:

```
gcc -c great-software.c -o great-software.o
gcc -c db.c -o db.o
gcc -c myread.c -o myread.o
gcc -c bebas.c -o bebas.o
gcc -o great-software great-software.o db.o myread.o bebas.o
```
Setiap anda mengubah source code maka anda harus mengulang lagi 5 baris perintah diatas itu. Betapa melelahkan.

#### Makefile Latihan 2 (Penggunaan Variables)
Penggunaan variables memiliki banyak keuntungan. Salah satunya adalah tidak perlu lagi mengulang-ulang susunan prerequiesites dan menghindari pengulangan yang lainnya. Langsung saja, mari kita modifikasi file Makefile yang pertama kita buat di latihan 1 menjadi Makefile yang lebih ganteng di latihan 2 ini. **Untuk source code program masih menggunakan source code program yg sama seperti di latihan 1**.

Berikut ini adalah susunan file Makefile latihan 2 dengan menggunakan variables.

![Makefile Excercise 1](http://res.cloudinary.com/okaprinarjaya/image/upload/v1437492554/Makefile-exercise2_wwkwkz.png)

Jika sudah selesai memodifikasi file Makefile nya, maka lanjutkan dengan menjalankan perintah `make` yg sama seperti di latihan 1. Bila perlu, jalankan perintah `make clean` terlebih dahulu agar file-file hasil proses build yg lama terhapus.

#### Makefile Latihan 3 (Kerapian)
Kerapian??? Ya! Betul kerapian dibutuhkan agar mencapai situasi yang manageable dan maintainable. Yaa..sebenernya sih tidak serumit itu, saya cuma ingin memindahkan semua file source code `.c` dan `.h` ke direktori baru bernama `src/` dan semua file hasil proses build ditaruh di direktori bernama `build`. Seruuu kaan?

Desainnya adalah, direktori `src/` merupakan direktori permanen yang menyimpan source code. Dan direktori `build/` adalah direktori yg hanya tercipta saat proses build dijalankan dan bisa dihapus sesuka hati.

**Buatlah sub direktori bernama `src` dan jangan lupa untuk memindahkan semua file-file source code `.c` dan `.h` ke sub direktori `src`**

Dan berikut adalah susunan Makefile latihan 3 :

![Makefile Excercise 1](http://res.cloudinary.com/okaprinarjaya/image/upload/v1437492555/Makefile-Exercise3_zysxni.png)

Jika sudah selesai memodifikasi file Makefile nya, maka lanjutkan dengan menjalankan perintah `make` yg sama seperti di latihan 1. Bila perlu, jalankan perintah `make clean` terlebih dahulu agar file-file hasil proses build yg lama terhapus.

### Bagaimana GNU Make Berperilaku dengan Makefile ?
Bagian ini menjelaskan bagaimana perilaku program `make` saat melakukan proses build dengan mengkonsumsi informasi-informasi yang ada di file Makefile sebagai referensi untuk menjalankan tugasnya. Bagian tulisan ini sebenarnya adalah saduran berbahasa Indonesia dari manual GNU Make dari official documentation nya di http://www.gnu.org/software/make/manual/html_node/How-Make-Works.html#How-Make-Works .

Saya menggunakan judul yang berbeda dari sumber aslinya dengan tujuan menyeragamkan metode / pendekatan saya dalam menjelaskan sesuatu. Pada intinya judul yang saya pilih punya tujuan yang sama dengan judul pada sumber aslinya yg jika diterjemahkan ke bahasa Indonesia menjadi: **Bagaimana `make` Memproses sebuah Makefile**

#### Default Goal
Dari sekian banyak rule yang tersusun / terdaftar di file Makefile kita, rule yang manakah yang pertamakali dieksekusi oleh `make` ? Jawabannya adalah rule yang posisinya berada paling atas / pertama dan dengan SYARAT nama target dari rule tersebut tidak diawali dengan karakter titik `.`contoh: `.PHONY` . Rule pertama yang dieksekusi oleh `make` saat `make` mulai dijalankan adalah disebut sebagai **default goal** .

#### Menentukan Default Goal secara Custom
Ingat, default goal adalah rule pertama yang dieksekusi oleh `make`. Bagaimana jika kita ada kebutuhan untuk menentukan sendiri / secara custom rule yang akan pertamakali dieksekusi oleh si `make` ? Sebenarnya file Makefile yang sudah kita susun sebelumnya sudah bisa mengeksekusi sebuah rule sesuai pilihan kita. Contohnya adalah saat menjalankan perintah: `make clean` . `clean` adalah nama target dari sebuah rule.

`.PHONY` adalah sebuah special target. Ibaratkan sebuah bahasa pemrograman, `.PHONY` adalah reserved word / keyword dari sebuah bahasa pemrograman. Semua target yang terdaftar sebagai prerequiesites pada `.PHONY` akan dikeluarkan dari daftar urutan eksekusi, dan hanya bisa dieksekusi secara eksplisit. Pada file Makefile yang kita susun, kita sudah mendaftarkan target `clean` sebagai prerequiesites di 
target `.PHONY` maka target `clean` sudah keluar dari daftar urutan eksekusi.

#### Alur (Flow) Build Berdasarkan Rules
Tentunya anda akan bertanya-tanya bagaimana sebuah default goal menentukan rule manakah yang selanjutnya akan dieksekusi? Bagaimana `make` menyusun urutan daftar eksekusi? Agar anda punya sedikit bayangan, mari kita lihat gambar berikut ini:

![Build Dependencies 1](http://res.cloudinary.com/okaprinarjaya/image/upload/v1437587518/Build-Dependencies_t9rvaa.png)

Berdasarkan pada gambar, maka bisa dikatakan file executable `great-software` adalah root target / target paling puncak. Berikut penjelasannya dimulai dari root target:

`great-software`

1. Rule paling pertama dieksekusi oleh `make`. Nama target dari rule adalah `great-software`. 
2. Bahan-bahan / prerequiesites dari target `great-software` dicheck secara berurutan dari kiri ke kanan.
3. Dari sini `make` menyusun daftar urutan eksekusi
3. Check apakah `great-software.o` ADA ? jika TIDAK ADA, Check apakah `great-software.o` adalah sebagai target juga di sebuah rule? Jika YA sebagai target, maka eksekusi rule dengan nama target `great-software.o`
4. Jika `great-software.o` ADA, maka hal yg sama check juga apakah dia adalah sebagai target juga? Jika ya, maka eksekusi rule dengan nama target `great-software.o`

`great-software.o`

1. Jika datang dari kondisi tidak ada, maka receipes langsung dijalankan
2. Jika datang dari kondisi ada, maka sebelum menjalankan receipes, `make` melakukan checking apakah ada perubahan dari file `great-software.c` , `db.h`, `myread.h`, dan `bebas.h` ? Jika ya, maka jalankan receipes.
3. Hasil dari berjalannya receipes adalah file `great-software.o`

Begitu juga dengan prerequiesite - prerequiesite yang lainnya yang merupakan bagian / bahan dari sebuah target. Hal yang yg sama terjadi dengan mereka. 


