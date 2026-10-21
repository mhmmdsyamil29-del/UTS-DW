# Portal Akademik Universitas ABC

Aplikasi web portal akademik sederhana untuk mahasiswa Universitas ABC. Dibuat sebagai tugas mata kuliah **Desain Web** oleh **Kelompok 12**.

---

## Deskripsi

Portal ini memungkinkan mahasiswa untuk:
- Melihat jadwal perkuliahan per hari dan per semester
- Melakukan presensi kehadiran secara otomatis (hanya bisa saat jam kuliah berlangsung)
- Melihat rekap kehadiran per mata kuliah
- Mengakses informasi kontak, lokasi kampus, dan profil pembuat

Aplikasi ini **murni front-end** (HTML + CSS + JavaScript) tanpa backend, menggunakan `localStorage` dan `sessionStorage` untuk menyimpan data sementara di browser.

---

## Fitur

| Fitur | Deskripsi |
|-------|-----------|
| 🔐 **Login** | Autentikasi sederhana (demo) dengan session `sessionStorage` |
| 📅 **Jadwal Kuliah** | Tampilan jadwal per hari (Senin–Minggu) & per semester |
| ✅ **Presensi Otomatis** | Tombol presensi aktif hanya jika hari & jam kuliah sesuai |
| 📊 **Rekap Absensi** | Ringkasan jumlah hadir per mata kuliah |
| 🗑️ **Reset Data** | Hapus semua data absensi dari `localStorage` |
| 📱 **Responsif** | Tabel dapat di-scroll horizontal pada layar kecil |

---

## Struktur Proyek
📦 portal-akademik
```
├── css/
│   └── style.css     # Styling global (Sidebar, tabel, card, dll)
├── index.html        # Dasbor utama (login + jadwal + presensi)
├── beranda.html      # Halaman sambutan & pengumuman
├── jadwal.html       # Daftar jadwal kuliah (read-only)
├── absensi.html      # Rekap kehadiran mahasiswa
├── kontak.html       # Informasi kontak kampus
├── lokasi.html       # Alamat & peta kampus
├── tentang.html      # Profil pembuat aplikasi
└── README.md         # Dokumentasi ini
```
---

## Cara Menjalankan

1. **Clone / unduh** semua file ke satu folder.
2. Buka `index.html` di browser (Chrome, Firefox, Edge, dll).
3. Login dengan kredensial demo:

   | Field | Value |
   |-------|-------|
   | Username | `admin` |
   | Password | `12345` |

4. Setelah login, Anda akan diarahkan ke dasbor jadwal kuliah.
5. Klik tab hari untuk melihat jadwal, dan klik **Presensi** pada mata kuliah yang sedang berlangsung.

>  Tidak perlu server lokal — cukup buka file HTML langsung di browser.

---

## Akun Demo
### Username : admin
### Password : 12345
---

> **Catatan:** Kredensial ini *hardcoded* di JavaScript dan hanya untuk keperluan demo. **Jangan digunakan di produksi.**

---

## Teknologi

- **HTML5** — Struktur halaman
- **CSS3** — Styling (layout flexbox, tema warna ungu)
- **Vanilla JavaScript** — Logika jadwal, presensi, dan login
- **Web Storage API** — `localStorage` & `sessionStorage` untuk persistensi data

---

## Cara Kerja Presensi

1. Data jadwal disimpan dalam objek `masterDataJadwal` (per semester & hari).
2. Saat halaman dimuat, sistem mengecek:
   - **Hari ini** harus sama dengan hari pada jadwal.
   - **Waktu sekarang** harus berada di antara jam mulai & selesai kuliah.
3. Jika kedua syarat terpenuhi → tombol **Presensi** aktif.
4. Setelah diklik, data kehadiran disimpan ke `localStorage` dengan     
key: absensiData_<semester>
Contoh: `absensiData_Ganjil 2026/2027`

5. Tombol berubah menjadi **"Hadir ✔"** dan tidak bisa diklik lagi.

---

## 📊 Format Data `localStorage`

```json
{
"absensiData_Ganjil 2026/2027": {
 "Komunikasi Data": { "hadir": 3 },
 "Basis Data": { "hadir": 1 }
}
}
