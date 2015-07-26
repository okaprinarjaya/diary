---
layout: post
title: Mahasiswa/Mahasiswi Jurusan TI Wajib Belajar Bahasa Pemrograman C
---

## Membosankan dan Tidak Punya Ide
Waktu saya masih menjadi mahasiswa, saya sendiri dan hampir semua teman-teman yang lain hanya menyentuh bahasa pemrograman C saat berurusan dengan kegiatan akademik saja. Hanya sekedar menyusun baris-baris kode C yang hanya untuk mengejar nilai dan memenuhi persyaratan matakuliah saja. Waktu dulu, saya pribadi menganggap bahasa pemrograman C itu membosankan dan saya tidak punya ide. Mengapa membosankan? Karena saya sama sekali tidak memiliki bayangan bagaimana bentuk aplikatifnya? Bisa membuat apa dengan bahasa C? Apa yang bisa membuat saya keren jika mempelajari C? 

Saya lebih suka dan terasa menyenangkan membuat aplikasi sistem informasi sederhana dengan form-form sederhana menggunakan PHP yg berbasis web atau dengan Java Swing berbasis desktop. Mengapa susah-susah menggunakan C untuk membuat form-form aplikasi sistem informasi. Saya masih ingat karena sample-sample aplikasi waktu dulu belajar bahasa C di kampus adalah membuat form-form sistem informasi sederhana. Dan, bahasa C juga digunakan di matakuliah struktur data. Lagi, lagi, dan lagi saya tidak punya ide. Saya sama sekali tidak memiliki bayangan bagaimana bentuk aplikatif dari struktur data? Bisa membuat apa dengan struktur data? Apa yang bisa membuat saya keren jika mempelajari struktur data? 

## Bahasa C Akan Membuat Kamu Sangat Keren!
Dengan mempelajari bahasa pemrograman C kamu dapat mengetahui bagaimana sesuatu itu bekerja. Bagaimana computer networking bekerja, bagaimana variable array, list, dictionary, tuple, hash map pada bahasa pemrograman high level seperti: Python, Ruby, PHP, Java, dan VB bekerja. Bagaimana sebuah tool dapat mencapai situasi yang multi threading dan berhasil menangani masalah concurrency.

Dengan mengetahui bagaimana sesuatu itu bekerja kamu akan dengan mudah mengidentifikasi masalah, lalu kamu akan lebih paham dan bijaksana dalam menggunakan existing tool yang kamu pakai dalam pengembangan. Atau jika memang existing tool tidak dapat solving masalah yg dihadapi, setidaknya kamu akan lebih bijaksana dan smart dalam memilih tool baru yg akan digunakan. Tool baru bukan berarti tool yg paling terkini dalam konteks lahir / terciptanya tool itu. Tidak latah ikut-ikutan pakai tool paling baru tapi tidak memahami latar belakang masalah yg ada dibalik eksistensi sebuah tool.

Contoh paling sederhana adalah bagaimana komputer menyimpan data berupa string? Bahasa-bahasa pemrograman high level akan memberikan kamu kemudahan karena sudah menyembunyikan kerumitannya. Dalam bahasa pemrograman C menyimpan string tidak semudah yang dibayangkan apalagi mengolah string seperti kebutuhan concat string. Di C kamu akan berinteraksi dengan memori dan bytes untuk HANYA menyimpan dan mengolah string. Dengan memahami dan menguasai bagaimana menyimpan dan mengolah string di C maka otomatis kamu akan paham bagaimana komputer menyimpan data string.

Jika di Indonesia ini ada mahasiswa strata 1 jurusan TI / computer science atau bahkan yg strata 2 masih malas belajar bahasa pemrograman C saya akan berikan sebuah pertanyaan kpd para mahasiswa/mahasiswi jurusan TI di Indonesia. Pertanyaannya adalah:

"
Mengapa kalian selalu mengajukan pertanyaan-pertanyaan ini? :

1. Kapan yaa Indonesia punya operating system buatan sendiri?

2. Kenapa yaa kontributor-kontributor kernel linux, web server apache, nginx tidak ada yang orang Indonesia?

3. Kapan yaa ada bahasa pemrograman buatan Indonesia? Sudah ada sih..tapi..

4. Ada atau tidak RDBMS seperti MySql yang dibuat oleh orang Indonesia?
"

Dan masih banyak pertanyaan-pertanyaan yang sejenis. Untuk dapat mewujudkan hal-hal yang ada di dalam pertanyaan-pertanyaan itu maka diperlukan kemampuan pemrograman dengan bahasa C dan dibarengi dengan fondasi computer science yang kuat. Dalam proses belajar C secara paralel konsep-konsep dan teori-teori dalam computer science menjadi diterapkan.

Bahasa C adalah bahasa pemrograman dengan kategori middle level. Maksudnya adalah sebuah bahasa pemrograman yang memiliki kemampuan high level dan low level secara bersamaan. Salah satu kemampuam high level adalah adanya kontrol flow melalui penggunaan keyword `if-else`, `for`, `while` yang merupakan bahasa ekspresi yang umum dalam bahasa inggris. Sehingga memudahkan kita mengerti alur proses sebuah program. Lalu, beberapa kemampuan low level nya adalah:

1. Akses dan interaksi secara langsung dengan memori melalui pointer
2. Dukungan terhadap penulisan program dengan bahasa assembly (bahasa mesin) secara inline melalui bahasa C itu sendiri. Berikut penjelasan berdasarkan wikipedia tentang kemampuan inline assembler di bahasa C

> https://en.m.wikipedia.org/wiki/Inline_assembler
> In computer programming, the inline assembler is a feature of some compilers that allows very low level code written inassembly to be 
> embedded in a high level language like C or Ada. This embedding is usually done for one of three reasons:
> 
> 1. Optimization: when assembly language is inlined for optimization, the most performance-sensitive parts of an algorithm are replaced by 
> hand-written assembly. This allows the programmer to use the full extent of his ingenuity, without being limited by a compiler's 
> higher-level constructs.
>
> 2. Access to processor specific instructions: some processors offer special instructions, such as Compare and Swap and Test and Set 
> — instructions which may be used to construct semaphores or other synchronization and locking primitives. Nearly every modern 
> processor has these or similar instructions, as they are necessary to implement multitasking. To name a few, specialized 
> instructions are found in the SPARC VIS, Intel MMX and SSE, and Motorola Altivec instruction sets.
>
> 3. System calls: high-level languages rarely have a direct facility to make system calls, so assembly code is used.

Oleh karena itulah bahasa C sering digunakan untuk system programming. Yaitu software-software yang bersifat fondasi / core system, contoh: untuk membangun operating system, driver hardware, dan bahasa pemrograman. Dan sekaligus juga dapat digunakan untuk application programming. Yaitu membangun software-software yg bersifat aplikatif / end user. Contohnya: HTTP Server Apache, Email Server, bahkan aplikasi kasir point of sale bisa dibangun dengan bahasa C.

Dengan menguasai bahasa C kamu punya kemampuan untuk bisa melakukan hal-hal berikut ini

* Ikut berkontribusi mengembangkan linux kernel / menyumbangkan secuil kode walau hanya berupa tambalan security issue.
* Membuat tools networking seperti: HAProxy load balancer, Snort Intrusion Detection System https://www.snort.org/
* Ikut berkontribusi mengembangkan bahasa pemrograman PHP / Python / Ruby
* Membuat embedded system di perangkat mikrokontroller
* Membuat dongle untuk mengunci aplikasi kita. Jadi aplikasi tidak bisa dengan mudah digandakan oleh si pembeli aplikasi kita. Karena aplikasi hanya bisa running jika ada dongle terpasang di slot USB.
* Membuat web / HTTP server seperti: Apache, Nginx
* Ikut berkontribusi mengembangkan desktop environment di linux seperti: KDE, dan GNome
* Membuat database jenis NoSQL yg sederhana seperti: Redis, dan Gibson.

Dengan menguasai bahasa C, ibaratkan dalam industri transportasi, kita tidak lagi hanya bisa **merakit** atau sekedar **karoseri (https://id.wikipedia.org/wiki/Karoseri)** saja karena mesin dibuat di jepang. Dengan menguasai bahasa C, ibaratkan dalam industri transportasi kita bisa membuat mesin sebuah kendaraan. Dan banyaakkk hal keren lagi yang membuat bangsa Indonesia makin berjaya dalam bidang Teknologi Informasi.
