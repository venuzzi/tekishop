# Tugas 9

1. **Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?**

    
2. **Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.**

3. **Jelaskan mekanisme pengambilan data dari JSON hingga dapat ditampilkan pada Flutter.**

4. **Jelaskan mekanisme autentikasi dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.**


5. **Sebutkan seluruh widget yang kamu pakai pada tugas ini dan jelaskan fungsinya masing-masing.**

6. **Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).**







# Tugas 8 

1. **Jelaskan perbedaan antara Navigator.push() dan Navigator.pushReplacement(), disertai dengan contoh mengenai penggunaan kedua metode tersebut yang tepat!**

    Keduanya digunakan untuk menavigasi antara berbagai halaman (routes) di aplikasi Flutter. Namun, perbedaan dari keduanya adalah:
    - Navigator.push() 
        Digunakan untuk menambahkan halaman baru ke tumpukan navigasi. Pengguna masih dapat kembali ke halaman sebelumnya. Contoh:
        ```Dart 
        Navigator.push(
            context,
            MaterialPageRoute(builder: (context) => NewPage()),
        );
        ```

    - Navigator.pushReplacement()
        Digunakan untuk menggantikan halaman saat ini dengan halaman baru. Hal ini menghapus halaman saat ini dari tumpukan navigasi dan menambahkan halaman baru ke posisi tersebut. Contoh:
        ```Dart
        Navigator.pushReplacement(
            context,
            MaterialPageRoute(builder: (context) => NewPage()),
        );
        ```

2.  **Jelaskan masing-masing layout widget pada Flutter dan konteks penggunaannya masing-masing!**

    - **Column & Row** = Digunakan untuk mengatur posisi children widget secara vertikal maupun horizontal. Pada tugas ini, digunakan Column dalam mengatur tampilan Form, Snackbar, Menu, dan Drawer.
    - **Container** = Digunakan untuk mengelompokkan berbagai widget dalam satu tempat. Widget-widget yang dikelompokkan tersebut juga dapat diberikan dekorasi sesuai yang kita inginkan. 
    - **GridView** = Digunakan untuk menyusun berbagai child dalam bentuk grid atau table. GridView ini cocok untuk menampilkan koleksi item dalam grid, seperti galeri foto dan tampilan untuk ShopCard pada menu.
    - **Card** = Merupakan widget yang menampilkan konten dalam bentuk kartu dengan sudut yang dibulatkan. Digunakan untuk menampilkan berbagai informasi dalam format yang konsisten, seperti kartu menu dan kartu kontak.
    - **Wrap** = Merupakan widget yang mengatur child-nya ke dalam baris atau kolom, dan akan beralih ke baris atau kolom berikutnya jika tidak cukup ruang. Digunakan untuk menampilkan sejumlah widget dalam ruang yang terbatas.

3. **Sebutkan apa saja elemen input pada form yang kamu pakai pada tugas kali ini dan jelaskan mengapa kamu menggunakan elemen input tersebut!**

    Dalam tugas 8 ini, saya menggunakan elemen input berupa `TextFormField`. Dimana saya gunakan untuk memasukkan *name, price, amount, dan description*. Elemen input ini digunakan karena memiliki sifat yang interaktif dalam mengumpulkan input data. Selain itu, `TextFormField` juga dapat melakukan validasi terhadap input yang dimasukkan.

4. **Bagaimana penerapan clean architecture pada aplikasi Flutter?**

    Clean Architecture adalah pendekatan pengembangan perangkat lunak yang dirancang untuk meningkatkan pemeliharaan, skaalabilitas, dan uji pada proyek perangkat lunak. Penerapan Clean Architecture di Flutter melibatkan pemisahan kode ke dalam beberapa lapisan terisolasi. Berikut adalah contoh implementasinya dalam flutter:

    **a. Lapisan Presentasi** = Bertanggung jawab untuk menangani tampilan dan presentasi. Untuk implementasi, masukkan widget Flutter pada direktori `screens/` dan `widgets/`.

    **b. Lapisan Domain** = Merupakan inti dari aplikasi yang mengandung logika, aturan, dan entitas domain. Lapisan ini tidak boleh bergantung pada detail implementasi atau infrastruktur. Untuk implementasinya, buat direktori seperti `domain/` dan teruh berbagai logika pada direktori tersebut.

    **c. Lapisan Infrastruktur** = Lapisan ini berisi implementasi dari detail teknis seperti penyimpanan data, API, database, dan lainnya. Untuk implementasi, tempatkan kode infrastruktur seperti penyimpanan lokal, pengambilan data dari API, atau pengaturan database di dalam direktori seperti `data/`. 
    
    **d. Lapisan Aplikasi** = Lapisan ini bertanggung jawab untuk mengkoordinasikan aliran data antara lapisan Presentasi, Domain, dan Infrastruktur. Untuk implementasi, tempatkan logika koordinasi, kasus penggunaan, dan objek yang memediasi antara presentasi dan domain pada direktori seperti `usecases/` atau `blocs/`.

5. **Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial)**

    Checklist pembuatan drawer:

    - Buat direktori baru bernama `widgets`, lalu buat berkas `left_drawer.dart` dalam direktori `widgets`.
    - Impor halaman-halaman yang ingin kita masukkan navigasinya, lalu masukkan kode yang tersedia ke dalam berkas tersebut.
    - Masukkan routing untuk halaman-halaman yang kita impor.
    - Hias drawer dengan memasukkan drawer header.
    - Masukkan drawer tersebut ke dalam halaman `menu.dart`.

    Checklist pembuatan halaman baru untuk formulir:

    - Buat berkas baru pada direktori `lib` dengan nama `shoplist_form.dart`.
    - Tambahkan kode yang tersedia ke dalam berkas tersebut dan ubah widget Placeholder yang ada.
    - Buat variabel baru bernama `_formKey`, lalu tambahkan ke dalam atribut `key` milik widget `Form`.
    - Isi widget `Form` dengan `_name`, `_price`, `_amount`, dan `_description`.
    - Buat widget `Column` sebagai child dari `SingleChildScrollView`.
    - Buat empat widget `TextFormField` untuk field `name`, `price`, `amount`, dan `description`, yang dibungkus oleh `Padding` sebagai  children dari `Column`.
    - Buat tombol sebagai child selanjutnya dari `Column`. Tombol ini digunakan untuk memunculkan pop-up.

    Checklist pemunculan data sesuai isi dari formulir setelah menekan tombol Save:

    - Tambahkan fungsi `showDialog()` pada bagian `onPressed()` dan munculkan widget `AlertDialog` pada fungsi tersebut.
    - Tambahkan juga fungsi untuk mereset form.

    Checklist pengarahan pengguna ke halaman formulir ketika menekan tombol Tambah Item pada halaman utama:

    - Pada widget `ShopItem` pada berkas `menu.dart`, tambahkan kode pengimplementasian `Navigator.push()` dalam atribut `onTap`. Contoh kode:
        ```Dart
        if (item.name == "Tambah Item") {
            Navigator.push(context, MaterialPageRoute(builder: (context) => const ShopFormPage()));
        }
        ``` 


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

3. **Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial)**

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

        ```Dart 
        class ShopItem {
            final String name;
            final IconData icon;
        ShopItem(this.name, this.icon);
        }
        ```

    - Dibawah kode `MyHomePage({Key? key}) : super(key: key);`, tambahkan barang-barang yang dijual.
    - Selanjutnya tambahkan isi dari Scaffold dengan kode yang ada di tutorial.
    - Buat widget stateless baru untuk menampilkan card.


<!-- ## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference. -->
