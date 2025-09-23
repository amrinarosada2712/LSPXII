# Gambaran umum

Halaman ini adalah landing page sederhana untuk bisnis rental mobil. Data mobil disimpan dalam array PHP, lalu dirender menjadi kartu produk dengan Bootstrap. Ada navbar, hero/banner, daftar produk, bagian “Tentang Kami”, dan footer.

1) Data awal (PHP)

```
<?php
$rentals = [
    ["Fortuner", 1000000, "fortuner.jpg"],
    ["Creta", 900000, "creta.jpg"],
    ["CRV", 700000, "crv.jpg"]
];
?>
```

ita bikin array `$rentals` berisi daftar mobil.  
Urutannya: `[nama, harga_per_hari, nama_file_gambar]`.

Nantinya array ini di-loop untuk menampilkan kartu produk.

> Tips: lebih rapi kalau pakai array asosiatif:

```
$rentals = [
  ["nama"=>"Fortuner","harga"=>1000000,"gambar"=>"fortuner.jpg"],
  ...
];
```