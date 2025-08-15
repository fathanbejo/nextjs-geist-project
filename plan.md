```markdown
# Rencana Pengembangan Aplikasi Gamifikasi "Bintang CAKEP"

Dokumen ini merupakan blueprint lengkap untuk membangun aplikasi gamifikasi "Bintang CAKEP" berbasis SPA menggunakan Next.js (frontend) dan PHP (backend) dengan MySQL sebagai basis data. Seluruh pesan, validasi, dan UI akan menggunakan bahasa Indonesia.

---

## 1. Struktur Proyek & Dependensi

### 1.1. Struktur Direktori Backend (PHP)
Folder utama (misalnya: /bintang-cakep-app/) akan berisi:
- **/api/**  
  Berisi endpoint PHP:
  - `auth/login.php` & `auth/logout.php` – untuk autentikasi pengguna.
  - `points/award.php` – untuk proses pemberian poin oleh guru.
  - `class/leaderboard.php` – untuk mengambil data leaderboard kelas.
  - `nominations/submit.php`, `nominations/pending.php`, `nominations/validate.php` – untuk pengajuan dan validasi nominasi.
  - `student/profile.php` – untuk mengambil profil detail siswa.
  - `users/index.php` – untuk manajemen CRUD pengguna (khusus admin).
- **/app/core/Database.php**  
  Kelas untuk koneksi database menggunakan PDO dengan error handling dan prepared statements.
- **/app/models/**  
  Misalnya: `User.php`, `Student.php` untuk representasi entitas.
- **/config/database.php**  
  Berisi konfigurasi koneksi (host, username, password, nama database).
- **skema.sql**  
  File SQL yang berisi perintah pembuatan tabel (users, classes, students, points_log, nominations, badges) sesuai blueprint.

### 1.2. Struktur Direktori Frontend (Next.js)
Folder utama (misalnya: `src/`) akan berisi:
- **/app/**  
  - `globals.css` (style global via Tailwind CSS)  
  - `page.tsx` sebagai entry point (menampilkan halaman login jika belum terautentikasi).
- **/components/ui/**  
  Berisi komponen-komponen UI seperti:  
  - `Button.tsx` (tombol modern dengan hover effect dan padding yang konsisten)  
  - Komponen form, card, dan layout.
- **/components/**  
  Komponen spesifik masing-masing halaman:
  - `DashboardAdmin.tsx` – menampilkan statistik dan manajemen data.
  - `DashboardGuru.tsx` – menampilkan peta bintang kelas, form pemberian poin, dan validasi nominasi.
  - `DashboardSiswa.tsx` – menampilkan profil pribadi, leaderboard, dan formulir nominasi.
  - `DashboardOrangtua.tsx` – menampilkan profil dan progres anak secara view-only.
- **/lib/api.ts**  
  Fungsi-fungsi untuk integrasi ke API PHP (misalnya fungsi login, awardPoints, getLeaderboard) dengan error handling dan validasi response.

---

## 2. Langkah-Langkah Implementasi & Perubahan File

### 2.1. Backend PHP
1. **Konfigurasi Database**
   - Buat file `/config/database.php`:
     - Definisikan variabel: `$host`, `$username`, `$password`, `$database`.
     - Tambahkan pengecekan koneksi dan pesan error dalam bahasa Indonesia.
2. **Kelas Koneksi Database**
   - Buat file `/app/core/Database.php`:
     - Implementasikan kelas `Database` menggunakan PDO.
     - Gunakan try-catch untuk menangkap error dan log secara detail.
3. **Endpoint Autentikasi**
   - `/api/auth/login.php`:
     - Terima input JSON `username` dan `password`.
     - Verifikasi password menggunakan `password_verify()` dan enkripsi dengan `password_hash()`.
     - Kembalikan response JSON `{ success: true, message: "Login berhasil", data: {...} }` atau error dalam bahasa Indonesia.
   - `/api/auth/logout.php`:
     - Hapus session dan kembalikan response JSON.
4. **Endpoint Poin & Nominasi**
   - `/api/points/award.php`:
     - Validasi input: `student_id`, `criteria`, `points`, `notes`.
     - Gunakan prepared statement untuk menyimpan record ke tabel `points_log` dan update `total_points` di tabel `students`.
     - Kembalikan response JSON dengan status.
   - `/api/class/leaderboard.php`:
     - Ambil data leaderboard berdasarkan `class_id` dan format sebagai JSON.
   - `/api/nominations/submit.php`:
     - Terima input: `nominated_student_id` dan `reason`.
     - Simpan ke tabel `nominations` dengan status default `pending`.
   - `/api/nominations/pending.php`:
     - Query semua nominasi dengan status `pending` dan kirimkan kepada guru.
   - `/api/nominations/validate.php`:
     - Terima input: `nomination_id` dan `status` (approved/rejected) untuk memperbarui nominasi.
5. **Endpoint Profil & Manajemen Pengguna**
   - `/api/student/profile.php`:
     - Ambil dan kembalikan detail profil siswa, termasuk poin, lencana, dan data lainnya.
   - `/api/users/index.php`:
     - Implementasikan operasi CRUD untuk pengguna (GET, POST, PUT, DELETE) dengan validasi input.
6. **Best Practices & Error Handling**
   - Pastikan setiap endpoint menangani exception menggunakan blok try-catch.
   - Gunakan prepared statements untuk semua query SQL.
   - Format response JSON dengan struktur: `{ success: boolean, message: string, data?: any }`.

### 2.2. Frontend Next.js
1. **Global Style & Setup Tailwind**
   - Modifikasi file `src/app/globals.css` untuk mengintegrasikan Tailwind CSS dan mengatur tipografi serta spacing yang konsisten.
2. **Halaman Masuk (Login)**
   - Ubah `src/app/page.tsx`:
     - Buat form login dengan input `username` dan `password`, dan tombol login (menggunakan komponen `Button.tsx`).
     - Tambahkan validasi client-side dan tampilkan pesan error jika input tidak valid.
3. **Komponen UI Modern**
   - **Button.tsx** di `src/components/ui/`:
     - Buat komponen tombol dengan desain minimalis (background warna solid, padding, border-radius) dan efek hover.
   - Buat komponen-komponen umum seperti form, card, dan alert tanpa menggunakan ikon eksternal.
4. **Halaman Dashboard untuk Masing-Masing Peran**
   - **DashboardAdmin.tsx**:
     - Tampilkan statistik sekolah (total poin, siswa progresif, dll) dengan layout grid dan card.
     - Sediakan fitur manajemen pengguna dan kelas dengan tombol navigasi.
   - **DashboardGuru.tsx**:
     - Tampilkan peta bintang kelas dan daftar nominasi untuk divalidasi.
     - Sediakan form input untuk pemberian poin dan catatan perilaku.
   - **DashboardSiswa.tsx**:
     - Tampilkan profil siswa (poin, level misi, lencana) serta leaderboard kelas.
     - Sediakan form pengajuan nominasi untuk teman.
   - **DashboardOrangtua.tsx**:
     - Tampilkan tampilan view-only dari progres seorang siswa dengan informasi update secara real-time (simulasi mock data).
5. **Layer Integrasi API**
   - Buat file `src/lib/api.ts`:
     - Tulis fungsi seperti `async function login(username, password)` yang melakukan fetch ke endpoint PHP `/api/auth/login.php`.
     - Implementasikan fungsi untuk awardPoints, getLeaderboard, getProfile, dan lainnya.
     - Sertakan handling loading state, error response, dan validasi data.
6. **Routing & State Management**
   - Gunakan built-in routing Next.js untuk berpindah antar halaman.
   - Kelola state autentikasi (token/session) menggunakan context atau penyimpanan lokal (localStorage).
7. **Error Handling & UI Feedback**
   - Tampilkan pesan error dan notifikasi menggunakan komponen alert yang sederhana.
   - Pastikan setiap form menyertakan validasi input dan feedback secara langsung pada UI.

---

## 3. Pengujian & Validasi
- **Backend:**  
  Uji endpoint PHP menggunakan `curl` commands. Contoh:
  ```bash
  curl -X POST http://localhost/bintang-cakep-app/api/auth/login.php \
    -H "Content-Type: application/json" \
    -d '{"username": "admin", "password": "password"}'
  ```
- **Frontend:**  
  Simulasikan response API dengan mock data pada tahap pengembangan awal.
- Pastikan setiap error ditangani dan pesan dalam bahasa Indonesia ditampilkan dengan jelas.
- Lakukan pengecekan cross-origin (CORS) jika frontend dan backend di-deploy pada domain atau port terpisah.

---

## 4. Konfigurasi Deployment
- **Backend PHP & MySQL:**
  - Deploy folder `/bintang-cakep-app/` ke VPS dengan konfigurasi LAMP/LEMP.
  - Ubah konfigurasi di `/config/database.php` sesuai pengaturan server.
  - Impor file skema `skema.sql` ke MySQL untuk membuat tabel yang diperlukan.
- **Frontend Next.js:**
  - Build aplikasi Next.js dengan perintah `npm run build` dan jalankan dengan `npm start` atau melalui PM2.
  - Pastikan routing diatur sehingga SPA dapat berinteraksi dengan endpoint backend.

---

## 5. Manajemen Dependensi & Best Practices
- Gunakan git untuk version control dan commit kode secara berkala.
- Komentar dan dokumentasikan kode dengan bahasa Indonesia.
- Validasi serta sanitasi semua input di backend untuk mencegah serangan SQL Injection.
- Selalu cek error handling dan berikan feedback yang informatif bagi pengguna.
- Pastikan komunikasi data dilakukan melalui HTTPS untuk keamanan.

---

## Summary
- Aplikasi "Bintang CAKEP" akan dikembangkan sebagai SPA dengan Next.js (frontend) dan PHP untuk REST API (backend) menggunakan MySQL.  
- Terdapat endpoint untuk login, pemberian poin, manajemen nominasi, dan CRUD pengguna, lengkap dengan validasi dan error handling dalam bahasa Indonesia.  
- Frontend menggunakan Tailwind CSS dan komponen UI modern untuk menampilkan dashboard bagi Admin, Guru, Siswa, dan Orang Tua.  
- Integrasi API dilakukan melalui layer di `src/lib/api.ts` dengan pengelolaan state autentikasi.  
- Pengujian menggunakan `curl` dan simulasi mock data memastikan responsif dan akurasi data.  
- Deployment dijelaskan untuk server VPS dengan konfigurasi LAMP/LEMP dan pengaturan database yang sesuai.
