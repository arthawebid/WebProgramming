# Konsep OOP (Object Oriented Programming)
## Konsep OOP, Class, Object, Tools pemrograman PHP, Class dan method pada PHP

Berikut ini adalah **materi perkuliahan Laravel** yang mencakup **sub-materi dasar pemrograman berorientasi objek (OOP) di PHP**, sebagai pengantar sebelum masuk ke Laravel secara menyeluruh. Materi ini cocok digunakan di minggu-minggu awal perkuliahan Laravel untuk memberikan pondasi yang kuat.

---

## 📚 MATERI PERKULIAHAN: DASAR-DASAR PEMROGRAMAN UNTUK LARAVEL

### Pertemuan 1: Pengantar OOP dan Tools Pemrograman PHP

---

## **1. Konsep OOP, Class, dan Object**

### ✅ Apa itu OOP?

OOP (Object-Oriented Programming) adalah paradigma pemrograman yang memodelkan program sebagai sekumpulan **objek** yang saling berinteraksi.

### 🔑 Konsep Utama OOP:

| Konsep            | Penjelasan                                                          |
| ----------------- | ------------------------------------------------------------------- |
| **Class**         | Blueprint atau cetak biru dari objek                                |
| **Object**        | Instance dari class                                                 |
| **Encapsulation** | Menyembunyikan detail implementasi dan hanya menunjukkan antarmuka  |
| **Inheritance**   | Pewarisan sifat dari satu class ke class lain                       |
| **Polymorphism**  | Kemampuan objek untuk memiliki banyak bentuk                        |
| **Abstraction**   | Menyederhanakan kompleksitas dengan hanya menampilkan fitur penting |

---

### 📌 Contoh Class dan Object:

```php
<?php
class Mahasiswa {
    public $nama;
    public $nim;

    public function __construct($nama, $nim) {
        $this->nama = $nama;
        $this->nim = $nim;
    }

    public function tampilkanData() {
        echo "Nama: $this->nama, NIM: $this->nim";
    }
}

// Membuat object
$mhs1 = new Mahasiswa("Andi", "12345678");
$mhs1->tampilkanData();
?>
```

---

## **2. Tools Pemrograman PHP**

Untuk membangun aplikasi Laravel dengan efisien, berikut adalah tools yang umum digunakan:

### 🔧 Tools Utama:

| Tool                                         | Fungsi                                        |
| -------------------------------------------- | --------------------------------------------- |
| **XAMPP / Laragon**                          | Local server environment (Apache, MySQL, PHP) |
| **Composer**                                 | Dependency manager untuk PHP                  |
| **VS Code / PHPStorm**                       | Code editor / IDE                             |
| **Git & GitHub**                             | Version control                               |
| **Postman**                                  | Testing API                                   |
| **Laravel Installer / Laravel via Composer** | Instalasi Laravel                             |
| **Terminal / CLI**                           | Menjalankan perintah Artisan dan Composer     |

---

### 💡 Cara Install Laravel via Composer:

```bash
composer create-project --prefer-dist laravel/laravel nama-proyek
```

Atau jika menggunakan Laravel Installer:

```bash
laravel new nama-proyek
```

---

## **3. Class dan Method pada PHP**

### ✅ Definisi:

* **Class**: Struktur yang mendefinisikan properti dan method.
* **Method**: Fungsi yang didefinisikan di dalam class.

### 📘 Contoh:

```php
class Mobil {
    public $merk;
    public $warna;

    public function __construct($merk, $warna) {
        $this->merk = $merk;
        $this->warna = $warna;
    }

    public function infoMobil() {
        return "Mobil $this->merk berwarna $this->warna";
    }
}

// Penggunaan
$mobil1 = new Mobil("Toyota", "Merah");
echo $mobil1->infoMobil();
```

---

### ⚙️ Access Modifier:

| Modifier    | Deskripsi                                    |
| ----------- | -------------------------------------------- |
| `public`    | Dapat diakses dari mana saja                 |
| `private`   | Hanya bisa diakses dari dalam class          |
| `protected` | Hanya bisa diakses dari class dan turunannya |

---

### 🧱 Static Method:

```php
class Kalkulator {
    public static function tambah($a, $b) {
        return $a + $b;
    }
}

echo Kalkulator::tambah(5, 3); // Output: 8
```

---

## 📌 Kesimpulan Pertemuan Ini:

* OOP penting untuk memahami struktur Laravel yang berorientasi objek.
* Tools seperti Composer, VS Code, dan Terminal adalah alat bantu utama dalam pengembangan Laravel.
* Pemahaman class dan method di PHP adalah dasar untuk memahami controller, model, dan berbagai komponen di Laravel.

---

## 🎯 Tugas Mandiri:

1. Buat class `Dosen` dengan properti `nama`, `nidn`, dan method `tampilData()`.
2. Install Laravel secara lokal dan jalankan server lokal (`php artisan serve`).

---
