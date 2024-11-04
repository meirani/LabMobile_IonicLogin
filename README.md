# Penjelasan Cara Kerja Login
## Nabila Winanda Meirani
## H1D022108
## Praktikum Pemograman Mobile Shift D

# Demo
![App Demo](2024-11-05%2000-55-15.gif)

# Penjelasan

### Membuat Database dan menghubungkannya
#### File Koneksi.php pada direktori laragon
- buat database di mysql bernama coba-ionic
- file konesi.php ini berfungsi untuk menghubungkan aplikasi dengan database di mysql yang bernama coba-ionic
- jika konesi gagal, maka akan muncul pesan "koneksi gagal"

#### File Login.php
- file ini berfungsi untuk menerima data login yang diinputkan user di frontend (di ionic)
- data yang diambil diubah menjadi format JSON agar mudah diproses
- lalu data yang diinputkan di cocokkan di database
- jika berhasil maka JSON akan mengirimkan data-data termasuk token dan pesan berhasil
- jika gagal maka akan dikirimkan pesan gagal

### Pembuatan Frontend pada Ionic

#### app.module.ts
- file ini merupakan file utama yang mengatur aplikasi
- file ini lah yang menghubungkan aplikasi dengan API nya
- provideHttpClient di deklarasikan agar aplikasi dapat berinteraksi dengan API
```
import { provideHttpClient } from '@angular/common/http';
providers: [{ provide: RouteReuseStrategy, useClass: IonicRouteStrategy }, provideHttpClient()],
```

#### authentication.service.ts
- file yang mengelola autentikasi pengguna
- terdapat metode untuk mengirimkan data login yang diinputkan pengguna, lalu menangani pesan responnya
- terdapat preferences yang menyimpan data token dan pengguna secara lokal

#### auth.guard.ts
- file ini Memastikan hanya pengguna yang sudah login yang bisa mengakses halaman.
- jika pengguna blm login, maka diarahkan ke halaman login

#### auto-login.guard.ts
- untuk mengarahkan pengguna ke halaman dashboard jika pengguna sudah login tp mencoba mengakses halaman login
- jadi file ini mencegah pengguna yang sudah ter autentikasi login ulang

#### app-routing.module.ts 
- membuat dan mengatur jalur navigasi pada halaman-halaman di aplikasi
- membuat path yang menghubungkan halaman dengan URL

#### login.page.html
- sebuah file untuk menampilkan tampilan login
- isinya terdapat 2 field form dan satu button

#### login.page.ts
- file yang mengatur login
- mengambil inputan dari pengguna lalu dikirimkan ke authentication.service.ts
- menampilkan pesan kesalahan jika login gagal

#### home.page.html
- file untuk tampilan halaman dashboard

#### home.page.html
- file yang mengatur halaman dashboard
- terdapat fungsi logout untuk keluar dan mengarahkannya ke halaman login


