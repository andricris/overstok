# SCM Dropping Optimizer

Aplikasi berbasis web (tanpa backend) untuk membantu proses optimasi dropping/redistribusi stok berdasarkan data Excel. Antarmuka dibuat dengan React + Tailwind, berjalan langsung di browser (cukup buka file HTML). Fungsionalitas utama: membaca file Excel, memetakan kolom penting, menghitung overstock, serta memberikan rekomendasi alokasi pengiriman berdasarkan rayon dan skala prioritas.

## Fitur Utama

- **Impor Excel langsung di browser** menggunakan SheetJS.
- **Rayonisasi otomatis** berdasarkan kode cabang dan **prioritas distribusi** per rayon.
- **Pemetaan kolom fleksibel** (kolom cabang, kode produk, deskripsi, plan drop, overstock, multiple, dll).
- **Kalkulator overstock** berdasarkan kolom stock, sales, dan buffer/PO pending.
- **Filter & pencarian** untuk memudahkan review hasil rekomendasi.
- **Tampilan ringkas** untuk mempercepat workflow analisis.

## Struktur File

- `index.html` — **Versi utama** aplikasi SCM Dropping Optimizer (UI modern dengan Tailwind + lucide icons).
- `komplit.html` — **Versi alternatif/komplit** dengan tampilan dan komponen yang lebih klasik.
- `maintenance.html` — Halaman “Under Maintenance”.
- `under-maintenance.png` — Asset gambar untuk halaman maintenance.

## Cara Menjalankan

Karena aplikasi berjalan sepenuhnya di browser, tidak ada proses build atau server.

1. **Buka file HTML** langsung di browser (Chrome/Edge/Firefox).
   - Versi utama: `index.html`
   - Versi alternatif: `komplit.html`
2. **Unggah file Excel** melalui tombol upload di halaman.
3. **Pilih sheet** dan **baris header** yang sesuai.
4. **Sesuaikan mapping kolom** jika struktur Excel berbeda.
5. Jalankan proses analisis untuk mendapatkan rekomendasi alokasi.

> Catatan: Karena aplikasi menggunakan `FileReader` dan pustaka eksternal dari CDN, pastikan koneksi internet tersedia saat pertama kali membuka file.

## Konsep Data & Konfigurasi

### 1) Rayonisasi
Kode cabang dipetakan ke rayon (misalnya JABODUNGTABEK, JAWA TENGAH, JAWA TIMUR, SUMATERA, CABANG JAUH). Mapping ini terdapat di dalam file HTML.

### 2) Skala Prioritas
Setiap rayon tujuan memiliki urutan prioritas sumber pengiriman (misalnya JABODUNGTABEK memprioritaskan JABODUNGTABEK → JAWA TENGAH → JAWA TIMUR → SUMATERA → CABANG JAUH).

### 3) Mapping Kolom (Default)
Default mapping pada versi utama `index.html`:

- **Branch**: `A`
- **Product Code**: `E`
- **Product Description**: `F`
- **Plan Drop**: `AY`
- **Overstock**: `AZ`
- **Multiple**: `AP`

### 4) Konfigurasi Kalkulator Overstock (Default)
- **Stock**: `AA`
- **Sales Qty**: `V`
- **Buffer / PO Pending**: `AL`

> Semua mapping ini dapat diubah melalui UI agar sesuai dengan layout Excel yang berbeda.

## Teknologi

- **React 18** (UMD) + **ReactDOM**
- **Tailwind CSS** (CDN)
- **Babel Standalone** (agar JSX berjalan langsung di browser)
- **SheetJS** untuk membaca file Excel
- **Lucide Icons** (khusus di `index.html`)

## Tips Penggunaan

- Pastikan file Excel memiliki header yang jelas dan konsisten.
- Cek kembali mapping kolom jika hasil tampak tidak sesuai.
- Gunakan filter dan pencarian untuk memfokuskan produk atau cabang tertentu.

## Lisensi

Belum ditentukan. Silakan tambahkan lisensi sesuai kebutuhan proyek.
