# 📚 Jurnal Mengajar Digital

Aplikasi pencatatan jurnal mengajar digital berbasis **Google Apps Script** untuk guru SMP Al-Irsyad Bogor. Diakses melalui **GitHub Pages** sebagai wrapper iframe.

---

## 🔗 Akses Aplikasi

> **[Klik di sini untuk membuka aplikasi](https://[USERNAME-GITHUB].github.io/[NAMA-REPO]/)**

---

## ✨ Fitur Utama

| Fitur | Deskripsi |
|---|---|
| 🔐 Login | Autentikasi berbasis role (Admin / Guru / Wali Kelas) |
| 🤖 Generator AI | Buat CP, TP, ATP, RPP & Soal dengan Google Gemini AI |
| 📁 Arsip Perangkat Ajar | Simpan & kelola hasil generate AI |
| 📅 Jadwal Mengajar | Kelola jadwal harian dengan deteksi konflik otomatis |
| 📖 Jurnal Mengajar | Catat kegiatan pembelajaran harian |
| ✅ Kehadiran Siswa | Presensi siswa per sesi + rekap kehadiran |
| ⭐ Input Nilai | Nilai harian, tugas, PTS, PAS + import massal |
| 📊 Laporan | Rekap kehadiran, nilai, sikap, & akhir tahun |
| 🗄️ Data Master | Kelola siswa, kelas, dan akun guru |
| 📆 Tahun Ajaran | Manajemen multi-tahun dengan arsip otomatis |

---

## 🏗️ Arsitektur

```
GitHub Pages (docs/index.html)
        │
        │  iframe
        ▼
Google Apps Script Web App
        │
        │  Spreadsheet API
        ▼
Google Sheets (Master Data + Operasional)
```

### Struktur File

```
📁 JURNAL-MENGAJAR/
├── 📁 docs/
│   └── index.html          ← GitHub Pages wrapper (iframe loader)
│
├── 🔧 Backend (upload ke GAS Editor)
│   ├── appsscript.json
│   ├── Code.gs             ← Entry point & routing
│   ├── Utils.gs            ← Helper & inisialisasi DB
│   ├── Auth.gs             ← Login & session
│   ├── MasterService.gs    ← CRUD siswa, kelas, guru
│   ├── JadwalService.gs    ← CRUD jadwal
│   ├── JurnalService.gs    ← CRUD jurnal
│   ├── KehadiranService.gs ← CRUD kehadiran
│   ├── NilaiService.gs     ← CRUD nilai
│   ├── ArsipService.gs     ← CRUD arsip AI
│   ├── LaporanService.gs   ← Laporan & statistik
│   ├── AIService.gs        ← Integrasi Gemini API
│   └── ArchiveService.gs   ← Tutup tahun ajaran
│
└── 🎨 Frontend (upload ke GAS Editor sebagai HTML file)
    ├── Index.html          ← SPA utama (GAS template)
    ├── Stylesheet.html     ← Semua CSS
    └── JavaScript.html     ← Semua logika JS client-side
```

---

## 🚀 Cara Setup

Lihat **[Panduan Setup Lengkap](SETUP.md)** untuk langkah-langkah detail.

### Ringkasan Cepat:
1. Buat 2 Google Spreadsheet di Google Drive sekolah
2. Buat project baru di [script.google.com](https://script.google.com)
3. Upload semua file `.gs` dan `.html` ke GAS Editor
4. Isi ID Spreadsheet & Gemini API Key di `Utils.gs`
5. Jalankan `inisialisasiDatabase()` sekali
6. Deploy sebagai Web App → salin URL `/exec`
7. Paste URL ke `docs/index.html` pada bagian `src` iframe
8. Push ke GitHub → aktifkan GitHub Pages dari folder `docs/`

---

## ⚙️ Konfigurasi

Edit bagian `CONFIG` di file `Utils.gs`:

```javascript
const CONFIG = {
  MASTER_SPREADSHEET_ID:      'ID_SPREADSHEET_MASTER',
  OPERASIONAL_SPREADSHEET_ID: 'ID_SPREADSHEET_OPERASIONAL',
  AI_API_KEY:                 'GEMINI_API_KEY',
  SEKOLAH_NAMA:               'edit di halaman profil sekolah',
};
```

---

## 👤 Akun Default (Saat Pertama Kali)

| Username | Password | Role |
|---|---|---|
| `admin` | `admin123` | Admin |

> ⚠️ **Segera ganti password setelah login pertama!**

---

## 🛡️ Keamanan Data

- Password di-hash dengan algoritma **SHA-256**
- Akses data dibatasi berdasarkan **role** (Admin / Guru / Wali Kelas)
- Data tidak pernah dihapus permanen (**soft delete**)
- Edit jurnal dibatasi **24 jam** setelah dibuat
- Data kehadiran **tidak bisa dihapus**, hanya bisa dikoreksi

---

## 📋 Teknologi

- **Backend**: Google Apps Script (V8 Runtime)
- **Database**: Google Sheets (2 Spreadsheet)
- **AI**: Google Gemini API (`gemini-1.5-flash`)
- **Frontend**: Vanilla HTML, CSS, JavaScript
- **Hosting**: GitHub Pages (wrapper) + GAS Web App

---

## 📝 Lisensi

Dikembangkan khusus untuk **Pendidikan**.

---

*Dibuat dengan ❤️ untuk kemajuan pendidikan*
