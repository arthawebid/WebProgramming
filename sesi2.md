**Framework PHP dan Laravel**.
---
## 📚 MATERI PERKULIAHAN: **Menerapkan OOP dalam Pemrograman Web**
---

### 1. **Framework PHP**

#### ✅ Apa itu Framework?

Framework adalah kerangka kerja (template) untuk mempercepat dan mempermudah proses pengembangan aplikasi dengan menyediakan struktur, aturan, dan fitur bawaan.

#### 🔧 Contoh Framework PHP:

| Framework       | Kelebihan                         |
| --------------- | --------------------------------- |
| **Laravel**     | Modern, elegan, banyak fitur      |
| **CodeIgniter** | Ringan, cocok untuk pemula        |
| **Symfony**     | Enterprise-level, modular         |
| **Yii**         | Cepat, cocok untuk aplikasi besar |

#### 💡 Kenapa Menggunakan Framework?

* Mempercepat development
* Menggunakan prinsip OOP dan MVC
* Keamanan lebih baik
* Kode lebih terstruktur dan rapi

---

### 2. **Framework Laravel**

#### ✅ Laravel Overview

* Laravel adalah framework PHP open-source berbasis OOP dan **arsitektur MVC (Model-View-Controller)**.
* Dikenal karena syntax yang clean, fitur lengkap, dan dokumentasi yang baik.

#### 🔑 Konsep OOP dalam Laravel:

| OOP Konsep        | Penerapan di Laravel                                       |
| ----------------- | ---------------------------------------------------------- |
| **Class**         | Controller, Model, Middleware, Service                     |
| **Object**        | Instance dari Model, Request, Response                     |
| **Inheritance**   | Semua Controller biasanya extend `Controller.php`          |
| **Polymorphism**  | Interface dan Service Container                            |
| **Encapsulation** | Mengatur akses data dalam model                            |
| **Abstraction**   | Laravel menyembunyikan kompleksitas database, routing, dll |

---

### 3. **Struktur Framework Laravel**

Berikut adalah struktur direktori utama Laravel:

```
project-name/
├── app/               # Business logic (Models, Controllers, etc.)
│   ├── Http/
│   ├── Models/
│   └── ...
├── bootstrap/         # Bootstrap file
├── config/            # Konfigurasi aplikasi
├── database/          # Migration, Seeder
├── public/            # Root folder untuk web (index.php, asset)
├── resources/         # View (Blade), assets, lang
├── routes/            # Routing (web.php, api.php)
├── storage/           # Logs, cache
├── tests/             # Unit testing
└── vendor/            # Composer dependencies
```

---

### 4. **Fitur Framework PHP (Laravel)**

Laravel menyediakan berbagai fitur out-of-the-box:

| Fitur                  | Penjelasan                                        |
| ---------------------- | ------------------------------------------------- |
| **Routing**            | Menentukan URL dan menghubungkannya ke controller |
| **Middleware**         | Filter permintaan HTTP sebelum masuk ke aplikasi  |
| **Eloquent ORM**       | Pemodelan database berbasis OOP                   |
| **Blade Template**     | Engine templating untuk view                      |
| **Migration & Seeder** | Membuat dan mengatur struktur database            |
| **Authentication**     | Login, register, dan otorisasi                    |
| **Artisan CLI**        | Command line tool Laravel                         |
| **RESTful API**        | Dukungan penuh untuk membuat API                  |

#### 🎯 Contoh Routing:

```php
// routes/web.php
Route::get('/mahasiswa', [MahasiswaController::class, 'index']);
```

#### 🎯 Contoh Model:

```php
// app/Models/Mahasiswa.php
namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Mahasiswa extends Model {
    protected $table = 'mahasiswa';
}
```

---

### 5. **Instalasi Framework Laravel**

#### ✅ Syarat:

* PHP ≥ 8.1
* Composer
* Web server (Apache/Nginx atau Laravel's built-in server)

#### 🔧 Langkah-langkah Instalasi:

##### A. Instalasi via Composer

```bash
composer create-project --prefer-dist laravel/laravel nama-proyek
```

##### B. Jalankan Server Lokal

```bash
cd nama-proyek
php artisan serve
```

##### C. Akses di Browser

```
http://localhost:8000
```

---

### 📌 Penutup: Integrasi OOP dalam Laravel

Laravel bukan sekadar framework — Laravel adalah cara modern untuk **membangun aplikasi PHP dengan prinsip OOP, MVC, dan clean code**.

Dengan memahami konsep OOP, struktur Laravel, dan fitur-fiturnya, Anda akan dapat:

✅ Menulis kode yang reusable
✅ Memisahkan logika program dengan tampilan
✅ Membuat aplikasi yang scalable dan maintainable

---

## 🎯 Tugas Mandiri:

1. Install Laravel di komputer masing-masing.
2. Buat satu Controller `MahasiswaController` dan tampilkan halaman "Daftar Mahasiswa".
3. Jelaskan konsep OOP yang digunakan dalam Controller tersebut.

---
