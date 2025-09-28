# 📂 **Project Sederhana 2: Student Management**

## 1️⃣ **Persiapan Project**

Jika sudah ada project Laravel sebelumnya, bisa langsung gunakan.
Jika ingin terpisah, buat project baru:

```bash
composer create-project laravel/laravel student-crud
cd student-crud
php artisan serve
```

---

## 2️⃣ **Buat Database & Konfigurasi**

Buat database `student_crud` di MySQL, lalu atur `.env`:

```env
DB_DATABASE=student_crud
DB_USERNAME=root
DB_PASSWORD=
```

---

## 3️⃣ **Buat Migration & Model**

```bash
php artisan make:model Student -m
```

Edit file migration `create_students_table.php`:

```php
public function up(): void
{
    Schema::create('students', function (Blueprint $table) {
        $table->id();
        $table->string('name');
        $table->string('email')->unique();
        $table->string('major'); // Jurusan
        $table->integer('age');
        $table->timestamps();
    });
}
```

Jalankan migration:

```bash
php artisan migrate
```

Edit `app/Models/Student.php`:

```php
class Student extends Model
{
    protected $fillable = ['name', 'email', 'major', 'age'];
}
```

---

## 4️⃣ **Buat Controller**

```bash
php artisan make:controller StudentController --resource
```

Isi `app/Http/Controllers/StudentController.php`:

```php
<?php

namespace App\Http\Controllers;

use App\Models\Student;
use Illuminate\Http\Request;

class StudentController extends Controller
{
    public function index()
    {
        $students = Student::all();
        return view('students.index', compact('students'));
    }

    public function create()
    {
        return view('students.create');
    }

    public function store(Request $request)
    {
        $request->validate([
            'name'  => 'required|string|max:255',
            'email' => 'required|email|unique:students',
            'major' => 'required|string|max:100',
            'age'   => 'required|integer|min:17',
        ]);

        Student::create($request->all());

        return redirect()->route('students.index')
                         ->with('success', 'Mahasiswa berhasil ditambahkan');
    }

    public function edit(Student $student)
    {
        return view('students.edit', compact('student'));
    }

    public function update(Request $request, Student $student)
    {
        $request->validate([
            'name'  => 'required|string|max:255',
            'email' => 'required|email|unique:students,email,' . $student->id,
            'major' => 'required|string|max:100',
            'age'   => 'required|integer|min:17',
        ]);

        $student->update($request->all());

        return redirect()->route('students.index')
                         ->with('success', 'Data mahasiswa diperbarui');
    }

    public function destroy(Student $student)
    {
        $student->delete();

        return redirect()->route('students.index')
                         ->with('success', 'Data mahasiswa dihapus');
    }
}
```

---

## 5️⃣ **Atur Route**

`routes/web.php`:

```php
use App\Http\Controllers\StudentController;

Route::resource('students', StudentController::class);
```

---

## 6️⃣ **Buat View**

Buat folder `resources/views/students`:

### a) `index.blade.php`

```blade
@extends('layouts.app')

@section('content')
<h1>Daftar Mahasiswa</h1>
<a href="{{ route('students.create') }}">Tambah Mahasiswa</a>

@if(session('success'))
    <p style="color: green">{{ session('success') }}</p>
@endif

<table border="1" cellpadding="5">
    <tr>
        <th>Nama</th>
        <th>Email</th>
        <th>Jurusan</th>
        <th>Usia</th>
        <th>Aksi</th>
    </tr>
    @foreach($students as $student)
    <tr>
        <td>{{ $student->name }}</td>
        <td>{{ $student->email }}</td>
        <td>{{ $student->major }}</td>
        <td>{{ $student->age }}</td>
        <td>
            <a href="{{ route('students.edit', $student) }}">Edit</a>
            <form action="{{ route('students.destroy', $student) }}" method="POST" style="display:inline">
                @csrf
                @method('DELETE')
                <button type="submit" onclick="return confirm('Hapus data ini?')">Hapus</button>
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
<h1>Tambah Mahasiswa</h1>

<form action="{{ route('students.store') }}" method="POST">
    @csrf
    <input type="text" name="name" placeholder="Nama" value="{{ old('name') }}">
    @error('name') <p style="color:red">{{ $message }}</p> @enderror

    <input type="email" name="email" placeholder="Email" value="{{ old('email') }}">
    @error('email') <p style="color:red">{{ $message }}</p> @enderror

    <input type="text" name="major" placeholder="Jurusan" value="{{ old('major') }}">
    @error('major') <p style="color:red">{{ $message }}</p> @enderror

    <input type="number" name="age" placeholder="Usia" value="{{ old('age') }}">
    @error('age') <p style="color:red">{{ $message }}</p> @enderror

    <button type="submit">Simpan</button>
</form>
@endsection
```

### c) `edit.blade.php`

```blade
@extends('layouts.app')

@section('content')
<h1>Edit Mahasiswa</h1>

<form action="{{ route('students.update', $student) }}" method="POST">
    @csrf
    @method('PUT')
    <input type="text" name="name" value="{{ old('name', $student->name) }}">
    @error('name') <p style="color:red">{{ $message }}</p> @enderror

    <input type="email" name="email" value="{{ old('email', $student->email) }}">
    @error('email') <p style="color:red">{{ $message }}</p> @enderror

    <input type="text" name="major" value="{{ old('major', $student->major) }}">
    @error('major') <p style="color:red">{{ $message }}</p> @enderror

    <input type="number" name="age" value="{{ old('age', $student->age) }}">
    @error('age') <p style="color:red">{{ $message }}</p> @enderror

    <button type="submit">Perbarui</button>
</form>
@endsection
```

---

## 7️⃣ **Layout Dasar**

Gunakan `layouts/app.blade.php` seperti pada project sebelumnya.

---

## ✅ **Fitur yang Dicakup**

* **Create** → Tambah data mahasiswa.
* **Read** → Lihat daftar mahasiswa.
* **Update** → Edit data mahasiswa.
* **Delete** → Hapus data mahasiswa.
* **Validation** → Cek agar email unik, usia minimal 17, dan semua field wajib diisi.

---
Baik! Kita tambahkan **Seeder** agar mahasiswa langsung punya data dummy untuk diuji pada project **Student Management** tadi.

---

# 🌱 **Langkah Menambahkan Data Seeder**

## 1️⃣ **Buat Seeder**

Jalankan perintah artisan:

```bash
php artisan make:seeder StudentSeeder
```

---

## 2️⃣ **Isi Seeder**

Edit file `database/seeders/StudentSeeder.php`:

```php
<?php

namespace Database\Seeders;

use Illuminate\Database\Seeder;
use App\Models\Student;

class StudentSeeder extends Seeder
{
    public function run(): void
    {
        Student::create([
            'name'  => 'Andi Saputra',
            'email' => 'andi@example.com',
            'major' => 'Informatika',
            'age'   => 20,
        ]);

        Student::create([
            'name'  => 'Budi Santoso',
            'email' => 'budi@example.com',
            'major' => 'Sistem Informasi',
            'age'   => 22,
        ]);

        Student::create([
            'name'  => 'Citra Dewi',
            'email' => 'citra@example.com',
            'major' => 'Teknik Elektro',
            'age'   => 19,
        ]);
    }
}
```

---

## 3️⃣ **Daftarkan Seeder di DatabaseSeeder**

Edit file `database/seeders/DatabaseSeeder.php`:

```php
public function run(): void
{
    $this->call(StudentSeeder::class);
}
```

---

## 4️⃣ **Jalankan Seeder**

```bash
php artisan db:seed
```

Jika ingin sekaligus reset dan seeding ulang:

```bash
php artisan migrate:fresh --seed
```

---

## ✅ **Hasil**

Setelah dijalankan, tabel `students` akan memiliki data awal:

| ID | Nama         | Email                                         | Jurusan          | Usia |
| -- | ------------ | --------------------------------------------- | ---------------- | ---- |
| 1  | Andi Saputra | [andi@example.com](mailto:andi@example.com)   | Informatika      | 20   |
| 2  | Budi Santoso | [budi@example.com](mailto:budi@example.com)   | Sistem Informasi | 22   |
| 3  | Citra Dewi   | [citra@example.com](mailto:citra@example.com) | Teknik Elektro   | 19   |

Mahasiswa dapat langsung mengakses `/students` untuk melihat data awal tanpa harus input manual.

---
