# Tugas 9

1. **Apakah bisa kita melakukan pengambilan data JSON tanpa membuat model terlebih dahulu? Jika iya, apakah hal tersebut lebih baik daripada membuat model sebelum melakukan pengambilan data JSON?**

    Pengambilan data JSON tanpa membuat model terlebih dahulu bisa dilakukan, bahkan akan lebih mudah dan tidak kompleks. Meskipun adanya kemudahan tersebut, terdapat beberapa resiko terkait validasi data dan konsistensi, terutama jika projek yang dikerjakan termasuk ke skala besar. Pembuatan model sebelum melakukan pemgambilan data JSON akan memberikan manfaat berupa validasi data yang signifikan. Pendekatan yang kedua tersebut akan lebih baik dilakukan dalam proyek skala besar sehingga akan membuat kode lebih mudah dibaca, dipelihara, dan memberikan struktur yang memudahkan pengelolaan dan ekspansi data.


2. **Jelaskan fungsi dari CookieRequest dan jelaskan mengapa instance CookieRequest perlu untuk dibagikan ke semua komponen di aplikasi Flutter.**

    CookieRequest ini berfungsi untuk mengelola berbagai operasi yang terkait dengan cookie dalam HTTP request di aplikasi flutter. Berbagai operasinya di antara lain yaitu manajemen cookie, autentikasi keamanan, pemeliharaan session, dan penyesuaian preferensi user. Instance CookieRequest ini perlu dibagikan ke semua komponen di app flutter agar dapat memastikan konsistensi data, efisiensi dalam kode, keamanan kode, dan memudahkan debugging.

3. **Jelaskan mekanisme pengambilan data dari JSON hingga dapat ditampilkan pada Flutter.**

    Mekanisme pengambilan data:
    1. Tambah dependensi http ke proyek, ini akan menambahkan dependensi agar bisa menggunakan fungsi HTTP untuk melakukan request ke web service.
    2. Buat model yang sesuai dengan respons data dari web service, hal ini akan menentukan format data dan menentukan struktur data yang akan digunakan untuk menyimpan data.
    3. Buat http request ke web service menggunakan dependensi http, ini untuk menentukan URL web service yang akan diaksess, menentukan metode HTTP yang digunakan, dan menentukan parameter yang dikirim ke web service.
    4. Konversi objek yang didapat dari web service ke model yang telah dibuat, ini dilakukan dengan membaca data dari objek yang diterima dari web service, kemudiannya menyimpannya ke model yang telah dibuat.
    5. Menampilkan data yang telah dikonversi ke aplikasi dengan `FutureBuilder`, data akan ditampilkan secara bertahap.
    6. Fetch JSON ke url yang sama dengan header json, ini untuk menambahka header untuk menentukan format JSON yang akan diterima.
    7. Sesuaikan body JSON yang telah difetch ke model item sesuai dengan properti yang ada.

4. **Jelaskan mekanisme autentikasi dari input data akun pada Flutter ke Django hingga selesainya proses autentikasi oleh Django dan tampilnya menu pada Flutter.**
    Mekanisme autentikasi dan menampilkan menu pada flutter:
    1. User memasukkan username dan password pada TextField.
    2. Buat permintaaan POST HTTP ke fungsi login Django, dengan membuat `CookieRequest` baru yang akan digunakan untuk mengirim data ke web server dan menyimpan session user yang telah terautentikasi.
    3. Django kemudian mengelola permintaan login dengan memvalidasi username dan password. Jika berhasil, akan dikirimkan respons yang diakses dan diperiksa oleh app flutter.
    4. Jika login sukses akan melakukan navigasi ke halaman `MyHomePage`.

5. **Sebutkan seluruh widget yang kamu pakai pada tugas ini dan jelaskan fungsinya masing-masing.**

    Berikut widget-widget yang saya gunakan pada tugas ini:
    - **Drawer**, untuk membuat sebuah drawer yang berisikan menu-menu seperti buat item dan lihat item.
    - **TextFormField**, untuk membuat input field pada halaman `shoplist_form.dart` dan `login.dart`.
    - **FutureBuilder**, untuk membuat widget yang akan dibangun di masa yang akan datang.
    - **AlertDialog**, untuk membuat popup pesan peringatan kepada user.
    - **ElevatedButton**, untuk membuat dan menampilkan tombol.
    - **ListTile**, untuk membuat menu-menu yang ada pada drawer serta membuat list dari item.
    - **ScaffoldMessenger**, untuk menampilkan snackbar.
    - **ListView.builder**, untuk membuat list item.
    - **Navigator**, untuk mengelola dan menavigasi rute didalam aplikasi.
    - **TextButton**, untuk membuat dan menampilkan tombol yang berisi teks.

6. **Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step! (bukan hanya sekadar mengikuti tutorial).**

    Checklist pembuatan halaman login: 

    - Install package `Provider` dan `pbp_django_auth`.
    - Modifikasi root widget untuk menyediakan `CookieRequest` library ke semua child widgets dengan menggunakan `Provider`.
    - Buat file baru pada folder `screens` dengan nama `login.dart`.
    - Isi file `login.dart` dengan kode yang telah disediakan.
    - Ubah `home: MyHomePage()` menjadi `home: LoginPage()` widget `MaterialApp(...)` pada file `main.dart`.

    Checklist integrasi sistem autentikasi Django:

    - Buat app Django baru bernama `authentication` pada proyek Django sebelumnya.
    - Install library `django-cors-headers`. 
    - Tambahkan `corsheaders` ke `INSTALLED_APPS` pada main project `settings.py`.
    - Tambahkan middleware corsheaders nya dan beberapa variabel cookie ke `settings.py`.
    - Buat method view untuk login pada `authentication/views.py`.
    - Atur pathnya pada `urls.py`.

    Checklist pembuatan model kustom:

    - Salin endpoint JSON yang ada pada proyek Django.
    - Buka situs Quicktype lalu ubah setup name menjadi `Product`, source type menjadi `JSON`, dan language menjadi `Dart`.
    - Tempelkan data JSON yang telah disalin sebelumnya kedalam textbox yang tersedia.
    - Tekan pilihan `Copy Code` pada Quicktype
    - Buat file baru bernama `product.dart` pada folder `lib/models`, lalu tempel kode yang telah disalin ke dalamnya.

    Checklist pembuatan halaman yang berisi daftar item:
    
    - Buat file baru pada folder `lib/screens` dengan nama `list_product.dart`.
    - Lalu impor library yang dibutuhkan ke dalam file baru tersebut.
    - Salin potongan kode yang tersedia ke `pages/list_product.dart`, setelah itu imporlah file-file yang diperlukan.
    - Tambahkan halaman `list_product.dart` ke `left_drawer.dart` dengan menambahkan kode yang tersedia.
    - Ubah fungsi tombol `Lihat Produck` pada halaman utama agar mengarahkan ke halaman `ProductPage`.
    - Impor file yang dibutuhkan saat menambahkan `ProductPage` ke `left_drawer.dart` dan `shop_card.dart`.









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
