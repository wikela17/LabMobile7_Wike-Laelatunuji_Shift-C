Penjelasan cara kerja login dalam aplikasi Ionic 8 dengan Angular:

 1. Membuat Database dan API Backend
- Database: Buat database bernama coba-ionic dengan tabel user berisi username dan password yang di-hash menggunakan MD5.
- File koneksi.php: Menyediakan koneksi ke database MySQL.
- File login.php: Menerima data username dan password via php://input, mengecek data tersebut di database, dan mengembalikan status login (berhasil atau gagal) beserta token jika login berhasil.

 2. Frontend dengan Ionic dan Angular
- Setup Project: Buat project dengan ionic start dan instal modul yang diperlukan.
- Formulir Login:
  - Halaman login dibuat di app/login/login.page.html dengan input untuk username dan password.
  - Di login.page.ts, fungsi login() digunakan untuk mengirim permintaan ke API menggunakan AuthenticationService.

 3. Authentication Service
- Service (authentication.service.ts):
  - Mengelola proses autentikasi, menyimpan token di Preferences, dan mengelola status login dengan BehaviorSubject.
  - Fungsi postMethod() mengirimkan data ke API.
  - saveData() menyimpan token dan nama pengguna.
  - logout() menghapus data sesi dan mengatur status autentikasi ke false.

 4. Guards untuk Proteksi Rute
- Auth Guard (auth.guard.ts):
  - Mencegah akses ke rute tertentu tanpa autentikasi.
- Auto-Login Guard (auto-login.guard.ts):
  - Mengarahkan pengguna yang sudah login langsung ke halaman home.

 5. Rute Aplikasi
- app-routing.module.ts: Rute home dilindungi oleh authGuard, sementara rute login dilindungi autoLoginGuard.

 6. Halaman Home
- Halaman home menampilkan nama pengguna dan memiliki opsi logout.

 Alur Login
1. Pengguna memasukkan username dan password di formulir.
2. Fungsi login() mengirim data ke login.php.
3. Jika respons API menunjukkan sukses, data disimpan dan pengguna diarahkan ke home.
4. Jika gagal, notifikasi ditampilkan.

Pendekatan ini mencakup autentikasi berbasis token untuk menjaga sesi pengguna, validasi input, dan proteksi rute menggunakan Angular Guards.

Tampilan Halaman:

![Screenshot 2024-11-04 132050](https://github.com/user-attachments/assets/9ee1511a-d551-44b6-a0c8-e9062d30dedd)
![Screenshot 2024-11-04 132110](https://github.com/user-attachments/assets/cada121e-213e-4497-89aa-70ae7946c311)

T
