**project sederhana** Laravel yang mencakup **CRUD** (Create, Read, Update, Delete) dan **Form Validation**.

Project ini akan menggunakan **Laravel 10+**, **Eloquent ORM**, dan **Blade Template**.
Topik yang diangkat: **Manajemen Produk** (`Product Management`).

---

# 📂 **Project Sederhana: Product Management**

## 1️⃣ **Persiapan Project**

Pastikan Laravel sudah terinstall. Jika belum, buat project baru:

```bash
composer create-project laravel/laravel product-crud
cd product-crud
php artisan serve
```

---

## 2️⃣ **Buat Database & Konfigurasi**

* Buat database baru, misalnya `product_crud` di MySQL.
* Atur file `.env`:

```env
DB_DATABASE=product_crud
DB_USERNAME=root
DB_PASSWORD=
```

---

## 3️⃣ **Buat Migration & Model**

```bash
php artisan make:model Product -m
```

Edit file migration `database/migrations/xxxx_xx_xx_create_products_table.php`:

```php
public function up(): void
{
    Schema::create('products', function (Blueprint $table) {
        $table->id();
        $table->string('name');
        $table->decimal('price', 10, 2);
        $table->integer('stock');
        $table->timestamps();
    });
}
```

Jalankan migration:

```bash
php artisan migrate
```

Edit model `app/Models/Product.php`:

```php
class Product extends Model
{
    protected $fillable = ['name', 'price', 'stock'];
}
```

---

## 4️⃣ **Buat Controller**

```bash
php artisan make:controller ProductController --resource
```

Edit `app/Http/Controllers/ProductController.php`:

```php
<?php

namespace App\Http\Controllers;

use App\Models\Product;
use Illuminate\Http\Request;

class ProductController extends Controller
{
    // READ - Menampilkan semua produk
    public function index()
    {
        $products = Product::all();
        return view('products.index', compact('products'));
    }

    // CREATE - Form tambah produk
    public function create()
    {
        return view('products.create');
    }

    // STORE - Simpan produk baru
    public function store(Request $request)
    {
        $request->validate([
            'name'  => 'required|string|max:255',
            'price' => 'required|numeric|min:0',
            'stock' => 'required|integer|min:0',
        ]);

        Product::create($request->all());

        return redirect()->route('products.index')
                         ->with('success', 'Produk berhasil ditambahkan');
    }

    // EDIT - Form edit produk
    public function edit(Product $product)
    {
        return view('products.edit', compact('product'));
    }

    // UPDATE - Perbarui produk
    public function update(Request $request, Product $product)
    {
        $request->validate([
            'name'  => 'required|string|max:255',
            'price' => 'required|numeric|min:0',
            'stock' => 'required|integer|min:0',
        ]);

        $product->update($request->all());

        return redirect()->route('products.index')
                         ->with('success', 'Produk berhasil diperbarui');
    }

    // DELETE - Hapus produk
    public function destroy(Product $product)
    {
        $product->delete();
        return redirect()->route('products.index')
                         ->with('success', 'Produk berhasil dihapus');
    }
}
```

---

## 5️⃣ **Atur Route**

Edit file `routes/web.php`:

```php
use App\Http\Controllers\ProductController;

Route::resource('products', ProductController::class);
```

---

## 6️⃣ **Buat View**

Buat folder `resources/views/products` lalu tambahkan file berikut:

### a) `index.blade.php`

```blade
@extends('layouts.app')

@section('content')
<h1>Daftar Produk</h1>
<a href="{{ route('products.create') }}">Tambah Produk</a>

@if(session('success'))
    <p style="color: green">{{ session('success') }}</p>
@endif

<table border="1" cellpadding="5">
    <tr>
        <th>Nama</th>
        <th>Harga</th>
        <th>Stok</th>
        <th>Aksi</th>
    </tr>
    @foreach($products as $product)
    <tr>
        <td>{{ $product->name }}</td>
        <td>{{ $product->price }}</td>
        <td>{{ $product->stock }}</td>
        <td>
            <a href="{{ route('products.edit', $product) }}">Edit</a>
            <form action="{{ route('products.destroy', $product) }}" method="POST" style="display:inline">
                @csrf
                @method('DELETE')
                <button type="submit" onclick="return confirm('Hapus produk ini?')">Hapus</button>
            </form>
        </td>
    </tr>
    @endforeach
</table>
@endsection
```

### b) `create.blade.php`

```blade
@extends('layouts.app')

@section('content')
<h1>Tambah Produk</h1>

<form action="{{ route('products.store') }}" method="POST">
    @csrf
    <input type="text" name="name" placeholder="Nama Produk" value="{{ old('name') }}">
    @error('name') <p style="color:red">{{ $message }}</p> @enderror

    <input type="number" name="price" placeholder="Harga" value="{{ old('price') }}">
    @error('price') <p style="color:red">{{ $message }}</p> @enderror

    <input type="number" name="stock" placeholder="Stok" value="{{ old('stock') }}">
    @error('stock') <p style="color:red">{{ $message }}</p> @enderror

    <button type="submit">Simpan</button>
</form>
@endsection
```

### c) `edit.blade.php`

```blade
@extends('layouts.app')

@section('content')
<h1>Edit Produk</h1>

<form action="{{ route('products.update', $product) }}" method="POST">
    @csrf
    @method('PUT')
    <input type="text" name="name" value="{{ old('name', $product->name) }}">
    @error('name') <p style="color:red">{{ $message }}</p> @enderror

    <input type="number" name="price" value="{{ old('price', $product->price) }}">
    @error('price') <p style="color:red">{{ $message }}</p> @enderror

    <input type="number" name="stock" value="{{ old('stock', $product->stock) }}">
    @error('stock') <p style="color:red">{{ $message }}</p> @enderror

    <button type="submit">Perbarui</button>
</form>
@endsection
```

---

## 7️⃣ **Buat Layout Dasar**

Buat file `resources/views/layouts/app.blade.php`:

```blade
<!DOCTYPE html>
<html>
<head>
    <title>Manajemen Produk</title>
</head>
<body>
    <div class="container">
        @yield('content')
    </div>
</body>
</html>
```

---

## ✅ **Hasil Akhir**

* **Create** → Tambah produk baru.
* **Read** → Lihat daftar produk di `/products`.
* **Update** → Edit produk yang ada.
* **Delete** → Hapus produk dari database.
* **Form Validation** → Menampilkan pesan error jika input tidak sesuai aturan.

---
