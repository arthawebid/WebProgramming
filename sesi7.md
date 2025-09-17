Berikut adalah **materi perkuliahan Laravel** dengan topik:

## **"Menerapkan Framework dalam Pemrograman Web"**

### Sub Tema:

1. **Migration pada Framework Laravel**
2. **Seeding pada Framework Laravel**
   **Disertai Pre-Test dan Post-Test**

---

# 🧑‍🏫 **Materi Perkuliahan Laravel: Migration & Seeding**

---

## 🎯 **Tujuan Pembelajaran**

Setelah mengikuti perkuliahan ini, mahasiswa diharapkan dapat:

* Menjelaskan fungsi dan peran **Migration** dalam pengelolaan struktur database Laravel.
* Membuat dan menjalankan file **migration**.
* Menjelaskan konsep dan manfaat **Seeding**.
* Membuat data dummy menggunakan **Seeder** di Laravel.

---

## 📝 **Pre-Test (Sebelum Materi)**

1. Apa itu *database schema*?
2. Bagaimana biasanya Anda membuat tabel di database saat menggunakan PHP native?
3. Apakah Anda pernah mendengar istilah **migration** di Laravel?
4. Mengapa kita perlu membuat data dummy (palsu) saat proses pengembangan?
5. Apakah Anda mengetahui cara mengisi data otomatis ke database tanpa insert manual?

---

## 📘 **Materi Inti**

---

## 🧱 **1. Migration pada Framework Laravel**

### 📌 Apa itu Migration?

* Migration adalah **fitur Laravel** yang memungkinkan kita untuk **mengelola struktur tabel database menggunakan kode** (bukan klik-klik di phpMyAdmin).
* Migration seperti **version control untuk database** — memudahkan tim untuk melacak perubahan struktur data.

---

### 🧰 **Langkah-langkah Migration**

#### 1. Membuat File Migration

```bash
php artisan make:migration create_products_table
```

#### 2. Isi File Migration

Terletak di folder: `database/migrations/`

Contoh isi:

```php
public function up()
{
    Schema::create('products', function (Blueprint $table) {
        $table->id();
        $table->string('name');
        $table->integer('price');
        $table->timestamps();
    });
}
```

#### 3. Menjalankan Migration

```bash
php artisan migrate
```

#### 4. Rollback (Jika Ingin Dibatalkan)

```bash
php artisan migrate:rollback
```

---

### 📝 Contoh Lengkap

```bash
php artisan make:migration create_mahasiswa_table
```

```php
public function up()
{
    Schema::create('mahasiswa', function (Blueprint $table) {
        $table->id();
        $table->string('nama');
        $table->string('nim')->unique();
        $table->string('jurusan');
        $table->timestamps();
    });
}
```

---

## 🌱 **2. Seeding pada Framework Laravel**

### 📌 Apa itu Seeding?

* Seeder digunakan untuk **mengisi tabel dengan data dummy** secara otomatis.
* Berguna untuk keperluan **testing**, **pengembangan**, atau **presentasi demo**.

---

### 🧰 **Langkah-langkah Seeding**

#### 1. Membuat Seeder

```bash
php artisan make:seeder MahasiswaSeeder
```

#### 2. Isi Seeder

File berada di `database/seeders/MahasiswaSeeder.php`

```php
use Illuminate\Support\Facades\DB;

public function run()
{
    DB::table('mahasiswa')->insert([
        'nama' => 'Andi Saputra',
        'nim' => '12345678',
        'jurusan' => 'Informatika'
    ]);
}
```

#### 3. Jalankan Seeder

```bash
php artisan db:seed --class=MahasiswaSeeder
```

#### 4. Seeder Global (DatabaseSeeder.php)

Buka `database/seeders/DatabaseSeeder.php`:

```php
public function run()
{
    $this->call([
        MahasiswaSeeder::class,
    ]);
}
```

Lalu jalankan:

```bash
php artisan db:seed
```

---

### 🔁 Faker untuk Data Dummy Banyak

Tambahkan di `MahasiswaSeeder.php`:

```php
use Faker\Factory as Faker;

public function run()
{
    $faker = Faker::create();

    foreach(range(1, 10) as $i){
        DB::table('mahasiswa')->insert([
            'nama' => $faker->name,
            'nim' => $faker->unique()->numerify('########'),
            'jurusan' => $faker->randomElement(['Informatika', 'Sistem Informasi', 'Teknik Komputer']),
        ]);
    }
}
```

---

## ✅ **Post-Test (Setelah Materi)**

1. Jelaskan apa fungsi utama dari **migration** di Laravel!
2. Bagaimana cara membuat tabel baru menggunakan migration?
3. Apa yang terjadi ketika Anda menjalankan perintah `php artisan migrate`?
4. Jelaskan perbedaan antara **migration** dan **seeder**!
5. Tuliskan perintah untuk menjalankan seeder bernama `ProductSeeder`.

---

## 🧪 **Latihan Praktik (Opsional)**

1. Buat migration `create_books_table` dengan field:

   * `id`, `judul`, `pengarang`, `tahun_terbit`, `created_at`, `updated_at`
2. Buat Seeder `BookSeeder` yang mengisi 10 data dummy dengan Faker.
3. Jalankan migration dan seeder lalu tampilkan hasilnya di database.

---

## 📎 **Kesimpulan**

* **Migration** membantu pengelolaan struktur database secara efisien dan dapat dikontrol melalui versi kode.
* **Seeding** digunakan untuk mengisi database dengan data awal atau data testing secara otomatis.
* Keduanya sangat penting dalam proses pengembangan web modern menggunakan Laravel.

---

## 📚 **Referensi**

* Laravel Docs – [Database: Migrations](https://laravel.com/docs/migrations)
* Laravel Docs – [Database: Seeding](https://laravel.com/docs/seeding)
* Laracasts – *Laravel From Scratch* series

---
