Berikut adalah **materi perkuliahan Laravel** dengan topik:

## **"Controller dan Parameter pada Controller di Laravel"**

Lengkap dengan **Pre-Test** dan **Post-Test** untuk mahasiswa.

---

# 🧑‍🏫 Materi Perkuliahan Laravel

## 📘 **Controller dan Parameter pada Controller**

---

## 🎯 **Tujuan Pembelajaran**

Setelah mengikuti materi ini, mahasiswa mampu:

* Menjelaskan peran controller dalam arsitektur MVC.
* Membuat controller dan method dengan parameter.
* Menggunakan parameter dari URL untuk menangani request dinamis di Laravel.

---

## 📝 **Pre-Test (Sebelum Materi Disampaikan)**

1. Apa itu controller dalam arsitektur MVC?
2. Apa perbedaan antara controller dan route closure (fungsi langsung di route)?
3. Bagaimana cara mengirim data dari URL ke controller?
4. Apakah Anda tahu apa itu parameter dinamis pada route?
5. Contoh URL `/produk/5` kira-kira membawa informasi apa?

---

## 📚 **Materi Inti**

---

## 📌 1. **Pengertian Controller di Laravel**

### 🔎 Fungsi Controller:

* Sebagai **penghubung antara View dan Model**
* Menangani permintaan (request) dari user
* Memproses logika aplikasi, lalu mengembalikan respon (View/JSON/dll)

---

## 📌 2. **Membuat Controller**

Gunakan perintah artisan:

```bash
php artisan make:controller ProdukController
```

Controller dibuat di folder:
`app/Http/Controllers/ProdukController.php`

---

## 📌 3. **Membuat Method di Controller**

Contoh method sederhana:

```php
public function index() {
    return view('produk.index');
}
```

---

## 📌 4. **Parameter pada Controller**

Parameter digunakan untuk menerima input dari **URL**.

### 📌 Contoh 1: Parameter Biasa

**Route:**

```php
Route::get('/produk/{id}', [ProdukController::class, 'show']);
```

**Controller:**

```php
public function show($id) {
    return "Menampilkan produk dengan ID: " . $id;
}
```

**Akses URL:**

```
http://localhost:8000/produk/5
```

Output:

```
Menampilkan produk dengan ID: 5
```

---

### 📌 Contoh 2: Parameter dengan Default Value

**Route:**

```php
Route::get('/user/{nama?}', [UserController::class, 'profil']);
```

**Controller:**

```php
public function profil($nama = 'Guest') {
    return "Halo, " . $nama;
}
```

---

### 📌 Contoh 3: Parameter Bertipe Array

```php
public function tampilkanProduk($kategori, $id) {
    return "Kategori: $kategori, ID Produk: $id";
}
```

**Route:**

```php
Route::get('/produk/{kategori}/{id}', [ProdukController::class, 'tampilkanProduk']);
```

---

## 🛠️ 5. **Validasi Parameter (Opsional)**

Validasi bisa dilakukan langsung di controller:

```php
public function show($id) {
    if (!is_numeric($id)) {
        abort(404);
    }
    return "ID Produk: $id";
}
```

---

## 💡 Tips Best Practice

* Gunakan nama parameter yang deskriptif (`$id`, `$slug`, `$username`).
* Validasi parameter jika dibutuhkan.
* Gunakan **Route Model Binding** untuk mengakses data langsung dari model.

---

## ✅ **Post-Test (Setelah Materi Disampaikan)**

1. Apa fungsi dari controller dalam Laravel?
2. Jelaskan bagaimana parameter dikirim melalui URL ke controller!
3. Tuliskan contoh route dengan parameter `{id}` yang memanggil method `detail()` di `ProdukController`.
4. Apa yang terjadi jika parameter pada URL tidak sesuai format yang diharapkan?
5. Bagaimana cara memberi nilai default pada parameter controller?

---

## 🧠 **Latihan Praktik (Opsional)**

1. Buat controller `MahasiswaController` dengan method `detail($nim)`.
2. Buat route `/mahasiswa/{nim}` yang memanggil method tersebut.
3. Tampilkan output:
   `"Detail Mahasiswa dengan NIM: 12345678"`

---

## 📎 **Kesimpulan**

* Controller menerima input dari route dan mengatur respon yang akan diberikan.
* Parameter digunakan untuk menangkap input dari URL ke controller.
* Laravel mendukung parameter wajib, opsional, dan juga validasi manual pada controller.

---

## 📚 **Referensi Tambahan**

* Laravel Docs: [Controllers](https://laravel.com/docs/controllers)
* Laravel Docs: [Routing - Parameters](https://laravel.com/docs/routing#parameters)
