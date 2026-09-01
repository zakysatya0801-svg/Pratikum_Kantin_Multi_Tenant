# Kantin Multi-Tenant

Aplikasi web **Kantin Multi-Tenant** berbasis Laravel yang digunakan untuk mengelola data kantin dan tenant dalam satu sistem.

## Requirements

Pastikan komputer sudah memiliki:

* PHP >= 8.2
* Composer
* Node.js dan npm
* MySQL
* Git
* Laravel
* Web server lokal seperti ServBay, Laragon, atau sejenisnya

Untuk memastikan requirements sudah tersedia, jalankan:

```bash
php -v
composer -V
node -v
npm -v
git --version
```

## Setup

### 1. Clone repository

Clone repository ke komputer:

```bash
git clone https://github.com/zakysatya0801-svg/Pratikum_Kantin_Multi_Tenant
```

Masuk ke folder project:

```bash
cd kantin-multi-tenant
```

### 2. Install dependency PHP

```bash
composer install
```

### 3. Install dependency JavaScript

```bash
npm install
```

### 4. Buat file environment

Salin file `.env.example` menjadi `.env`:

```bash
cp .env.example .env
```

Jika menggunakan Windows Command Prompt dan perintah tersebut tidak dapat digunakan:

```cmd
copy .env.example .env
```

### 5. Generate application key

```bash
php artisan key:generate
```

### 6. Konfigurasi database

Buka file `.env`, kemudian sesuaikan konfigurasi database.

Contoh:

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=kantin_multi_tenant
DB_USERNAME=root
DB_PASSWORD=
```

Buat database dengan nama:

```text
kantin_multi_tenant
```

Sesuaikan `DB_USERNAME` dan `DB_PASSWORD` dengan konfigurasi MySQL pada komputer masing-masing.

### 7. Jalankan migration

```bash
php artisan migrate
```

Jika project menyediakan seeder:

```bash
php artisan db:seed
```

Atau jalankan migration dan seeder sekaligus:

```bash
php artisan migrate --seed
```

## Run

Jalankan server Laravel:

```bash
php artisan serve
```

Secara default aplikasi dapat diakses melalui:

```text
http://127.0.0.1:8000
```

Untuk menjalankan Vite dalam mode development, buka terminal baru dan jalankan:

```bash
npm run dev
```

Biarkan proses `npm run dev` tetap berjalan selama proses development.

## Test

Untuk menjalankan automated test Laravel:

```bash
php artisan test
```

Atau:

```bash
./vendor/bin/phpunit
```

## Troubleshooting

### 1. Composer tidak ditemukan

Jika muncul pesan seperti:

```text
'composer' is not recognized
```

Pastikan Composer sudah terinstall dan PATH Composer sudah ditambahkan ke environment variables.

Periksa dengan:

```bash
composer -V
```

### 2. NPM tidak ditemukan

Jika muncul:

```text
'npm' is not recognized
```

Pastikan Node.js sudah terinstall.

Periksa dengan:

```bash
node -v
npm -v
```

### 3. Error koneksi database

Pastikan:

* MySQL sedang berjalan.
* Nama database pada `.env` benar.
* Username dan password database benar.
* `DB_HOST` dan `DB_PORT` sesuai dengan konfigurasi MySQL.

Setelah mengubah `.env`, jalankan:

```bash
php artisan config:clear
```

Kemudian coba kembali:

```bash
php artisan migrate
```

### 4. Error `APP_KEY`

Jika aplikasi mengalami masalah karena application key belum tersedia, jalankan:

```bash
php artisan key:generate
```

### 5. Perubahan pada `.env` tidak terbaca

Bersihkan cache konfigurasi:

```bash
php artisan config:clear
php artisan cache:clear
```

### 6. Tampilan CSS atau JavaScript tidak muncul

Pastikan Vite sedang berjalan:

```bash
npm run dev
```

Jika dependency belum terinstall, jalankan:

```bash
npm install
```

Untuk membuat asset production:

```bash
npm run build
```

### 7. Error setelah mengambil perubahan dari Git

Jika repository baru saja diperbarui, jalankan:

```bash
git pull origin main
composer install
npm install
php artisan migrate
```

Jika terdapat perubahan konfigurasi atau cache Laravel:

```bash
php artisan optimize:clear
```

## Development Workflow

Alur dasar untuk menjalankan project:

```bash
git pull origin main
composer install
npm install
php artisan migrate
npm run dev
```

Pada terminal lain:

```bash
php artisan serve
```

Setelah selesai melakukan perubahan:

```bash
git add .
git commit -m "deskripsi perubahan"
git push
```

## Project Structure

Struktur utama project Laravel:

```text
kantin-multi-tenant/
├── app/
├── bootstrap/
├── config/
├── database/
├── public/
├── resources/
├── routes/
├── storage/
├── tests/
├── .env.example
├── artisan
├── composer.json
├── package.json
└── README.md
```

## Notes

* Jangan commit file `.env` ke repository.
* Pastikan `.env.example` selalu diperbarui apabila terdapat environment variable baru.
* Jalankan migration setelah mendapatkan perubahan database dari repository.
* Gunakan `npm run dev` selama development frontend.
* Gunakan `npm run build` untuk membuat asset production.
