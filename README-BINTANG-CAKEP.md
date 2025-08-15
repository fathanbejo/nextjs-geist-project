# 🌟 Aplikasi Bintang CAKEP
## MI Almaarif 02 Singosari

Aplikasi Gamifikasi Program Apresiasi Karakter Bulanan untuk membangun generasi yang **Cendekia**, **Akrab**, **Kreatif**, **Elegan**, dan **Progresif**.

---

## 📋 Deskripsi Aplikasi

Bintang CAKEP adalah aplikasi web modern yang dirancang untuk mendukung program apresiasi karakter bulanan di MI Almaarif 02 Singosari. Aplikasi ini menggunakan sistem gamifikasi untuk memotivasi siswa dalam mengembangkan karakter positif melalui 5 nilai utama CAKEP.

### 🎯 Tujuan Aplikasi
- Memudahkan guru dalam mencatat dan mengapresiasi kebaikan siswa
- Membuat progres karakter siswa menjadi transparan dan terlihat
- Memberikan platform bagi siswa untuk saling mengapresiasi
- Menyediakan data akurat untuk evaluasi program
- Memperkuat branding madrasah sebagai lembaga pendidikan inovatif

---

## 👥 Role Pengguna

### 1. 👨‍💼 Administrator (Kepala Madrasah)
**Fitur Utama:**
- Dashboard statistik sekolah
- Manajemen pengguna (siswa, guru, orang tua)
- Manajemen kelas
- Generate SK "Bintang CAKEP" bulanan
- Rekapitulasi poin dan lencana semua kelas

### 2. 👩‍🏫 Guru (Wali Kelas & Guru Mapel)
**Fitur Utama:**
- Dashboard "Peta Bintang Kelas" (leaderboard)
- Memberikan Poin Karakter (PK) dan Lencana Misi
- Validasi nominasi kebaikan dari siswa
- Melihat profil detail dan progres siswa
- Menulis catatan perilaku positif

### 3. 👨‍🎓 Siswa
**Fitur Utama:**
- Profil pribadi dengan total PK dan lencana
- Melihat "Peta Bintang Kelas"
- Mengajukan nominasi kebaikan untuk teman ("Misi Mata Bintang")
- Riwayat pencapaian dan progress level

### 4. 👨‍👩‍👧‍👦 Orang Tua
**Fitur Utama:**
- Melihat profil dan progres karakter anak (view-only)
- Analisis karakter anak
- Riwayat aktivitas real-time
- Tips untuk mendukung karakter anak di rumah

---

## 🏆 Sistem CAKEP

### Kriteria Karakter:

1. **🧠 Cendekia** - Kecerdasan & Pengetahuan
   - Aktif bertanya dan menjawab
   - Prestasi akademik
   - Rasa ingin tahu tinggi

2. **🤝 Akrab** - Keramahan & Kerjasama
   - Membantu teman
   - Kerjasama yang baik
   - Sikap ramah dan peduli

3. **🎨 Kreatif** - Kreativitas & Inovasi
   - Ide-ide baru yang positif
   - Karya seni yang bagus
   - Solusi kreatif untuk masalah

4. **👔 Elegan** - Kesopanan & Etika
   - Berpakaian rapi
   - Berbicara santun
   - Etika yang baik

5. **📈 Progresif** - Kemajuan & Perkembangan
   - Usaha yang konsisten
   - Peningkatan prestasi
   - Semangat belajar tinggi

---

## 🚀 Teknologi yang Digunakan

### Frontend
- **Next.js 15+** - React framework dengan App Router
- **TypeScript** - Type-safe development
- **Tailwind CSS** - Utility-first CSS framework
- **shadcn/ui** - Modern UI component library
- **Radix UI** - Accessibility-first primitives

### State Management
- **React Context** - Authentication dan state global
- **React Hooks** - Local state management

### Styling & UI
- **Google Fonts (Inter)** - Modern typography
- **Responsive Design** - Mobile-first approach
- **Dark/Light Mode Ready** - Theme support
- **Clean Design** - No external icons, focus on typography

---

## 📦 Instalasi & Menjalankan Aplikasi

### Prerequisites
- Node.js 18+
- npm / yarn / pnpm / bun

### Langkah Instalasi

1. **Clone Repository**
   ```bash
   git clone [repository-url]
   cd bintang-cakep-app
   ```

2. **Install Dependencies**
   ```bash
   npm install
   ```

3. **Jalankan Development Server**
   ```bash
   npm run dev
   ```

4. **Akses Aplikasi**
   - Buka browser: `http://localhost:8000`

### Build untuk Production
```bash
npm run build
npm start
```

---

## 🔐 Akun Demo

Untuk testing aplikasi, gunakan akun demo berikut:

| Username | Password | Role | Deskripsi |
|----------|----------|------|-----------|
| `admin` | `password` | Administrator | Kepala Madrasah |
| `guru1` | `password` | Guru | Bu Siti Aminah - Kelas IV-A |
| `guru2` | `password` | Guru | Pak Ahmad Fauzi - Kelas IV-B |
| `siswa1` | `password` | Siswa | Ahmad Rizki - Kelas IV-A |
| `siswa2` | `password` | Siswa | Siti Fatimah - Kelas IV-A |
| `ortu1` | `password` | Orang Tua | Bapak Rizki (Orang tua Ahmad) |
| `ortu2` | `password` | Orang Tua | Ibu Fatimah (Orang tua Siti) |

---

## 🎮 Cara Menggunakan Aplikasi

### Untuk Guru:
1. Login dengan akun guru
2. Pilih tab "Berikan Poin" untuk memberikan poin karakter
3. Pilih siswa, kriteria CAKEP, jumlah poin (1-100), dan catatan
4. Validasi nominasi dari siswa di tab "Validasi Nominasi"

### Untuk Siswa:
1. Login dengan akun siswa
2. Lihat profil dan koleksi lencana di tab "Profil Saya"
3. Nominasikan teman di tab "Nominasi Teman"
4. Pantau ranking di "Peta Bintang"

### Untuk Admin:
1. Login dengan akun admin
2. Kelola pengguna dan kelas
3. Generate SK bulanan
4. Monitor statistik sekolah

### Untuk Orang Tua:
1. Login dengan akun orang tua
2. Pantau progres karakter anak
3. Lihat analisis karakter dan tips

---

## 📊 Fitur Utama

### 🏅 Sistem Poin & Level
- Setiap kriteria CAKEP memiliki poin 1-100
- Level misi naik setiap 250 poin
- Progress bar menunjukkan kemajuan ke level berikutnya

### 🏆 Sistem Lencana
- 5 jenis lencana sesuai kriteria CAKEP
- Lencana diberikan berdasarkan pencapaian tertentu
- Koleksi lencana ditampilkan di profil siswa

### 👁️ Misi Mata Bintang
- Siswa dapat menominasikan teman
- Nominasi harus divalidasi guru
- Nominasi yang disetujui memberikan poin tambahan

### 📈 Leaderboard Real-time
- Ranking siswa berdasarkan total poin
- Update otomatis saat ada perubahan poin
- Tampilan medali untuk 3 besar

### 📱 Responsive Design
- Optimal di desktop, tablet, dan mobile
- Interface yang user-friendly
- Loading states dan feedback yang jelas

---

## 🔧 Struktur Proyek

```
src/
├── app/                    # Next.js App Router
│   ├── globals.css        # Global styles
│   ├── layout.tsx         # Root layout
│   └── page.tsx           # Main page
├── components/            # React components
│   ├── ui/               # shadcn/ui components
│   ├── DashboardAdmin.tsx
│   ├── DashboardGuru.tsx
│   ├── DashboardSiswa.tsx
│   ├── DashboardOrangtua.tsx
│   ├── LoginForm.tsx
│   ├── Navigation.tsx
│   ├── StudentCard.tsx
│   ├── CAKEPBadge.tsx
│   ├── Leaderboard.tsx
│   ├── PointsForm.tsx
│   ├── NominationForm.tsx
│   └── NominationValidation.tsx
├── contexts/              # React contexts
│   └── AuthContext.tsx
├── hooks/                 # Custom hooks
│   ├── use-mobile.ts
│   └── use-toast.ts
├── lib/                   # Utilities
│   ├── utils.ts
│   └── mockData.ts       # Demo data
└── types/                 # TypeScript types
    └── index.ts
```

---

## 🚀 Roadmap Pengembangan

### Version 2.0 (Planned)
- **Progressive Web App (PWA)** - Install di homescreen
- **Push Notifications** - Notifikasi real-time
- **WhatsApp Integration** - Notifikasi via WhatsApp
- **Advanced Analytics** - Grafik dan visualisasi data

### Version 3.0 (Future)
- **Digital Portfolio** - Portofolio karakter digital
- **Export/Print Reports** - Laporan yang bisa dicetak
- **Multi-school Support** - Dukungan multiple sekolah
- **AI-powered Insights** - Analisis karakter dengan AI

---

## 🤝 Kontribusi

Aplikasi ini dikembangkan untuk MI Almaarif 02 Singosari. Untuk kontribusi atau saran pengembangan, silakan hubungi tim pengembang.

---

## 📄 Lisensi

© 2024 MI Almaarif 02 Singosari. All rights reserved.

---

## 📞 Kontak & Dukungan

Untuk bantuan teknis atau pertanyaan tentang aplikasi:
- **Email**: [email-sekolah]
- **Telepon**: [nomor-telepon]
- **Alamat**: MI Almaarif 02 Singosari

---

**Bersama membangun generasi CAKEP! 🌟**
