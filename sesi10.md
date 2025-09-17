Baik! Berikut saya buatkan **materi perkuliahan** dengan subtema **Object Relational Mapping (ORM) di Framework PHP** beserta **Penggunaan Eloquent ORM**, lengkap dengan **pretest** dan **posttest** berformat esai.

---

# 📚 Materi Perkuliahan

## **Object Relational Mapping (ORM) dan Eloquent ORM di Laravel**

---

### 🎯 **Tujuan Pembelajaran**

Setelah mengikuti perkuliahan ini, mahasiswa diharapkan dapat:

1. Memahami konsep **Object Relational Mapping (ORM)** dalam pengembangan aplikasi berbasis PHP.
2. Menjelaskan cara kerja **Eloquent ORM** sebagai implementasi ORM di Laravel.
3. Menggunakan **Eloquent ORM** untuk melakukan operasi **CRUD** pada database.

---
## 📝 **Pretest**

**Instruksi:** Jawab dengan singkat dan jelas.

1. Apa yang Anda ketahui tentang Object Relational Mapping (ORM)?
2. Mengapa ORM dianggap mempermudah pengembang dibandingkan menulis query SQL manual?
3. Jelaskan hubungan antara **class** dan **tabel** dalam konsep ORM.
4. Apa peran Model dalam arsitektur MVC?
5. Berikan contoh penggunaan ORM (secara umum, tidak harus Eloquent).

---

## 1️⃣ **Konsep Object Relational Mapping (ORM)**

**Definisi:**
Object Relational Mapping (ORM) adalah teknik pemrograman yang digunakan untuk memetakan (mapping) objek dalam bahasa pemrograman ke tabel pada database relasional. Dengan ORM, kita dapat berinteraksi dengan database menggunakan **objek** dan **metode**, bukan menulis query SQL secara manual.

**Manfaat ORM:**

* Memudahkan pengembang untuk bekerja dengan database tanpa menulis SQL mentah.
* Meningkatkan keterbacaan dan maintainability kode.
* Mendukung keamanan dengan mencegah SQL Injection melalui parameter binding.
* Mendukung hubungan antar tabel (relasi) seperti **One-to-One**, **One-to-Many**, dan **Many-to-Many**.

**Konsep Dasar ORM:**

| Konsep OOP | Konsep Database                                |
| ---------- | ---------------------------------------------- |
| Class      | Tabel                                          |
| Object     | Baris/Record                                   |
| Attribute  | Kolom/Field                                    |
| Method     | Operasi Query (Insert, Select, Update, Delete) |

---

## 2️⃣ **Eloquent ORM di Laravel**

Laravel menggunakan **Eloquent** sebagai implementasi ORM-nya.
Eloquent memudahkan pengembang untuk mengakses dan memanipulasi data menggunakan **Model**.

### **Membuat Model**

```bash
php artisan make:model Product
```

Kode di atas akan membuat file `Product.php` di folder `app/Models`.

### **Contoh Model**

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Model;

class Product extends Model
{
    protected $fillable = ['name', 'price', 'stock'];
}
```

---

### **Operasi CRUD dengan Eloquent**

#### 1. **Create (Insert)**

```php
Product::create([
    'name' => 'Laptop',
    'price' => 15000000,
    'stock' => 5
]);
```

#### 2. **Read (Select)**

```php
$products = Product::all(); // Ambil semua data
$product = Product::find(1); // Ambil data berdasarkan ID
```

#### 3. **Update**

```php
$product = Product::find(1);
$product->price = 14000000;
$product->save();
```

#### 4. **Delete**

```php
$product = Product::find(1);
$product->delete();
```

---

### **Relasi di Eloquent**

Contoh relasi **One-to-Many** (satu kategori memiliki banyak produk):

```php
// Model Category
public function products()
{
    return $this->hasMany(Product::class);
}
```

Dengan ini, kita dapat mengambil semua produk dari kategori tertentu:

```php
$category = Category::find(1);
$products = $category->products;
```

---

## 3️⃣ **Kelebihan Eloquent ORM**

* Sintaks sederhana dan mudah dibaca.
* Mendukung relasi antar tabel dengan cara yang natural.
* Mengurangi penulisan query SQL secara manual.
* Mendukung fitur seperti **lazy loading**, **eager loading**, dan **mutators/accessors**.

---

## 📝 **Posttest**

**Instruksi:** Jawab dengan uraian yang terstruktur dan sertakan contoh kode jika perlu.

1. Jelaskan perbedaan antara ORM dan query SQL biasa.
2. Bagaimana cara membuat Model baru di Laravel menggunakan Artisan Command?
3. Tulis contoh kode **Eloquent ORM** untuk menambahkan data baru ke tabel `products` dengan field `name`, `price`, dan `stock`.
4. Bagaimana cara memperbarui data menggunakan Eloquent ORM? Jelaskan langkah-langkahnya.
5. Jelaskan salah satu jenis relasi di Eloquent ORM beserta contoh penggunaannya.

---
