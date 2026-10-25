# Sistem Manajemen Perpustakaan Kampus
 
Aplikasi berbasis konsol (CLI) yang dibuat dengan Java untuk mengelola koleksi buku perpustakaan kampus. Aplikasi ini memungkinkan pengelolaan data buku, pencarian lokasi buku di rak, antrean mahasiswa, pencatatan transaksi peminjaman, pembatalan transaksi, serta statistik peminjaman per kategori dan per hari. Program dibangun dengan pola **MVC** (Model-View-Controller) dan menerapkan konsep Pemrograman Berorientasi Objek.
 
## Tugas Pemrograman Java
- **Mata Kuliah:** Pemrograman Berorientasi Objek
- **Dosen Pengampu:** M. Ibadurrahman Arrasyid Supriyanto M.Kom.
- **Program Studi:** Sistem Informasi
- **Angkatan:** 2025
- **Kelompok:** 22
## Anggota Kelompok 22
 
1. *Ghea Aisyah Windraswari* - 2509116022 - Kelas A
2. *Noor Hamsyah Pratama* - 2509116046 - Kelas B
3. *Condrado Alain Sharon* - 2509116069 - Kelas B
4. *Nurul Shafa Azizah* - 2509116112 - Kelas C
## Struktur File Proyek
 
```
PerpustakaanKampus/
└── src/
    ├── main/
    │   └── Main.java                    # Titik masuk program
    ├── view/
    │   └── MenuView.java                # Tampilan menu & input pengguna
    ├── controller/
    │   └── PerpustakaanController.java  # Logika bisnis & pengelolaan data
    └── model/
        ├── DapatDipinjam.java           # Interface (cek, pinjam, kembalikan)
        ├── Pengguna.java                # Abstract class pengguna
        ├── Mahasiswa.java               # Turunan Pengguna
        ├── Buku.java                    # Implementasi DapatDipinjam
        └── Transaksi.java               # Data transaksi peminjaman
```
 
| Package | Class | Peran |
|---|---|---|
| `main` | `Main` | Menjalankan `MenuView` |
| `view` | `MenuView` | Menampilkan menu, membaca input, memanggil controller |
| `controller` | `PerpustakaanController` | Mengelola buku, antrean, transaksi, statistik, dan lokasi rak |
| `model` | `DapatDipinjam` | Interface kontrak peminjaman buku |
| `model` | `Pengguna` | Abstract class dengan atribut `id` dan `nama` |
| `model` | `Mahasiswa` | Turunan `Pengguna`, meng-override `tampilkanPeran()` |
| `model` | `Buku` | Data buku dan logika stok |
| `model` | `Transaksi` | Mencatat mahasiswa, buku, dan waktu peminjaman |
 
## Fitur Utama
 
| No | Menu | Deskripsi |
|---|---|---|
| 1 | Tampilkan kategori buku | Menampilkan 4 kategori: Pemrograman, Matematika, Jaringan Komputer, Basis Data |
| 2 | Tampilkan daftar buku | Menampilkan judul, kategori, dan stok seluruh buku |
| 3 | Cari lokasi buku | Menampilkan lantai, rak, dan posisi buku berdasarkan judul |
| 4 | Tampilkan statistik peminjaman | Tabel jumlah peminjaman per kategori untuk setiap hari (Senin-Minggu) |
| 5 | Tambah buku | Menambah buku baru dengan validasi ID dan judul unik, serta alokasi rak otomatis |
| 6 | Hapus buku | Menghapus buku (ditolak jika stok kosong atau sudah punya riwayat transaksi) |
| 7 | Tambah mahasiswa ke antrean | Memasukkan mahasiswa ke antrean (tanpa duplikasi ID) |
| 8 | Tampilkan antrean mahasiswa | Menampilkan urutan antrean saat ini |
| 9 | Layani antrean dan pinjam buku | Mengambil mahasiswa terdepan dan memproses peminjaman buku |
| 10 | Tampilkan transaksi terakhir | Menampilkan detail transaksi paling baru |
| 11 | Batalkan transaksi terakhir | Membatalkan transaksi terakhir, mengembalikan stok, dan mengurangi statistik |
| 0 | Keluar | Mengakhiri program |
 
## Konsep Pemrograman yang Diterapkan
 
**Struktur Data**
- **Array 1 dimensi** (`String[]`) untuk daftar kategori buku dan nama hari.
- **Array 2 dimensi** (`int[4][7]`) untuk statistik peminjaman (kategori x hari).
- **Array 3 dimensi** (`String[2][3][4]`) untuk lokasi buku (lantai x rak x posisi).
- **ArrayList** untuk menyimpan koleksi buku.
- **Stack** untuk riwayat transaksi (transaksi terakhir dapat dibatalkan, prinsip LIFO).
- **Queue (LinkedList)** untuk antrean mahasiswa (prinsip FIFO).
**Pemrograman Berorientasi Objek**
- **Encapsulation:** atribut `private` dengan getter.
- **Inheritance:** `Mahasiswa` mewarisi `Pengguna`.
- **Abstraction:** `Pengguna` (abstract class) dan `DapatDipinjam` (interface).
- **Polymorphism:** method `tampilkanPeran()` dan implementasi method interface dengan `@Override`.
