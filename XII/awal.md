# Gambaran umum

Halaman landing **Rental Kami**:

*   Data mobil disiapkan di PHP
*   Ditampilkan jadi grid kartu produk pakai Bootstrap.
*   Ada navbar, banner (hero), daftar produk, “Tentang Kami”, dan footer.
*   Tombol **Pesan** mengirim user ke `pesan.php` sambil membawa index mobil.

# 1) Data sumber (blok PHP paling atas)

```php
<?php
$rentals = [
    ["Fortuner", 1000000, "fortuner.jpg"],
    ["Creta", 900000, "creta.jpg"],
    ["CRV", 700000, "crv.jpg"]
];
?>
```

*   File dieksekusi server dulu (PHP), baru hasilnya dikirim ke browser.
*   `$rentals` adalah **array 2D**. Tiap baris = 1 mobil:

1.  `[$nilai[0]]` → **nama mobil** (string)
2.  `[$nilai[1]]` → **harga per hari** (integer, satuan rupiah)
3.  `[$nilai[2]]` → **nama file gambar** (string, dicari di folder `img/`)

*   Kenapa ditaruh di atas? Biar bisa dipakai di mana saja pada HTML berikutnya (khususnya di loop produk).

**Contoh cara “membaca” isi baris pertama**  
`["Fortuner", 1000000, "fortuner.jpg"]` → nama = `Fortuner`, harga = `1000000`, gambar = `fortuner.jpg`.

# 2) Kerangka HTML & Head (judul + asset)

```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Rental Kami</title>
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
```

*   `<!DOCTYPE html>`: standar HTML5.
*   `lang="id"`: bahasa Indonesia (bagus untuk SEO & pembaca layar).
*   `viewport`: bikin tampilan responsif di HP (tanpa ini, layout suka “kekecilan”).
*   Link ke **Bootstrap CSS** via CDN: semua kelas Bootstrap (grid, tombol, dll.) jadi bisa dipakai.

# 3) CSS internal (tampilan khusus halaman)

```css
.product-card { text-align: center; }
.product-card img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  border-radius: 10px;
}
.hero-plain{
  min-height: 360px;
  width: 100%;
  background-image:
    linear-gradient(rgba(0,0,0,.45), rgba(0,0,0,.45)),
    url('img/fortuner.jpg');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  padding: 64px 0;
}
```

*   `.product-card`: memusatkan isi setiap kartu.
*   `.product-card img`:
    *   `width:100%` → gambar selebar kartu.
    *   `height:200px` + `object-fit:cover` → tinggi seragam, gambar dipotong rapi tanpa “gepeng”.
    *   `border-radius:10px` → sudut membulat.
*   `.hero-plain` (banner):
    *   `min-height:360px` → tinggi minimum banner.
    *   `background-image`: **2 layer**:
        *   `linear-gradient(rgba(0,0,0,.45), rgba(0,0,0,.45))` → overlay gelap transparan agar teks putih terbaca
        *   `url('img/fortuner.jpg')` → gambar latar hero.
*   `background-size:cover` → menutupi area hero dengan crop rapi.
*   `background-position:center` → fokus di tengah gambar.
*   `padding:64px 0` → ruang atas-bawah agar teks “nafas”.

# 4) Navbar (menu atas responsif)

```html
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container">
    <a class="navbar-brand" href="#">Rental Kami</a>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav ms-auto">
        <li class="nav-item"><a class="nav-link" href="#produk">Produk</a></li>
        <li class="nav-item"><a class="nav-link" href="#tentang">Tentang Kami</a></li>
      </ul>
    </div>
  </div>
</nav>
```

*   `navbar-expand-lg` → menu melebar (horizontal) di layar besar, **collapse** (ditutup) jadi hamburger di HP.
*   `navbar-dark bg-dark` → tema gelap.
*   Tombol **toggler** (hamburger) mengontrol elemen dengan `id="navbarNav"` (lihat `data-bs-target`).
*   `ms-auto` (margin-start auto) mendorong menu ke kanan.
*   Link `href="#produk"` dan `href="#tentang"` adalah **anchor**: klik → scroll ke section dengan `id` tersebut.

# 5) Hero/Banner (judul + CTA)

```html
<section class="hero-plain d-flex align-items-center">
  <div class="container text-center text-white">
    <h1 class="display-5 fw-bold mb-2">Rental Mobil Mudah & Cepat</h1>
    <p class="lead mb-4">Fortuner • Creta • CRV — siap jalan kapan pun Anda perlu</p>
    <div class="d-flex justify-content-center gap-2">
      <a href="#produk" class="btn btn-light btn-lg">Lihat Produk</a>
    </div>
  </div>
</section>
```

*   `d-flex align-items-center` → konten vertikalnya sejajar (dipusatkan) dalam area hero.
*   `text-center text-white` → teks di tengah, warna putih (kontras dgn overlay).
*   `display-5` (ukuran judul besar), `fw-bold` (tebal), `lead` (subjudul lebih “ringan”).
*   Tombol **Lihat Produk** menuju section produk (anchor `#produk`).

# 6) Section Produk: wadah & judul

```html
<div class="container mt-5">
  <section id="produk">
    <h2 class="text-center">Jenis Kamar</h2>
    <div class="row">
      ...
    </div>
  </section>
</div>
```

*   `container` memberi padding kiri/kanan standar Bootstrap.
*   `mt-5` (margin-top besar) memberi jarak dari hero.
*   `id="produk"`: target anchor.
*   Judul yang tampil saat ini: **“Jenis Kamar”** (sesuai kode kamu).

# 7) Grid kartu produk (loop PHP)

```php
<?php foreach ($rentals as $indexarray => $nilai) { ?>
  <div class="col-md-4">
    <div class="product-card">
      <img src="img/<?= $nilai[2] ?>" alt="<?= $nilai[0] ?>">
      <h5 class="mt-2"><?= $nilai[0] ?></h5>
      <h5 class="mt-2">Rp <?= number_format($nilai[1], 0, ',', '.') ?></h5>
      <a href="pesan.php?indexarray=<?= $indexarray ?>" class="btn btn-primary mt-2">Pesan</a>
    </div>
  </div>
<?php } ?>
```

**Yang terjadi di sini:**

*   `foreach` mengulang setiap mobil dalam `$rentals`.
    *   `$indexarray` = 0 (Fortuner), 1 (Creta), 2 (CRV) → dipakai ke URL.
    *   `$nilai` = array `[nama, harga, gambar]` untuk item saat ini.
*   `col-md-4` → pada layar **≥ md (≥ 768px)**, dibuat **3 kolom** per baris; pada layar kecil otomatis turun jadi 1 kolom.
*   `<img src="img/<?= $nilai[2] ?>">` → per mobil, gambar diambil dari folder `img/`:
    *   Fortuner → `img/fortuner.jpg`
    *   Creta → `img/creta.jpg`
    *   CRV → `img/crv.jpg`
*   `<h5><?= $nilai[0] ?></h5>` → menampilkan **nama mobil**.
*   `number_format($nilai[1], 0, ',', '.')` → memformat **harga**:
    *   1000000 → `1.000.000`
    *   Parameternya: `0` (tanpa desimal), pemisah desimal `,`, pemisah ribuan `.`
*   Tombol **Pesan**:
    *   URL-nya: `pesan.php?indexarray=<?= $indexarray ?>`
    *   Contoh hasil:
        *   Fortuner → `pesan.php?indexarray=0`
        *   Creta → `pesan.php?indexarray=1`
        *   CRV → `pesan.php?indexarray=2`
*   **Makna:** halaman `pesan.php` bisa membaca `$_GET['indexarray']` untuk tahu mobil mana yang dipilih.

8) Section “Tentang Kami” (kartu info & kontak)

```html
<div class="container mt-5">
  <section id="tentang">
    <div class="card shadow-lg">
      <div class="card-body text-center">
        <h2 class="card-title">Tentang Kami</h2>
        <p class="card-text">Selamat datang di <strong>Rental Kami</strong>...</p>
        <p class="card-text">Kami berlokasi di <strong>Jalan Flamboyan III</strong>...</p>
        <p class="card-text">Kami selalu mengutamakan kepuasan pelanggan...</p>
        <hr>
        <h5>Hubungi Kami</h5>
        <p><strong>📍 Alamat:</strong>Jalan Flamboyan III</p>
        <p><strong>📞 Telepon:</strong> <a href="tel:[+62895383875089]">+62895383875089</a></p>
        <p><strong>📧 Email:</strong> <a href="mailto:[rentalkami@gmail.com]">rentalkami@gmail.com</a></p>
      </div>
    </div>
  </section>
</div>
```

*   `card shadow-lg` → kotak putih rapi dengan bayangan tebal (lebih menonjol).
*   `text-center` → semua teks rata tengah.
*   **Info Kontak**:
    *   `tel:` dan `mailto:` membuat nomor telepon/email **klikable**:
        *   di HP → membuka dialer
        *   di desktop → membuka app email default saat klik email

# 9) Footer (hak cipta sederhana)

```html
<footer class="bg-dark text-white text-center py-3 mt-5">
  <p>&copy; 2025 Rental.</p>
</footer>
```

*   `bg-dark text-white` → latar gelap, teks putih.
*   `text-center` → rata tengah.
*   `py-3` → padding atas-bawah sedang, `mt-5` → jarak atas yang besar.

# 10) Script Bootstrap (interaksi navbar, dll.)

```html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
```

*   **bundle** sudah termasuk Popper (dibutuhkan untuk komponen seperti dropdown/toggler).
*   Ditaruh di akhir `<body>` agar halaman dirender dulu (praktik umum untuk performa).

# 11) Alur data & interaksi dari kacamata pengguna

1.  Browser minta halaman → **server menjalankan PHP** → hasil HTML + CSS dikirim ke browser.
2.  Pengguna melihat **hero** dan klik **Lihat Produk** → halaman scroll ke section produk.
3.  Di grid, setiap kartu menampilkan **gambar**, **nama**, dan **harga**.
4.  Klik **Pesan** pada salah satu mobil → dibawa ke `pesan.php` dengan parameter `indexarray` sesuai item (0/1/2).
5.  Di `pesan.php`, kamu bisa gunakan nilai `indexarray` untuk menampilkan form pemesanan khusus mobil tersebut.

# 12) Struktur folder yang disarankan

```
/proyek-rental
├─ index.php           // file ini
├─ pesan.php           // halaman pemesanan (lanjutan)
└─ /img
   ├─ fortuner.jpg
   ├─ creta.jpg
   └─ crv.jpg
```

*   Pastikan nama file gambar **persis** sama dengan yang dirujuk di array.

# 13) Menjalankan di lokal (cepat)

*   Pakai XAMPP/Laragon, atau bawaan PHP:

1.  Buka terminal pada folder proyek.
2.  Jalankan:  `localhost:8000`
3.  Buka browser: `http://localhost:8000/index.php`

# 14) Cara menambah/mengubah produk (opsional, **tanpa** mengubah bagian lain)

Tambahkan baris di array:

```php
$rentals[] = ["Avanza", 500000, "avanza.jpg"];
```

# 15) Glosarium kelas Bootstrap yang dipakai (biar gampang ingat)

*   `container` → lebar konten terpusat dengan gutter.
*   `row` / `col-md-4` → sistem grid 12 kolom; `col-md-4` = 3 kolom per baris saat ≥768px.
*   `navbar navbar-expand-lg` → navbar responsif, melebar di layar besar.
*   `navbar-dark bg-dark` → tema gelap untuk navbar.
*   `text-center`, `text-white` → perataan dan warna teks.
*   `display-5`, `lead`, `fw-bold` → tipografi (judul besar, paragraf lead, tebal).
*   `btn btn-light btn-lg` / `btn btn-primary` → tombol siap pakai.
*   `mt-2`, `mt-5`, `py-3`, `gap-2` → utilitas jarak (margin/padding/gap).
*   `card`, `card-body`, `shadow-lg` → kartu konten dengan bayangan besar.

# 16) Troubleshooting cepat

*   **Gambar tidak muncul** → cek `img/nama-file.jpg` cocok dengan di array.
*   **Navbar tidak bisa collapse di HP** → pastikan `<script ...bootstrap.bundle.min.js>` ada di akhir.
*   **Font/ikon tampak “berantakan”** → kadang CDN ke-block; pastikan internet aktif atau gunakan mirror CDN lain (opsional).
*   **Klik “Produk”/“Tentang Kami” tidak scroll** → pastikan `id="produk"` dan `id="tentang"` ada (sudah ada di kode).