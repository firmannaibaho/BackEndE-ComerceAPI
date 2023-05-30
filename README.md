# ECommerce API

Ini adalah contoh kode untuk API ECommerce sederhana. API ini memungkinkan Anda untuk mengakses dan mengelola informasi pengguna, produk, pesanan, dan ulasan dalam database menggunakan protokol HTTP. Anda dapat menggunakan perangkat lunak seperti IntelliJ IDEA untuk menjalankan server API dan Postman untuk menguji dan mengirim permintaan HTTP ke API.

## Menjalankan Server API

1. Pastikan Anda telah menginstal [Java Development Kit (JDK)](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) dan mengatur variabel lingkungan JAVA_HOME.
2. Unduh dan instal [IntelliJ IDEA](https://www.jetbrains.com/idea/).
3. Buka IntelliJ IDEA dan impor proyek ini.
4. Setelah proyek terbuka, temukan kelas `ECommerceAPI` dan jalankan metode `main`.
5. Server API akan berjalan di `http://localhost:8059`.

## Menggunakan Postman untuk Menguji API

1. Unduh dan instal [Postman](https://www.postman.com/downloads/).
2. Buka Postman dan buat permintaan baru.
3. Tentukan URL permintaan sesuai dengan endpoint yang ingin Anda akses, misalnya `http://localhost:8078/users`.
4. Pilih metode HTTP yang sesuai (GET, POST, PUT, DELETE).
5. Jika diperlukan, atur header `API-Key` dengan nilai `Firman`.
6. Kirim permintaan dan periksa respons dari API.

## Pengaturan Awal
Untuk memulai menggunakan ECommerceAPI, ikuti langkah-langkah berikut:

Buka proyek dalam Intellij IDEA atau editor Java lainnya.
Pastikan semua dependensi yang diperlukan telah diimpor dengan benar. Hal ini meliputi paket com.sun.net.httpserver, org.json, dan java.sql.
Pastikan Anda memiliki koneksi JDBC ke database yang sesuai. Dalam contoh ini, digunakan koneksi JDBC ke database SQLite. Anda dapat menyesuaikan koneksi sesuai dengan database yang Anda gunakan.
Atur API key yang akan digunakan dalam variabel API_KEY. Gantilah "Firman" dengan kunci API yang Anda inginkan.

## Menggunakan JDBC dan JSON

API ini menggunakan JDBC (Java Database Connectivity) untuk berinteraksi dengan database SQLite dan menggunakan JSON untuk mengirim dan menerima data melalui HTTP. Kode ini sudah memperhitungkan penggunaan kedua teknologi tersebut.

Anda dapat mengubah koneksi database ke database lain dengan memperbarui URL, nama pengguna, dan kata sandi dalam metode `getConnection()` di kelas `SQLiteConnector`.

## Penggunaan API
Aplikasi ECommerceAPI menyediakan beberapa endpoint API yang dapat digunakan untuk mengakses data pengguna, produk, dan pesanan. Berikut adalah daftar endpoint yang disediakan:

### GET /users
Endpoint ini mengembalikan daftar pengguna dari database.

Contoh URL: http://localhost:8059/users
GET /users/{id}
Endpoint ini mengembalikan detail pengguna berdasarkan ID yang diberikan.

Contoh URL: http://localhost:8059/users/1
GET /users/{id}/products
Endpoint ini mengembalikan daftar produk yang dimiliki oleh pengguna berdasarkan ID yang diberikan.

Contoh URL: http://localhost:8059/users/1/products
GET /users/{id}/orders
Endpoint ini mengembalikan daftar pesanan yang dibuat oleh pengguna berdasarkan ID yang diberikan.

Contoh URL: http://localhost:8059/users/1/orders
GET /users/{id}/reviews
Endpoint ini mengembalikan daftar ulasan yang dibuat oleh pengguna berdasarkan ID yang diberikan.

Contoh URL: http://localhost:8059/users/1/reviews
GET /orders/{id}
Endpoint ini mengembalikan detail pesanan berdasarkan ID yang diberikan.

Contoh URL: http://localhost:8059/orders/1
GET /products
Endpoint ini mengembalikan daftar produk dari database.

Contoh URL: http://localhost:8059/products
GET /products/{id}
Endpoint ini mengembalikan detail produk berdasarkan ID yang diberikan.

Contoh URL: http://localhost:8059/products/1
POST /products
Endpoint ini digunakan untuk membuat produk baru.

Contoh URL: http://localhost:8059/products
PUT /products/{id}
Endpoint ini digunakan untuk memperbarui detail produk berdasarkan ID yang diberikan.

Contoh URL: http://localhost:8059/products/1
DELETE /products/{id}
Endpoint ini digunakan untuk menghapus produk berdasarkan ID yang diberikan.

Contoh URL: http://localhost:8059/products/1
POST /products/{id}/reviews
Endpoint ini digunakan untuk menambahkan ulasan baru pada produk berdasarkan ID yang diberikan.

Contoh URL: http://localhost:8059/products/1/reviews
Menjalankan Permintaan API dengan Postman
Anda dapat menggunakan Postman untuk mengirim permintaan ke API ECommerceAPI dan melihat responsnya. 

## Kesimpulan
ECommerceAPI adalah sebuah aplikasi server yang menyediakan API untuk layanan e-commerce. Anda dapat menggunakan aplikasi ini untuk mengakses dan mengelola data pengguna, produk, dan pesanan melalui permintaan HTTP. Dengan mengikuti panduan di atas, Anda dapat menjalankan aplikasi ini dan menguji endpoint API menggunakan Postman atau alat serupa.

# SQLiteConnector

`SQLiteConnector` adalah sebuah kelas utilitas yang digunakan untuk mendapatkan koneksi ke database SQLite.

## Penggunaan

Untuk menggunakan `SQLiteConnector`, ikuti langkah-langkah berikut:

1. Pastikan Anda telah mengimpor kelas `SQLiteConnector` ke proyek Anda.
2. Panggil metode `getConnection()` untuk mendapatkan objek koneksi ke database.

Contoh penggunaan:

```java
import java.sql.Connection;
import java.sql.SQLException;

public class MyClass {
    public static void main(String[] args) {
        try {
            Connection connection = SQLiteConnector.getConnection();
            // Gunakan koneksi untuk menjalankan query dan operasi database lainnya
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

## Kustomisasi

Anda dapat mengkustomisasi koneksi ke database SQLite dengan mengubah nilai `DB_URL` dalam kelas `SQLiteConnector`. Pastikan untuk mengganti path file database dengan path yang sesuai pada sistem Anda.

```java
private static final String DB_URL = "jdbc:sqlite:/path/to/your/database.db";
```

## Ketergantungan

`SQLiteConnector` membutuhkan dependensi berikut:

- SQLite JDBC driver: Pastikan Anda telah mengimpor driver JDBC SQLite ke proyek Anda. Anda dapat mendownload driver SQLite JDBC dari https://github.com/xerial/sqlite-jdbc

Pastikan driver JDBC SQLite telah diimpor ke proyek Anda sebelum menggunakan `SQLiteConnector`.

## Keterangan Tambahan

Pada contoh ini, diasumsikan bahwa database SQLite berada di lokasi file `C:/sqlite/sqlitedb_tugas2`. Pastikan untuk menyesuaikan path file database sesuai dengan lokasi file SQLite yang Anda gunakan.

Pastikan juga Anda telah menangani penanganan kesalahan (exception handling) dengan tepat saat menggunakan `SQLiteConnector` agar dapat menangkap dan mengatasi kesalahan yang mungkin terjadi dalam koneksi database.

# Dependencies

Proyek ini memiliki dependensi berikut yang ditentukan dalam file `pom.xml`.
    <dependencies>
        <dependency>
            <groupId>com.sun.net.httpserver</groupId>
            <artifactId>http</artifactId>
            <version>20070405</version>
        </dependency>

        <dependency>
            <groupId>org.xerial</groupId>
            <artifactId>sqlite-jdbc</artifactId>
            <version>3.7.2</version>
        </dependency>

        <dependency>
            <groupId>org.xerial</groupId>
            <artifactId>sqlite-jdbc</artifactId>
            <version>3.7.2</version>
        </dependency>
        <dependency>
            <groupId>org.json</groupId>
            <artifactId>json</artifactId>
            <version>20210307</version>
        </dependency>

        </dependencies>

## com.sun.net.httpserver:http:20070405
Dependensi ini menyediakan paket `com.sun.net.httpserver`, yang digunakan untuk membuat server HTTP dalam Java.

## org.xerial:sqlite-jdbc:3.7.2
Dependensi ini menyediakan driver JDBC untuk SQLite. Ini memungkinkan aplikasi Java untuk terhubung dan berinteraksi dengan database SQLite.

## org.json:json:20210307
Dependensi ini menyediakan dukungan untuk bekerja dengan data JSON dalam Java. Ini mencakup kelas-kelas untuk parsing, membuat, memanipulasi, dan serialisasi data JSON.

Pastikan Anda memiliki dependensi yang diperlukan dikonfigurasi dalam file `pom.xml` proyek Anda, dan bahwa sistem build Anda diatur untuk mengambil dan mengunduh dependensi ini dari repositori yang tepat.

Catatan: Nomor versi yang disediakan di atas adalah contoh. Pastikan menggunakan nomor versi yang sesuai berdasarkan persyaratan dan kompatibilitas proyek Anda.
