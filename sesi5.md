Berikut adalah **contoh project sederhana** untuk **menerapkan View dan Templating Engine (Blade)** di framework **Laravel**:

---

# 🧑‍💻 **Mini Project: Aplikasi Daftar Produk Menggunakan View dan Blade (Laravel)**

## 🎯 **Tujuan Project**

Mahasiswa mampu:

* Membuat tampilan menggunakan Blade templating engine.
* Menggunakan layout (`@extends`, `@section`) dan include (`@include`).
* Menampilkan data dinamis dari controller ke view.

---

## 🧱 **Deskripsi Proyek**

Membuat aplikasi sederhana untuk menampilkan **daftar produk**.
Fungsi utama:

* Halaman utama menampilkan semua produk.
* Menggunakan layout dan komponen Blade.

---

## 🧰 **Langkah-Langkah Proyek**

### 1. **Persiapan Project Laravel**

Install Laravel (jika belum):

```bash
composer create-project laravel/laravel produkApp
cd produkApp
php artisan serve
```

---

### 2. **Buat Route di `routes/web.php`**

```php
use Illuminate\Support\Facades\Route;
use App\Http\Controllers\ProductController;

Route::get('/', [ProductController::class, 'index']);
```

---

### 3. **Buat Controller**

```bash
php artisan make:controller ProductController
```

Edit `app/Http/Controllers/ProductController.php`:

```php
namespace App\Http\Controllers;

use Illuminate\Http\Request;

class ProductController extends Controller
{
    public function index()
    {
        $produk = [
            ['nama' => 'Laptop', 'harga' => 10000000],
            ['nama' => 'Smartphone', 'harga' => 5000000],
            ['nama' => 'Headset', 'harga' => 300000],
        ];

        return view('produk.index', compact('produk'));
    }
}
```

---

### 4. **Buat Layout Blade**

**File:** `resources/views/layouts/app.blade.php`

```blade
<!DOCTYPE html>
<html>
<head>
    <title>@yield('title')</title>
    <style>
        body { font-family: Arial; margin: 20px; }
        .container { max-width: 600px; margin: auto; }
        header, footer { background: #f4f4f4; padding: 10px; text-align: center; }
    </style>
</head>
<body>
    <header>
        <h2>Aplikasi Daftar Produk</h2>
    </header>

    <div class="container">
        @yield('content')
    </div>

    <footer>
        <p>© 2025 Laravel Project</p>
    </footer>
</body>
</html>
```

---

### 5. **Buat View `produk/index.blade.php`**

**File:** `resources/views/produk/index.blade.php`

```blade
@extends('layouts.app')

@section('title', 'Daftar Produk')

@section('content')
    <h3>Daftar Produk</h3>

    <ul>
        @foreach ($produk as $item)
            <li>
                {{ $item['nama'] }} - Rp {{ number_format($item['harga'], 0, ',', '.') }}
            </li>
        @endforeach
    </ul>
@endsection
```

---

## ✅ **Hasil Akhir**

Jika Anda mengakses `http://localhost:8000`, maka akan muncul halaman:

```
Aplikasi Daftar Produk
-----------------------
Daftar Produk
- Laptop - Rp 10.000.000
- Smartphone - Rp 5.000.000
- Headset - Rp 300.000
```

---

## 📚 **Fitur Blade yang Diterapkan**

| Fitur             | Contoh                    |
| ----------------- | ------------------------- |
| Layout            | `@extends('layouts.app')` |
| Section           | `@section('content')`     |
| Output Data       | `{{ $item['nama'] }}`     |
| Control Structure | `@foreach`                |

---

## 📝 **Pengembangan Selanjutnya (Opsional)**

* Tambahkan fitur detail produk (`/produk/{id}`)
* Gunakan komponen Blade untuk produk
* Integrasikan Bootstrap untuk tampilan menarik

---
