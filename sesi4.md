Berikut adalah **materi perkuliahan Laravel** dengan subtopik:

## **"View dan Templating Engine di Framework Laravel"**

---

## 🧑‍🏫 **Topik: View dan Blade Templating di Laravel**

### 🎯 **Tujuan Pembelajaran**

Setelah mengikuti materi ini, mahasiswa diharapkan:

* Memahami konsep **View** dalam Laravel.
* Mampu menggunakan **Blade**, templating engine Laravel.
* Dapat membuat tampilan antarmuka pengguna yang dinamis dan terstruktur.

---

## 📘 **1. Pengertian View di Laravel**

### 📌 Apa itu View?

* **View** adalah bagian dari arsitektur **MVC** yang bertugas menampilkan **antarmuka pengguna (UI)**.
* Di Laravel, **View** biasanya berupa file HTML yang dapat menggunakan sintaks khusus dari **Blade** (templating engine Laravel).

> File View disimpan di direktori:
> **`resources/views/`**

---

## 📘 **2. Blade: Templating Engine Laravel**

### 🔍 Apa itu Blade?

* **Blade** adalah templating engine bawaan Laravel yang ringan dan powerful.
* Mendukung **inheritance**, **komponen**, dan **kontrol struktur** seperti `if`, `foreach`, dll.
* Ekstensi file: `.blade.php`

---

## 📂 **3. Struktur View dan Layout Blade**

### 🧱 **Contoh Dasar View:**

```blade
<!-- resources/views/welcome.blade.php -->
<!DOCTYPE html>
<html>
<head>
    <title>Welcome Page</title>
</head>
<body>
    <h1>Selamat Datang di Laravel</h1>
</body>
</html>
```

### 🧩 **View dengan Data dari Controller**

```php
// routes/web.php
Route::get('/greeting', function () {
    return view('greeting', ['name' => 'Mahasiswa']);
});
```

```blade
<!-- resources/views/greeting.blade.php -->
<h1>Halo, {{ $name }}!</h1>
```

---

## 🎨 **4. Blade Templating Features**

### ✅ Ekspresi Blade:

```blade
{{ $nama }}      // Echo dengan auto escaping
{!! $html !!}    // Echo tanpa escaping (gunakan dengan hati-hati)
```

### ✅ Control Structures:

```blade
@if($user)
    Hello, {{ $user->name }}
@else
    Hello, Guest
@endif

@foreach($posts as $post)
    <p>{{ $post->title }}</p>
@endforeach
```

### ✅ Komentar di Blade:

```blade
{{-- Ini komentar Blade --}}
```

---

## 📦 **5. Layouting dengan Blade Templating**

### 🔄 Konsep Layout (Template Inheritance)

#### 1. **Membuat Template Induk**

```blade
<!-- resources/views/layouts/app.blade.php -->
<!DOCTYPE html>
<html>
<head>
    <title>@yield('title')</title>
</head>
<body>
    <div class="content">
        @yield('content')
    </div>
</body>
</html>
```

#### 2. **Membuat View Anak**

```blade
<!-- resources/views/pages/home.blade.php -->
@extends('layouts.app')

@section('title', 'Beranda')

@section('content')
    <h1>Selamat datang di halaman Beranda</h1>
@endsection
```

---

## 🧰 **6. Include dan Komponen Blade**

### ✅ Include View:

```blade
@include('partials.header')
```

### ✅ Komponen Blade (Laravel 7+):

```blade
<x-alert type="danger" message="Gagal menyimpan data!" />
```

---

## 📝 **Latihan Mandiri**

1. Buat sebuah layout utama `layouts/main.blade.php` yang memiliki header dan footer.
2. Buat view `home.blade.php` yang mewarisi layout tersebut dan menampilkan daftar nama mahasiswa.
3. Gunakan perulangan Blade (`@foreach`) untuk menampilkan data array dari controller.

---

## 📝 **Tugas atau Quiz Singkat**

1. Apa fungsi `@yield` dan `@section` dalam Blade?
2. Buat file `about.blade.php` yang mewarisi layout utama dan menampilkan biodata Anda.
3. Jelaskan perbedaan `{{ }}` dan `{!! !!}` di Blade.

---

## 📎 **Kesimpulan**

* View di Laravel digunakan untuk menyajikan UI.
* Blade adalah templating engine Laravel yang sangat efisien dan terintegrasi.
* Blade mendukung layout inheritance, komponen, dan kontrol struktur.

---

## 📚 **Referensi Tambahan**

* [Laravel Official Docs – Blade](https://laravel.com/docs/blade)
* [Laracasts – Views & Blade](https://laracasts.com)

---
