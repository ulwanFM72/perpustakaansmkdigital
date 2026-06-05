# 📚 Sistem Perpustakaan Sekolah — PHP Native + MySQL

Sistem manajemen perpustakaan sekolah berbasis PHP Native, MySQL, dan desain modern dark-mode.

---

## ✅ Fitur Lengkap

- 🔐 Login/Logout Admin dengan session
- 📊 Dashboard dengan statistik & grafik (Chart.js)
- 📚 Manajemen Buku (CRUD + upload cover)
- 👥 Manajemen Siswa (CRUD)
- 📖 Sistem Peminjaman (validasi stok, batas pinjam)
- 🔄 Sistem Pengembalian (denda otomatis Rp 1.000/hari)
- 📋 Riwayat lengkap + filter + print
- 🛡️ Aman dari SQL Injection (PDO Prepared Statement)
- 📱 Responsive mobile-friendly

---

## 🗂️ Struktur Folder

```
perpustakaan/
├── config/
│   ├── database.php       ← Koneksi PDO & helper functions
│   └── auth.php           ← Session, login guard, sanitize
├── controllers/
│   ├── books.php          ← CRUD buku
│   ├── students.php       ← CRUD siswa
│   ├── loans.php          ← Proses peminjaman
│   ├── returns.php        ← Proses pengembalian
│   └── logout.php         ← Logout
├── views/
│   ├── layout/
│   │   ├── header.php     ← Sidebar, navbar, CSS global
│   │   └── footer.php     ← Script JS global
│   ├── dashboard/
│   │   └── index.php      ← Halaman dashboard
│   ├── books/
│   │   └── index.php      ← Manajemen buku
│   ├── students/
│   │   └── index.php      ← Manajemen siswa
│   ├── loans/
│   │   └── index.php      ← Peminjaman
│   ├── returns/
│   │   └── index.php      ← Pengembalian
│   └── history/
│       └── index.php      ← Riwayat
├── uploads/
│   └── covers/            ← Folder upload cover buku
├── database.sql           ← File SQL database
└── index.php              ← Halaman login
```

---

## ⚙️ Konfigurasi Denda

Buka `config/database.php`, ubah nilai ini:
```php
define('DENDA_PER_HARI', 1000);   // Rp 1.000 per hari terlambat
```

Atau ubah lewat tabel `pengaturan` di database:
```sql
UPDATE pengaturan SET denda_per_hari=2000, maks_pinjam=3, maks_hari=7;
```

---

## 🗄️ Struktur Database

| Tabel        | Keterangan                          |
|-------------|-------------------------------------|
| `admin`      | Data admin login                    |
| `buku`       | Koleksi buku perpustakaan           |
| `siswa`      | Data siswa                          |
| `peminjaman` | Transaksi peminjaman & pengembalian |
| `pengaturan` | Konfigurasi sistem                  |

---

## 🔒 Keamanan

- **PDO Prepared Statement** → aman dari SQL Injection
- **password_hash()** → password admin di-hash dengan bcrypt
- **Session guard** → semua halaman admin dilindungi session
- **Sanitize input** → semua input di-strip dan di-escape
- **.htaccess** di folder uploads → mencegah eksekusi PHP di folder upload

---

## 📦 Teknologi

| Teknologi | Versi |
|-----------|-------|
| PHP | 7.4+ / 8.x |
| MySQL | 5.7+ / 8.x |
| XAMPP | Terbaru |
| Font Awesome | 6.5 |
| Chart.js | 4.x |
| SweetAlert2 | 11 |
| Google Fonts (Sora) | — |

---

## ❓ Troubleshooting

**Halaman tidak ditemukan (404)**  
→ Pastikan nama folder sudah `perpustakaan` dan Apache sudah aktif.

**Error koneksi database**  
→ Pastikan MySQL aktif di XAMPP dan database sudah diimport.

**Upload cover tidak berfungsi**  
→ Pastikan folder `uploads/covers/` ada dan memiliki permission write (777).

**Login gagal**  
→ Pastikan database sudah diimport dan tabel `admin` berisi data default.

---

Dibuat dengan ❤️ untuk tugas perpustakaan sekolah.
# perpustakaansmkdigital
