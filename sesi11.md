<img width="1024" height="1536" alt="image" src="https://github.com/user-attachments/assets/8dfdd253-0aa1-494f-a2b8-e053d9d44317" />Baik! Saya buatkan **materi perkuliahan** yang fokus pada **Proses Create, Read, Update, Delete (CRUD) di Laravel** dan **Form Validation di Laravel** supaya bisa langsung digunakan untuk pengajaran.

---

# 📚 Materi Perkuliahan

## **CRUD dan Form Validation di Laravel**

---

### 🎯 **Tujuan Pembelajaran**

Setelah mengikuti perkuliahan ini, mahasiswa diharapkan dapat:

1. Memahami alur **CRUD** pada Laravel menggunakan Model, Controller, dan View.
2. Mampu mengimplementasikan operasi **Create, Read, Update, Delete** pada aplikasi Laravel.
3. Memahami dan menerapkan **Form Validation** menggunakan fitur bawaan Laravel.

---

## 📝 **Pretest**

1. Apa yang Anda ketahui tentang CRUD? Jelaskan masing-masing komponennya.
2. Mengapa kita memerlukan validasi form pada aplikasi berbasis web?
3. Apa perbedaan antara `required` dan `nullable` pada validasi Laravel?
4. Bagaimana alur data dari form sampai tersimpan di database menggunakan Laravel?
5. Jelaskan secara singkat peran Model pada proses CRUD.
---

## 1️⃣ **Konsep CRUD di Laravel**

CRUD adalah singkatan dari **Create**, **Read**, **Update**, dan **Delete**. Ini merupakan operasi dasar yang dilakukan terhadap data dalam aplikasi.

Di Laravel, CRUD biasanya dilakukan menggunakan:

* **Route** → Menentukan URL dan method.
* **Controller** → Menangani logika bisnis.
* **Model** → Menghubungkan data dengan database.
* **View** → Menampilkan data di antarmuka pengguna.

---

## 2️⃣ **Contoh Implementasi CRUD**

### 🟢 **1. Create (Menyimpan Data Baru)**

**Route:**

```php
Route::post('/products', [ProductController::class, 'store']);
```

**Controller:**

```php
use App\Models\Product;

public function store(Request $request)
{
    // Validasi data
    $request->validate([
        'name' => 'required|string|max:255',
        'price' => 'required|numeric|min:0',
        'stock' => 'required|integer|min:0',
    ]);

    // Simpan data
    Product::create($request->all());

    return redirect()->back()->with('success', 'Produk berhasil ditambahkan!');
}
```

---

### 🔵 **2. Read (Menampilkan Data)**

**Route:**

```php
Route::get('/products', [ProductController::class, 'index']);
```

**Controller:**

```php
public function index()
{
    $products = Product::all();
    return view('products.index', compact('products'));
}
```

**View (Blade):**

```blade
@foreach($products as $product)
    <p>{{ $product->name }} - {{ $product->price }}</p>
@endforeach
```

---

### 🟠 **3. Update (Memperbarui Data)**

**Route:**

```php
Route::put('/products/{id}', [ProductController::class, 'update']);
```

**Controller:**

```php
public function update(Request $request, $id)
{
    $request->validate([
        'name' => 'required|string|max:255',
        'price' => 'required|numeric|min:0',
        'stock' => 'required|integer|min:0',
    ]);

    $product = Product::findOrFail($id);
    $product->update($request->all());

    return redirect()->back()->with('success', 'Produk berhasil diperbarui!');
}
```

---

### 🔴 **4. Delete (Menghapus Data)**

**Route:**

```php
Route::delete('/products/{id}', [ProductController::class, 'destroy']);
```

**Controller:**

```php
public function destroy($id)
{
    $product = Product::findOrFail($id);
    $product->delete();

    return redirect()->back()->with('success', 'Produk berhasil dihapus!');
}
```

---

## 3️⃣ **Form Validation di Laravel**

Laravel menyediakan sistem validasi yang mudah digunakan melalui method **validate()** pada class `Request`.

### **Contoh Validasi:**

```php
$request->validate([
    'name'  => 'required|string|max:255',
    'email' => 'required|email|unique:users',
    'age'   => 'nullable|integer|min:18',
]);
```

**Keterangan:**

* `required` → field wajib diisi.
* `string`, `email`, `integer` → tipe data yang diizinkan.
* `max:255` → panjang maksimal 255 karakter.
* `unique:users` → nilai harus unik di tabel `users`.
* `min:18` → nilai minimal 18.

Jika validasi gagal, Laravel otomatis:

* Redirect kembali ke halaman sebelumnya.
* Mengirimkan pesan error yang bisa ditampilkan di **View**.

**Contoh menampilkan error di Blade:**

```blade
@error('name')
    <div class="text-red-500">{{ $message }}</div>
@enderror
```

---

## 4️⃣ **Keuntungan Menggunakan Form Validation Laravel**

✅ Mengurangi kemungkinan input data yang salah.
✅ Mencegah SQL Injection dan bug karena data tidak sesuai format.
✅ Pesan error otomatis bisa ditampilkan ke pengguna.
✅ Sangat mudah diterapkan pada setiap controller.


---

## 📝 **Posttest**

1. Jelaskan langkah-langkah membuat fitur Create (penyimpanan data baru) di Laravel.
2. Berikan contoh kode controller untuk menampilkan semua data produk dari database menggunakan Eloquent ORM.
3. Bagaimana cara melakukan validasi agar field `email` tidak boleh sama dengan data yang sudah ada di tabel `users`?
4. Tulis contoh kode untuk memperbarui data produk menggunakan `ProductController`.
5. Jelaskan cara menampilkan pesan error validasi pada view menggunakan Blade.

---
