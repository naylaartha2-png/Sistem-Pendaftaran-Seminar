# Sistem Pendaftaran Seminar – Simulasi Bug & Fix

Aplikasi web satu halaman untuk mendemonstrasikan **Software Maintenance** (Corrective Maintenance) pada Sistem Pendaftaran Seminar. Halaman membandingkan versi **BUG** (sebelum perbaikan) dan versi **FIX** (sesudah perbaikan) secara berdampingan.

Proyek Mata Kuliah Rekayasa Perangkat Lunak – **Kelompok 6**.

## Fitur

- Input nama peserta seminar (kuota maksimal 5 peserta).
- Tombol **Jalankan BUG**: menerima semua input tanpa validasi.
- Tombol **Jalankan FIX**: menerapkan validasi sebelum menerima peserta.
- Tombol **Reset**: mengembalikan data awal (Andi, Budi, Citra, Dewi).
- Perbandingan jumlah peserta, status, pesan, dan daftar peserta antara versi BUG dan FIX.
- Perbandingan kode sebelum dan sesudah perbaikan.

## Bug yang Diperbaiki

| No | Bug | Penyebab | Perbaikan |
|----|-----|----------|-----------|
| 1 | Nama tidak valid (kosong, hanya spasi, mengandung angka/simbol) tetap terdaftar | Isian nama tidak divalidasi | Cek nama tidak kosong dan hanya berisi huruf dengan `regex` |
| 2 | Nama ganda tetap diterima | Tidak ada pemeriksaan nama yang sudah terdaftar | Cek dengan `some()` (tidak peduli huruf besar/kecil) |
| 3 | Peserta ke-6 dan seterusnya tetap diterima | Jumlah peserta tidak dibandingkan dengan kuota | Cek `peserta.length >= KUOTA` |

## Prasyarat

- Browser modern (Chrome, Edge, Firefox, atau Safari).
- Tidak perlu instalasi library, `npm`, maupun koneksi internet.
- Opsional: [VS Code](https://code.visualstudio.com/) dengan ekstensi Live Server, atau Python 3.

## Instalasi

```bash
git clone https://github.com/naylaartha2-png/Sistem-Pendaftaran-Seminar
cd Sistem-Pendaftaran-Seminar
```

Atau unduh melalui **Code → Download ZIP** di halaman repository, lalu ekstrak.

## Cara Menggunakan

Pilih salah satu cara menjalankan:

1. **Langsung:** klik dua kali `index.html` sehingga terbuka di browser.
2. **VS Code:** buka folder proyek, klik kanan `index.html`, pilih **Open with Live Server**.
3. **Python:**
   ```bash
   python -m http.server 8000
   ```
   lalu buka `http://localhost:8000`.

Langkah pemakaian:

1. Ketik nama peserta pada kolom **Nama peserta**.
2. Klik **Jalankan BUG** untuk melihat perilaku sebelum perbaikan.
3. Klik **Jalankan FIX** untuk melihat perilaku sesudah perbaikan.
4. Bandingkan hasil kedua kotak. Klik **Reset** untuk mengulang.

## Pengujian

Aplikasi ini berupa satu file HTML tanpa unit test otomatis, sehingga pengujian dilakukan secara manual. Klik **Reset** sebelum tiap kasus (kecuali kasus 5 dan 6).

| No | Input | Expected (FIX) | Actual BUG |
|----|-------|----------------|------------|
| 1 | *(kosong)* | Ditolak: "Nama tidak boleh kosong." | Diterima |
| 2 | `sit1` | Ditolak: nama tidak valid | Diterima |
| 3 | `andi` | Ditolak: "Nama sudah terdaftar." | Diterima |
| 4 | `Eko` | Diterima (peserta menjadi 5/5) | Diterima |
| 5 | `Fajar` setelah kuota penuh | Ditolak: kuota penuh | Diterima (6/5) |
| 6 | `Eko` lagi setelah kuota penuh | Ditolak: kuota penuh | Diterima |

Hasil: versi FIX menolak semua kasus tidak valid dan jumlah peserta tidak bertambah.

## Struktur Folder

```
.
├── index.html        # aplikasi (HTML, CSS, JavaScript)
├── README.md         # dokumentasi proyek
├── CHANGELOG.md      # riwayat perubahan

```

## Anggota Kelompok 6

| Nama | NIM |
|------|-----|
| Nayla Artha Mevia Suma | F5212510009 |
| Adelia Mutmaina  | F5212510012 |
| Ingel Laura Lamula | F5212510015 |
| Stevalia Bindi Rahmania  | F5212520040 |

## Riwayat Perubahan

Lihat [CHANGELOG.md](CHANGELOG.md).
