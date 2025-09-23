# Alur tombol “Pesan”

*   Saat pengguna klik **Pesan**, mereka diarahkan ke:

```
pesan.php?indexarray=0   // atau 1, 2, dst
```

*   Di `pesan.php`, kamu bisa baca index ini untuk mengambil data mobil yang dipilih dari array yang sama (atau dari DB).  
     

# Gambaran umum pesan.php

File ini adalah **halaman form pemesanan**. Alurnya:

*   Ambil index mobil dari URL (`indexarray`).
*   Siapkan data mobil (`$rentals`).
*   Tentukan pilihan mobil (dari dropdown atau default dari `indexarray`).
*   Validasi input saat form disubmit.
*   Hitung total (harga × durasi − diskon + supir).
*   Jika “Simpan” ditekan dan valid, munculkan alert & redirect.

# 1) Blok PHP (logika server-side)

```php
$id = $_GET['indexarray'];
```

*   Mengambil indeks mobil dari URL (`?indexarray=...`) untuk menentukan default pilihan mobil.

```php
$rentals = [
  ["Fortuner", 1000000, "fortuner.jpg"],
  ["Creta", 900000, "creta.jpg"],
  ["CRV", 700000, "crv.jpg"]
];
```

*   Sumber data mobil: nama, harga per hari, dan file gambar.

```php
$pilih_mobil = $_POST['car'] ?? $rentals[$id][0];
```

*   Menentukan mobil terpilih: kalau user sudah memilih di dropdown (POST) pakai itu, kalau belum pakai yang dari indeks URL.

```php
$pilih_harga = array_column($rentals, 1, 0)[$pilih_mobil];
```

*   Membuat peta `nama_mobil → harga` lalu ambil harga mobil terpilih.

```php
$supir = isset($_POST['supir']);
$durasi = $_POST['durasi'] ?? '';
$total_bayar = 0;
$errors = [];
```

*   Menangkap status checkbox supir (boolean), durasi sewa (hari), inisialisasi total, dan array penampung pesan error.

# 2) Saat form disubmit (metode POST)

```php
if ($_SERVER['REQUEST_METHOD'] == 'POST') {
    if (!is_numeric($durasi)) { $errors[] = "Durasi harus berupa angka"; }
    if (!is_numeric($_POST['identitas'])) { $errors[] = "Identitas harus berupa angka"; }
    if (strlen($_POST['identitas']) !== 16) { $errors[] = "Nomor Identitas harus 16 digit angka."; }
```

*   Validasi dasar:
    *   Durasi harus angka.
    *   Identitas harus angka dan panjangnya tepat 16 digit.

```php
    if (empty($errors)) {
        $total_harga_mobil = $pilih_harga * $durasi;
        $diskon = ($durasi >= 3) ? 0.1 * $total_harga_mobil : 0;
        $biaya_supir = $supir ? 100000 * $durasi : 0;
        $total_bayar = $total_harga_mobil - $diskon + $biaya_supir;
    }
```

*   Perhitungan biaya jika validasi lolos:
    *   **Harga dasar** = harga harian × durasi.
    *   **Diskon** 10% jika durasi ≥ 3 hari.
    *   **Biaya supir** = Rp100.000 × durasi jika dicentang.
    *   **Total bayar** = harga dasar − diskon + supir.

# 3) Aksi saat tombol “Simpan” ditekan

```php
if (isset($_POST['simpan'])) {
    $diskon = ($durasi >= 3) ? 0.1 * $total_harga_mobil : 0;
    $check = $supir == "checked" ? 'Ya' : 'Tidak';
    $nama = $_POST['nama'];
    $identitas = $_POST['identitas'];
    $gender = $_POST['gender'];
    $detail_pesanan = "Pesanan Berhasil!\n\n"
        . "Nama: $nama\n"
        . "Nomor Identitas: $identitas\n"
        . "Jenis Kelamin: $gender\n"
        . "Jenis Mobil: $pilihmobil \n"
        . "Supir: $check\n" 
        . "Durasi:$durasi \n"
        . "Diskon: $diskon  \n"
        . "Total Bayar: Rp " . number_format($total_bayar, 0, ',', '.');

    echo "<script>
        alert(`$detail_pesanan`);
        window.location.href = 'index.php';
    </script>";
    exit();
}
```

*   Ketika tombol **Simpan** diklik:
    *   Disusun teks ringkasan pesanan (nama, identitas, gender, mobil, supir, durasi, diskon, total).
    *   Ditampilkan lewat `alert()` JavaScript, lalu diarahkan kembali ke `index.php`.

> Bagian ini memproses dan menampilkan ringkasan berdasarkan nilai dari form dan hasil perhitungan sebelumnya.

# 4) Head HTML (frontend & styling)

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Form Pemesanan</title>
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
```

*   Set karakter, viewport responsif.
*   Memakai Bootstrap 5 via CDN untuk gaya dan komponen siap pakai.

# 5) Struktur halaman & kartu

```html
<div class="container mt-5">
  <div class="card">
    <div class="card-header bg-primary text-white text-center">
      <h5>Form Pemesanan</h5>
    </div>
    <div class="card-body">
      ...
    </div>
  </div>
</div>
```

*   Container memberi margin & layout responsif.
*   Card + header biru untuk judul form.

# 6) Menampilkan error validasi (jika ada)

```php
<?php if ($errors) { ?>
  <div class="alert alert-danger">
    <ul>
      <?php foreach ($errors as $error) { ?>
        <li><?= $error ?></li>
      <?php } ?>
    </ul>
  </div>
<?php } ?>
```

*   Jika `$errors` berisi pesan, tampilkan dalam alert merah berbentuk list.

# 7) Form pemesanan (field demi field)

```html
<form method="POST">
```

*   Form mengirim data via **POST** ke halaman yang sama.

a) Nama Pemesan

```html
<input type="text" class="form-control mb-3" name="nama"
       placeholder="Nama Pemesan" value="<?= $_POST['nama'] ?? '' ?>" required>
```

*   Input teks, mewajibkan pengisian, dan mengisi ulang nilai sebelumnya bila form reload.

**b) Jenis Kelamin (radio)**

```html
<label class="form-label">Jenis Kelamin</label><br>
<input class="form-check-input" type="radio" name="gender" value="Laki-laki"
  <?= ($_POST['gender'] ?? '') === 'Laki-laki' ? 'checked' : '' ?>> Laki-laki
<input class="form-check-input ms-3" type="radio" name="gender" value="Perempuan"
  <?= ($_POST['gender'] ?? '') === 'Perempuan' ? 'checked' : '' ?>> Perempuan
```

*   Dua pilihan radio, otomatis “checked” sesuai input sebelumnya.

**c) Nomor Identitas**

```html
<input type="text" class="form-control mb-3" name="identitas"
       placeholder="Nomor Identitas (16 digit)"
       value="<?= $_POST['identitas'] ?? '' ?>" required>
```

*   Input teks untuk 16 digit identitas; validasi angka & panjang dilakukan di server (bagian PHP).

**d) Pilihan Mobil (dropdown)**

```html
<select class="form-select mb-3" name="car" onchange="this.form.submit()">
  <?php foreach ($rentals as $indexarray => $nilai) { ?>
    <option value="<?= $nilai[0] ?>" <?= ($nilai[0] === $pilih_mobil) ? 'selected' : '' ?>>
      <?= $nilai[0] ?>
    </option>
  <?php }?>
</select>
```

*   Dropdown berisi nama mobil.
*   `onchange="this.form.submit()"` akan mengirim form otomatis saat pilihan berubah (memperbarui harga di bawahnya).

**e) Harga Mobil (readonly)**

```html
<input type="text" class="form-control mb-3" name="harga"
       value="<?= number_format($pilih_harga, 0, ',', '.') ?>" readonly>
```

*   Menampilkan harga per hari dari mobil terpilih dalam format Rupiah.

**f) Tanggal Sewa**

```html
<input type="date" class="form-control mb-3" name="tanggal"
       value="<?= $_POST['tanggal'] ?? '' ?>" required>
```

*   Tanggal mulai sewa.

**g) Durasi (hari)**

```html
<input type="number" class="form-control mb-3" name="durasi"
       placeholder="Durasi Sewa (hari)" value="<?= $durasi ?>" required>
```

*   Durasi dalam hari; dicek di server agar numerik.

**h) Checkbox Supir**

```html
<div class="mb-3">
  <input class="form-check-input" type="checkbox" name="supir"
         <?= $supir ? 'checked' : '' ?>>
  Termasuk Supir (Rp 100.000/hari)
</div>
```

**h) Checkbox Supir**

```html
<div class="mb-3">
  <input class="form-check-input" type="checkbox" name="supir"
         <?= $supir ? 'checked' : '' ?>>
  Termasuk Supir (Rp 100.000/hari)
</div>
```

*   Jika dicentang, biaya supir akan dihitung per hari.

**i) Total Bayar (readonly)**

```html
<input type="text" class="form-control mb-3" id="total"
       value="<?= $total_bayar ? number_format($total_bayar, 0, ',', '.') : '' ?>"
       placeholder="Total Bayar" readonly>
```

*   Menampilkan total setelah perhitungan (muncul saat POST valid).

**j) Tombol aksi**

```html
<button type="submit" class="btn btn-primary">Hitung Total</button>
<button type="submit" name="simpan" class="btn btn-primary">Simpan</button>
<button type="reset" class="btn btn-danger">Cancel</button>
```

*   **Hitung Total**: mengirim form untuk validasi & perhitungan total.
*   **Simpan**: mengirim form lalu menampilkan alert ringkasan dan redirect.
*   **Cancel**: reset input form di sisi klien.

# 8) Aturan harga & diskon (ringkas)

*   **Harga dasar** = `harga per hari × durasi`.
*   **Diskon 10%** jika durasi ≥ 3 hari.
*   **Supir** = `Rp 100.000 × durasi` bila dicentang.
*   **Total** = `harga dasar − diskon + supir`.

# 9) Alur penggunaan (ringkas)

1.  Pengguna datang dari halaman produk dengan URL `?indexarray=...`.
2.  Dropdown mobil default sesuai indeks URL; mengubah pilihan akan submit otomatis untuk menyesuaikan harga.
3.  Pengguna isi nama, gender, identitas (16 digit), tanggal, durasi, dan centang supir bila perlu.
4.  Klik **Hitung Total** untuk melihat total di kolom “Total Bayar”.
5.  Klik **Simpan** untuk menampilkan alert ringkasan dan kembali ke `index.php`.

[Kembali](index.md)