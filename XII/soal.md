# **Soal isian singkat (general)** tentang materi halaman “Rental Kami”

```php
$rentals = [
  ["Fortuner", 1000000, "fortuner.jpg"],
  ["Creta",     900000, "creta.jpg"],
  ["CRV",       700000, "crv.jpg"]
];
```

1.  Tulis **1 baris** untuk mengubah **harga CRV** menjadi **750000**.
2.  **Akses elemen**  
    Isi dari `$rentals[1][0]` adalah \_\_\_\_.
3.  **Akses elemen**  
    Isi dari `$rentals[0][2]` adalah \_\_\_\_.
4.  **Tambah elemen**  
    Tambahkan item baru **Avanza, 500000, avanza.jpg** ke `$rentals` (1 baris).
5.  **Prediksi output singkat**  
    Apa yang tercetak oleh:

```php
echo $rentals[0][0] . " - Rp " . number_format($rentals[0][1], 0, ',', '.');
```

6\. Di layar ≥ md, kelas `col-md-4` menghasilkan \_\_\_\_ kartu per baris.

7\. Tautan `href="#produk"` akan menggulir ke elemen yang memiliki atribut `id="____"`.  
8\. Saat tombol “Pesan” untuk item pertama diklik, parameter GET yang dikirim bernama \_\_\_\_ .

9\. Pada `number_format($nilai[1], 0, ',', '.')`, tanda titik (`.`) berfungsi sebagai pemisah \_\_\_\_.

10\. Kelas grid yang menghasilkan **3 kartu per baris** pada layar ≥ md adalah \_\_\_\_\_\_\_\_.

11\. Properti CSS untuk **memotong sudut** gambar kartu menjadi membulat adalah \_\_\_\_\_\_\_\_\_\_\_\_.

12\. File JS yang harus dimuat di akhir `<body>` agar toggler navbar bekerja adalah \_\_\_\_\_\_\_\_\_\_\_\_.

13\. Kelas utilitas untuk **teks rata tengah** pada hero adalah \_\_\_\_\_\_\_\_.

14\. Kombinasi kelas untuk navbar tema gelap adalah \_\_\_\_ dan \_\_\_\_.

15\.  Jelaskan singkat: **mengapa blok deklarasi** `**$rentals**` **diletakkan di paling atas file PHP?** \_\_\_\_

16\. Lengkapi agar harga tampil **Rp 1.000.000** untuk Fortuner:

```php
Rp <?= number_format($rentals[0][1], /* desimal */, /* pemisah desimal */, /* pemisah ribuan */) ?>
```

17\. Baris:

```php
<img src="img/<?= $nilai[2] ?>" alt="<?= $nilai[0] ?>">
```

Jika item saat ini **Fortuner**, maka `src` menjadi \_\_\_\_ dan `alt` menjadi \_\_\_\_.

18\. Pada loop:

```php
foreach ($rentals as $indexarray => $nilai) { ... }
```

Variabel `$indexarray` menyimpan \_\_\_\_ dan `$nilai` menyimpan \_\_\_\_.

19\. Prediksi **URL lengkap** saat tombol **Pesan** pada **Creta** diklik: \_\_\_\_  
(Petunjuk: urutan Fortuner=0, Creta=1, CRV=2)

20\. Jika di `pesan.php` kita membaca:

```php
$i = $_GET['indexarray'];
```

Apa **nilai** `$i` ketika tombol **Pesan** pada **Fortuner** diklik? \_\_\_\_  
Dan dengan nilai tersebut, bagaimana cara mengambil **nama mobil** di halaman `pesan.php`? Tulis 1 ekspresi array: \_\_\_\_.