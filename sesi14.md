# 📚 **Materi Perkuliahan: Implementasi Project Laravel**

## 🎯 **Tujuan Pembelajaran**

Setelah mengikuti materi ini, mahasiswa diharapkan dapat:

1. Mengimplementasikan project berbasis Laravel dari awal hingga selesai.
2. Merancang **fitur-fitur** project sesuai kebutuhan aplikasi.
3. Membuat **laporan project** yang profesional dan mudah dipahami.

---

## 1️⃣ **Tahapan Implementasi Project**

### **A. Analisis Kebutuhan**

* Tentukan jenis aplikasi (misalnya: sistem manajemen mahasiswa, sistem inventori, blog, toko online).
* Identifikasi fitur utama (misalnya: CRUD data, autentikasi user, laporan PDF).
* Gambar **diagram alur (flowchart)** atau **use case**.

---

### **B. Setup Project**

1. Install Laravel dan konfigurasi database.
2. Buat migration, model, controller, dan route.
3. Buat desain antarmuka (View) menggunakan Blade Template.
4. Tambahkan validasi form agar input data sesuai standar.

---

### **C. Pengembangan Fitur**

Berikut contoh daftar fitur umum pada project Laravel sederhana:

| Fitur               | Deskripsi                             | Implementasi                                             |
| ------------------- | ------------------------------------- | -------------------------------------------------------- |
| **Autentikasi**     | Login & register pengguna             | `php artisan make:auth` (Jetstream / Breeze)             |
| **CRUD Data**       | Tambah, lihat, ubah, hapus data utama | `Route::resource()` + Controller                         |
| **Form Validation** | Validasi input sebelum disimpan       | `$request->validate([...])`                              |
| **Search & Filter** | Mencari data berdasarkan kata kunci   | Query Eloquent `->where()`                               |
| **Pagination**      | Membagi data menjadi halaman          | `Product::paginate(10)`                                  |
| **Relasi Data**     | Menghubungkan antar tabel             | Eloquent Relationships (`hasMany`, `belongsTo`)          |
| **Upload File**     | Menyimpan gambar/file                 | `Storage::put()` atau `$request->file('image')->store()` |
| **Laporan**         | Export data ke PDF/Excel              | `barryvdh/laravel-dompdf` atau `maatwebsite/excel`       |

---

### **D. Testing**

* Uji semua fitur (manual testing).
* Periksa validasi, CRUD, relasi antar data.
* Pastikan tidak ada error di console browser & log Laravel.

---

## 2️⃣ **Laporan Project**

Laporan digunakan untuk mendokumentasikan hasil pekerjaan.
Berikut **format laporan project Laravel** yang disarankan:

---

### 📑 **Format Laporan Project**

#### **1. Halaman Judul**

* Judul Project
* Nama Kelompok / Mahasiswa
* NIM
* Mata Kuliah
* Nama Dosen
* Tahun Ajaran

---

#### **2. Daftar Isi**

* Otomatis dari Word / Google Docs

---

#### **3. Bab I: Pendahuluan**

* **Latar Belakang**
  Menjelaskan mengapa aplikasi ini dibuat, permasalahan yang dipecahkan.
* **Tujuan**
  Tujuan project secara umum dan khusus.
* **Manfaat**
  Manfaat aplikasi bagi pengguna.

---

#### **4. Bab II: Analisis Sistem**

* **Analisis Kebutuhan** (Fitur utama)
* **Use Case Diagram** atau **Flowchart**
* **Desain Database** (ERD)

---

#### **5. Bab III: Implementasi Sistem**

* **Struktur Folder Project**
* **Penjelasan Fitur** (CRUD, Validasi, Upload File, dsb.)
* **Potongan Kode** (Controller, Route, View)
* **Screenshot Tampilan** (Halaman List, Tambah, Edit, Hapus)

---

#### **6. Bab IV: Pengujian**

* **Skenario Pengujian**
  Contoh tabel pengujian:

| No | Fitur       | Skenario            | Input        | Output yang Diharapkan     | Hasil |
| -- | ----------- | ------------------- | ------------ | -------------------------- | ----- |
| 1  | Tambah Data | Mengisi form produk | Nama: Laptop | Data tersimpan di database | ✅     |

---

#### **7. Bab V: Kesimpulan & Saran**

* Kesimpulan hasil project.
* Saran pengembangan di masa depan (misalnya: tambah autentikasi, role user).

---

#### **8. Daftar Pustaka**

* Dokumentasi Laravel.
* Buku / artikel pendukung.

---

### ✅ **Tips Laporan**

* Gunakan screenshot yang jelas (tampilan browser).
* Sertakan potongan kode penting.
* Buat laporan rapi dengan heading yang konsisten.
* Tambahkan **flowchart** dan **ERD** untuk memperjelas desain sistem.

---
