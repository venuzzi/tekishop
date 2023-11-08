# Tugas 7

1. **Apa perbedaan utama antara stateless dan stateful widget dalam konteks pengembangan aplikasi Flutter?**

    Stateless widget merupakan widget statis, yang berarti widget tersebut tidak dapat berubah. Sedangkan stateful widget merupakan widget yang dinamis, ini berarti widget dapat berubah sesuai dengan respons dari events yang dipicu, baik dari interaksi user maupun adanya variabel atau nilai baru yang didapat.

2. **Sebutkan seluruh widget yang kamu gunakan untuk menyelesaikan tugas ini dan jelaskan fungsinya masing-masing.**
    - AppBar = Menampilkan header atas aplikasi dengan judul.
    - Column = Mengatur posisi children widget secara vertikal.
    - Center = Digunakan untuk mengatur konten di tengah kartu.
    - Container = Digunakan untuk mengatur struktur konten dalam kotak dengan padding yang telah ditentukan.
    - Icon = Berguna untuk menampilkan ikon tertentu.
    - InkWell = Memungkinkan area kartu menjadi responsif terhadap sentuhan pengguna, sehingga dapat mendeteksi ketika kartu ditekan.
    - Material = Digunakan untuk mengatur warna latar belakang dan tampilan dasar untuk kartu.
    - MaterialApp = Digunakan untuk mengatur konfigurasi global aplikasi dan menyediakan kerangka kerja untuk membangun aplikasi.
    - MyApp = Digunakan sebagai root dari aplikasi ini dan membungkus seluruh widget yang ada pada aplikasi ini. Widget ini yang dijalankan pada program utama
    - MyHomePage = Merupakan widget halaman utama aplikasi.
    - Padding = Menambahkan padding ke konten.
    - Scaffold = Menyediakan struktur dasar untuk tampilan halaman.
    - SnackBar = Digunakan untuk menampilkan pesan kepada pengguna.
    - ShopCard = Menampilkan card tombol Lihat Item, Tambah Item, dan Logout.
    - SingleChildScrollView = Membuat supaya konten dapat melakukan scrolling.
    - Text = Menampilkan teks dengan gaya tertentu.

3. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial)

    Checklist Pertama:

    - Buat program flutter terbaru, dimulai dengan membuat project baru bernama `tekishop` dengan perintah berikut: 
        ```flutter create tekishop``` 
        ```cd tekishop```
        ```flutter run```
    - Buat repositori GitHub baru dengan nama `tekishop`
    - Lakukan `git init` pada root folder dan lakukan `add-commit-push` ke repositori yang telah dibuat
    - Buat file baru bernama `menu.dart` pada direktori `tekishop/lib`.
    - Tambahkan ```import 'package:flutter/material.dart';``` pada baris pertama file tersebut.
    - Pada berkas `main.dart`, pindahkan kode baris 39 hingga akhir ke berkas `menu.dart`.
    - Tambahkan kode ```import 'package:shopping_list/menu.dart';``` pada `main.dart` agar tidak terjadi error.

    Checklist Kedua:

    - Pada berkas `main.dart` ubah `MyHomePage(title: 'Flutter Demo Home Page')` menjadi `MyHomePage()`.
    - Ubah sifat widget halaman dari stateful menjadi stateless. Lakukan perubahan pada bagian `({super.key, required this.title})` menjadi `({Key? key}) : super(key: key);`. Hapus `final Srting title;` sampai bawah dan tambahkan Widget build.
    - Tambahkan teks dan card untuk tombol, dimulai dengan define tipe pada list kita.
    ```class ShopItem { ```
        ```final String name;```
        ```final IconData icon;```
        ```ShopItem(this.name, this.icon);```
    ```}```
    - Dibawah kode `MyHomePage({Key? key}) : super(key: key);`, tambahkan barang-barang yang dijual.
    - Selanjutnya tambahkan isi dari Scaffold dengan kode yang ada di tutorial.
    - Buat widget stateless baru untuk menampilkan card.


## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
