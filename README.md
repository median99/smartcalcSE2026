# README - Kalkulator SE2026-L: Margin Lapangan 2026

## 📊 Deskripsi Proyek

**Kalkulator SE2026-L** adalah alat bantu digital yang dirancang khusus untuk membantu petugas sensus dan responden dalam mengisi kuesioner **Sensus Ekonomi 2026 (SE2026-L)**. Aplikasi ini secara otomatis menghasilkan isian kuesioner berdasarkan parameter input pengguna, dengan **margin keuntungan yang telah disesuaikan dengan kondisi lapangan tahun 2026**.

## 🎯 Fitur Utama

### 1. **24 Kategori Usaha Lengkap**
- Mendukung seluruh sektor KBLI 2025 (Klasifikasi Baku Lapangan Usaha Indonesia)
- Margin disesuaikan dengan analisis ekonomi terkini:
  - Pertambangan (20-35%)
  - Industri Pengolahan (12-25%)
  - Konstruksi Besar (8-12%) - *Margin tertekan biaya material*
  - Transportasi Pribadi (8-15%) - *Dampak Perpres batas komisi maksimal 10%*
  - Telekomunikasi (35-45%) - *Kompetisi ketat*
  - Real Estat (25-40%) - *Suku bunga tinggi*
  - Dan 18 sektor lainnya...

### 2. **Skip Logic Otomatis Sesuai Kuesioner Resmi**
- **Tahun Mulai < 2026**: Menampilkan data tahunan (Rincian 26-29)
- **Tahun Mulai = 2026**: Menampilkan data bulanan (Rincian 30-33)
- **Jaringan Usaha**: Logika khusus untuk Kantor Pusat, Cabang, dan Unit Penunjang
- **Status Formal/Informal**: Menentukan keberadaan NIB dan badan usaha

### 3. **Fitur Input Upah Pekerja**
- **Mode Otomatis**: Sistem menghitung upah berdasarkan omset, UMR, dan faktor sektor
- **Mode Manual**: Pengguna dapat menginput total upah sendiri
- **Validasi UMR**: Peringatan jika upah di bawah UMR setempat
- **Preview Real-time**: Menampilkan rata-rata per orang dan total tahunan

### 4. **Input Aset Fleksibel**
- **Otomatis**: Aset dihitung berdasarkan omset dan karakteristik usaha
- **Manual**: Pengguna dapat menginput nilai tanah, aset lain, dan luas tanah
- **Konsistensi Laporan Keuangan**: Nilai aset disesuaikan dengan kepemilikan laporan keuangan

### 5. **Validasi Margin Real-time**
- Memastikan margin keuntungan sesuai rentang target sektor
- Menampilkan warning jika margin terlalu rendah/tinggi
- Margin dapat disesuaikan berdasarkan jenis tempat usaha (online, keliling, dll.)

## 🚀 Cara Menggunakan

### Langkah 1: Buka Aplikasi
Buka file `index.html` di browser modern (Chrome, Firefox, Edge, Safari).

### Langkah 2: Isi Parameter Utama
1. **Pilih KBLI/Sektor Usaha** dari dropdown (24 kategori)
2. **Isi Omset per Hari** (Rp) - rata-rata pendapatan kotor harian
3. **Isi Hari Operasi per Tahun** (default: 365)
4. **Isi Jumlah Pekerja** (termasuk pemilik)

### Langkah 3: Konfigurasi Upah (Jika Pekerja > 1)
- Pilih mode **Otomatis** atau **Manual**
- Jika Manual, isi total upah per bulan
- Sistem akan memvalidasi terhadap UMR lokasi

### Langkah 4: Atur Karakteristik Usaha
- **Tahun Mulai Beroperasi**: Kunci untuk skip logic (maksimal 2026)
- **Lokasi Usaha**: Menentukan UMR dan harga tanah
- **Status**: Formal/Informal
- **Jenis Tempat**: Mempengaruhi komposisi aset dan margin
- **Jaringan Usaha**: Tunggal, Pusat, Cabang, dll.

### Langkah 5: Generate Isian
Klik tombol **"✨ GENERATE ISIAN ✨"** untuk menghasilkan kuesioner lengkap.

## 📋 Struktur Kuesioner yang Dihasilkan

### Blok I: Keterangan Usaha/Perusahaan
- **Rincian 1-7**: Identitas wilayah (contoh: Jawa Timur, Tulungagung)
- **Rincian 8**: Nama dan alamat usaha
- **Rincian 9**: Jenis usaha & lokasi (dengan conditional R9b)
- **Rincian 10**: NIB (dengan alasan jika tidak memiliki)
- **Rincian 11**: Badan usaha & laporan keuangan
- **Rincian 12**: Penanggung jawab
- **Rincian 13**: Kegiatan utama & KBLI (dengan conditional R13i untuk akomodasi)
- **Rincian 14-15**: Jaringan usaha (conditional untuk cabang/pusat)
- **Rincian 16**: Penggunaan internet
- **Rincian 17-23**: Lingkungan, sertifikasi, kemitraan, transaksi internasional
- **Rincian 24**: Pekerja (periode berdasarkan tahun mulai)
- **Rincian 25**: Tahun mulai beroperasi

### Blok II: Data Keuangan
- **Jika Tahun Mulai < 2026**:
  - Rincian 26-27: Pengeluaran & pendapatan tahun 2025
  - Rincian 28-29: Aset & modal per 31 Desember 2025
- **Jika Tahun Mulai = 2026**:
  - Rincian 30-31: Pengeluaran & pendapatan satu bulan terakhir
  - Rincian 32-33: Aset & modal saat didirikan

### Blok III: Resume Neraca
Ringkasan lengkap kondisi keuangan usaha.

## 🔧 Teknologi yang Digunakan

- **HTML5**: Struktur halaman
- **CSS3**: Styling dengan gradient dan responsivitas
- **JavaScript (ES6+)**: Logika perhitungan dan validasi
- **Google Fonts**: Segoe UI, Roboto, Arial
- **No Framework**: Pure vanilla JavaScript

## 📱 Responsivitas

Aplikasi didesain responsif untuk:
- **Desktop** (≥1200px): Tampilan penuh dengan grid 4 kolom
- **Tablet** (768px - 1199px): Grid menyesuaikan
- **Mobile** (<768px): Grid 1-2 kolom, font menyesuaikan

## 🎨 Fitur Visual

- **Popup Awal**: Panduan singkat saat pertama membuka
- **Modal Panduan Lengkap**: Dokumentasi detail setiap input
- **Indikator Warna**:
  - 🟡 Kuning: Warning/perhatian
  - 🟢 Hijau: Margin sesuai target
  - 🔵 Biru: Informasi penting
  - 🟠 Oranye: Informasi upah/aset
- **Badge Periode**: Menunjukkan periode referensi data

## ⚠️ Catatan Penting

### Batasan dan Asumsi
1. **UMR disederhanakan** menjadi 3 kategori:
   - Kota Besar: Rp 4.500.000
   - Kabupaten: Rp 3.500.000
   - Desa: Rp 2.500.000

2. **Harga Tanah Estimasi**:
   - Kota: Rp 3.000.000/m²
   - Kabupaten: Rp 1.500.000/m²
   - Desa: Rp 500.000/m²

3. **Margin Sektor** adalah estimasi berdasarkan analisis kondisi ekonomi 2026

### Data Contoh
- Semua data wilayah (Jawa Timur, Tulungagung) adalah **contoh**
- Nama pemilik (Budi Santoso) dan NIK adalah **data dummy**
- Ganti sesuai kebutuhan lapangan

## 📚 Referensi

Aplikasi ini mengacu pada dokumen resmi:
- **Kuesioner SE2026-L** (versi terbaru)
- **KBLI 2025** (Klasifikasi Baku Lapangan Usaha Indonesia)
- **Pedoman Pencacahan SE2026**

## 🔄 Pembaruan Margin 2026

| Sektor | Margin Lama | Margin 2026 | Alasan |
|--------|-------------|-------------|---------|
| Transportasi Pribadi | 20-30% | **8-15%** | Perpres batas komisi maksimal 10% |
| Telekomunikasi | 45-55% | **35-45%** | Kompetisi ketat, margin global 35% |
| Konstruksi Besar | 15-25% | **8-12%** | Tekanan biaya material & upah |
| Real Estat | 30-50% | **25-40%** | Suku bunga tinggi |
| Keuangan | 40-60% | **30-50%** | Asuransi jiwa tertekan |

## 🤝 Kontribusi

Jika ingin berkontribusi:
1. Fork repository
2. Buat branch fitur (`git checkout -b fitur-baru`)
3. Commit perubahan (`git commit -m 'Menambah fitur baru'`)
4. Push ke branch (`git push origin fitur-baru`)
5. Buat Pull Request

## 📄 Lisensi

Proyek ini bersifat **open-source** untuk keperluan Sensus Ekonomi 2026. Silakan gunakan, modifikasi, dan distribusikan dengan tetap mencantumkan atribusi.

## 📞 Kontak

Untuk pertanyaan atau masukan terkait aplikasi ini, silakan hubungi tim pengembang melalui:
- Email: [sensus.ekonomi@bps.go.id](mailto:sensus.ekonomi@bps.go.id)
- Website: [https://sensus.bps.go.id](https://sensus.bps.go.id)

---

**Disclaimer**: Aplikasi ini adalah alat bantu tidak resmi. Data yang dihasilkan harus diverifikasi dengan kondisi lapangan sebenarnya. BPS tidak bertanggung jawab atas kesalahan input atau interpretasi.
