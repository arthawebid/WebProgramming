Berikut adalah **materi perkuliahan** untuk topik **“Menerapkan Framework dalam Pemrograman Web”** dengan fokus pada **Laravel**, mencakup tiga sub materi utama:

---

## 🧾 **Mata Kuliah**: Menerapkan Framework dalam Pemrograman Web

### 🧩 **Topik Khusus**: Laravel – Model, Query Builder, dan Penggunaan Query Builder

---

## 🎯 **Tujuan Pembelajaran**

Setelah mengikuti materi ini, mahasiswa diharapkan dapat:

1. Memahami konsep dan peran **Model** dalam arsitektur MVC Laravel.
2. Menggunakan **Query Builder** untuk berinteraksi dengan database secara efisien.
3. Mengimplementasikan **Query Builder** untuk operasi CRUD dalam aplikasi Laravel.

---
## 📝 **Pretest** (Sebelum Materi)

**Tujuan:** Mengukur pemahaman awal mahasiswa tentang konsep Model, Query Builder, dan CRUD di Laravel.

**Instruksi:** Jawab setiap pertanyaan berikut dengan uraian yang jelas dan singkat.

1. Jelaskan apa yang Anda ketahui tentang **Model** pada framework Laravel.
2. Menurut Anda, bagaimana cara Laravel berinteraksi dengan database?
3. Apa yang dimaksud dengan **CRUD**? Sebutkan contoh sederhana dari masing-masing operasi.
4. Jelaskan perbedaan antara **Eloquent ORM** dan **Query Builder** (jika Anda mengetahuinya).
5. Mengapa kita perlu memisahkan logika bisnis dari tampilan (View) dalam sebuah aplikasi?

---
## 📚 Sub Materi 1: **Model di Framework Laravel**

### 📌 1.1. Apa itu Model?

* Komponen dari pola **MVC (Model-View-Controller)** yang bertanggung jawab untuk mengelola data dan logika bisnis.
* Model di Laravel berinteraksi langsung dengan **tabel database**.

### 📌 1.2. Membuat Model

```bash
php artisan make:model NamaModel
```

Contoh:

```bash
php artisan make:model Mahasiswa
```

### 📌 1.3. Struktur Dasar Model

```php
namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Mahasiswa extends Model
{
    protected $table = 'mahasiswa';
    protected $fillable = ['nama', 'nim', 'jurusan'];
}
```

### 📌 1.4. Kelebihan Model di Laravel

* Menggunakan **Eloquent ORM**: Memudahkan pemetaan antara objek dan tabel.
* Dapat mengatur relasi antar tabel seperti `hasOne`, `hasMany`, `belongsTo`, dll.

---

## 📚 Sub Materi 2: **Query Builder di Framework Laravel**

### 📌 2.1. Apa itu Query Builder?

* Fitur Laravel untuk menyusun query SQL secara **fleksibel dan aman** menggunakan PHP.
* Mendukung **SQL injection protection**.

### 📌 2.2. Kapan Menggunakan Query Builder?

* Saat tidak membutuhkan fitur lengkap dari Eloquent.
* Ketika membutuhkan performa tinggi untuk query kompleks.

### 📌 2.3. Contoh Struktur Query Builder

```php
use Illuminate\Support\Facades\DB;

$data = DB::table('mahasiswa')->get();
```

---

## 📚 Sub Materi 3: **Penggunaan Query Builder (Operasi CRUD)**

### 🟩 **3.1. CREATE (Insert Data)**

```php
DB::table('mahasiswa')->insert([
    'nama' => 'Budi',
    'nim' => '12345678',
    'jurusan' => 'Informatika'
]);
```

### 🟨 **3.2. READ (Mengambil Data)**

* Ambil semua data:

```php
$mahasiswa = DB::table('mahasiswa')->get();
```

* Ambil satu data:

```php
$mahasiswa = DB::table('mahasiswa')->where('nim', '12345678')->first();
```

### 🟧 **3.3. UPDATE (Memperbarui Data)**

```php
DB::table('mahasiswa')
  ->where('nim', '12345678')
  ->update(['jurusan' => 'Sistem Informasi']);
```

### 🟥 **3.4. DELETE (Menghapus Data)**

```php
DB::table('mahasiswa')
  ->where('nim', '12345678')
  ->delete();
```

---

## 🎓 Studi Kasus Mini

**Deskripsi**: Buat fitur untuk menampilkan data mahasiswa, menambah data, dan menghapus data menggunakan Query Builder.

**Langkah-langkah**:

1. Buat tabel `mahasiswa` di migration.
2. Buat route dan controller.
3. Gunakan Query Builder untuk operasi CRUD di controller.

---

## 🧠 Latihan Mahasiswa

### Tugas Individu:

1. Buat model `Dosen`.
2. Buat form input dosen dan simpan data menggunakan query builder.
3. Tampilkan daftar dosen menggunakan query builder.

---

## 🧩 Rangkuman

| Komponen      | Fungsi                                            |
| ------------- | ------------------------------------------------- |
| Model         | Representasi tabel, digunakan dengan Eloquent ORM |
| Query Builder | Menyusun query SQL secara dinamis & aman          |
| CRUD          | Operasi utama: Insert, Read, Update, Delete       |

---

## 📝 **Posttest** (Setelah Materi)

**Tujuan:** Mengukur pemahaman mahasiswa setelah mempelajari konsep Model, Query Builder, dan implementasi CRUD di Laravel.

**Instruksi:** Jawab dengan uraian yang terstruktur dan sertakan contoh kode jika perlu.

1. Jelaskan peran **Model** dalam arsitektur MVC Laravel dan bagaimana Model berhubungan dengan database.
2. Berikan contoh penggunaan **Query Builder** untuk mengambil semua data dari tabel `users` dengan kondisi `status = 'active'`.
3. Jelaskan langkah-langkah implementasi **CRUD** menggunakan Query Builder di Laravel, mulai dari Create hingga Delete.
4. Mengapa **Query Builder** dianggap efisien dibandingkan menulis SQL mentah?
5. Berikan satu contoh kode **Query Builder** untuk memperbarui kolom `email` pada tabel `users` berdasarkan `id` tertentu.

---

## 📎 Referensi

* [Laravel Official Documentation – Models](https://laravel.com/docs/models)
* [Laravel Official Documentation – Query Builder](https://laravel.com/docs/queries)

---
