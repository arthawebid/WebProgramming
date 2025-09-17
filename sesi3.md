## 🧑‍🏫 **Materi Perkuliahan: Menerapkan Framework dalam Pemrograman Web**

### 🎯 **Tujuan Umum**

Mahasiswa memahami dan mampu menerapkan konsep MVC dan Routing dalam pengembangan aplikasi web menggunakan framework PHP (Laravel).

---

## 📝 **Pertanyaan Awal (Pre-Test)**

> Digunakan untuk mengukur pemahaman awal mahasiswa terhadap materi.

1. Apa yang dimaksud dengan **framework** dalam pengembangan aplikasi web?
2. Pernahkah Anda mendengar konsep **MVC**? Jika ya, apa kepanjangannya?
3. Dalam pengembangan web, bagaimana biasanya Anda menangani URL dan permintaan user?
4. Apa yang Anda ketahui tentang **routing**?
5. Apakah Anda sudah pernah menggunakan Laravel atau framework PHP lainnya?

---

## 📘 **Sub Materi 1: Konsep MVC (Model - View - Controller)**

### 📚 Penjelasan Singkat

**MVC** adalah pola arsitektur perangkat lunak yang memisahkan aplikasi menjadi tiga bagian utama:

* **Model**: Mengelola logika data dan interaksi database.
* **View**: Menyajikan data ke pengguna (antarmuka).
* **Controller**: Menangani alur aplikasi dan menghubungkan Model dan View.

### 🧱 Struktur MVC di Laravel:

* `app/Models/` → Model
* `resources/views/` → View (Blade template)
* `app/Http/Controllers/` → Controller

### 🔄 Alur MVC Laravel

1. User mengakses URL
2. Route mengarahkan ke Controller
3. Controller mengakses Model
4. Model mengambil data
5. Controller mengirim data ke View
6. View menampilkan data ke user

### ✅ Contoh Kasus

#### Routing:

```php
Route::get('/posts', [PostController::class, 'index']);
```

#### Controller:

```php
public function index() {
    $posts = Post::all();
    return view('posts.index', compact('posts'));
}
```

#### View:

```blade
@foreach($posts as $post)
    <h2>{{ $post->title }}</h2>
@endforeach
```

---

## 📘 **Sub Materi 2: Routing di Framework PHP Laravel**

### 📚 Pengertian

Routing adalah sistem pemetaan URL ke fungsi atau controller dalam aplikasi.

### ✍️ Cara Kerja Routing:

* Laravel menggunakan file `routes/web.php` untuk mendefinisikan route aplikasi berbasis web.

### 🔧 Jenis-Jenis Routing:

| Jenis              | Contoh                                                  | Keterangan                  |
| ------------------ | ------------------------------------------------------- | --------------------------- |
| Basic Route        | `Route::get('/home', function() {...});`                | Langsung definisi fungsi    |
| Controller Route   | `Route::get('/user', [UserController::class, 'show']);` | Memanggil method controller |
| Parameter Route    | `Route::get('/user/{id}', ...)`                         | Menangkap input dari URL    |
| Optional Parameter | `Route::get('/profile/{name?}', ...)`                   | Parameter tidak wajib       |
| Named Route        | `->name('route.name')`                                  | Memudahkan pemanggilan      |
| Group Route        | `Route::prefix('admin')->group(...);`                   | Pengelompokan route         |
| Resource Route     | `Route::resource('posts', PostController::class);`      | CRUD otomatis               |

---

## 💬 **Diskusi Kelas (Opsional)**

* Mengapa menurut Anda pemisahan antara Model, View, dan Controller penting?
* Apa kelebihan Laravel dibanding membuat aplikasi native PHP tanpa framework?

---

## ✅ **Latihan Praktikum**

1. Buatlah sebuah route ke halaman “/about” yang mengembalikan view dengan nama `about.blade.php`.
2. Buatlah controller `ProductController` dengan method `detail($id)`, lalu buat route-nya.
3. Implementasikan view yang menampilkan data produk berdasarkan `id`.

---

## 📝 **Pertanyaan Akhir (Post-Test)**

1. Jelaskan dengan kata-kata Anda sendiri apa itu **MVC** dan bagaimana cara kerjanya di Laravel.
2. Apa fungsi dari masing-masing komponen dalam MVC?
3. Buat contoh routing Laravel yang menggunakan controller dan parameter.
4. Mengapa kita sebaiknya menggunakan **named routes**?
5. Apa yang akan terjadi jika user mengakses URL yang belum didefinisikan dalam file `web.php`?

---

## 📎 **Penutup dan Kesimpulan**

* Laravel menggunakan arsitektur MVC untuk struktur kode yang lebih baik.
* Routing adalah fondasi utama dalam menerima permintaan user di Laravel.
* Pemahaman tentang MVC dan routing adalah dasar penting untuk membangun aplikasi web modern.

---
