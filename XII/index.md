# FR.IA.02 — TPD: Tugas Praktik Demonstrasi

## Skema Sertifikasi (KKNI/Okupasi/Klaster)

**Judul:** SKEMA SERTIFIKASI OKUPASI PEMROGRAM JUNIOR (JUNIOR CODER)  
**Nomor:** _(diisi)_  
**TUK:** Sewaktu / Tempat Kerja / Mandiri _(coret yang tidak perlu)_  
**Nama Asesor:** MUHAMMAD CAHYOWIBOWO  
**Nama Asesi:** _(diisi)_  
**Tanggal:** _(diisi)_

---

## Petunjuk

*   Baca dan pelajari setiap instruksi kerja di bawah ini dengan cermat sebelum melaksanakan praktik.
*   Klarifikasi kepada asesor kompetensi apabila ada hal-hal yang belum jelas.
*   Laksanakan pekerjaan sesuai dengan urutan proses yang sudah ditetapkan.
*   Seluruh proses kerja mengacu kepada SOP/WI yang dipersyaratkan (jika ada).

---

## Skenario Tugas Praktik Demonstrasi

### Kelompok Pekerjaan 1

| No. | Kode Unit | Judul Unit |
| --- | --- | --- |
| 1 | J.620100.004.02 | Menggunakan Struktur Data |
| 2 | J.620100.009.01 | Menggunakan Spesifikasi Program |
| 3 | J.620100.010.01 | Menerapkan Perintah Eksekusi Bahasa Pemrograman Berbasis Teks, Grafik, dan Multimedia |
| 4 | J.620100.016.01 | Menulis Kode Dengan Prinsip Sesuai Guidelines dan Best Practices |
| 5 | J.620100.017.02 | Mengimplementasikan Pemrograman Terstruktur |
| 6 | J.620100.025.02 | Melakukan Debugging |
| 7 | J.620900.025.02 | Melakukan Instalasi Sistem Operasi |
| 8 | J.620900.026.02 | Melakukan Instalasi Software Aplikasi |

### Deskripsi Skenario

Untuk memenuhi Skema Sertifikasi Okupasi Pemrogram Junior (Junior Coder), Anda diminta untuk mendemonstrasikan pekerjaan:

*   **Menerapkan Perintah Eksekusi Bahasa Pemrograman** berbasis teks, grafik, dan multimedia.
*   **Menulis Kode** dengan prinsip sesuai guidelines dan best practices.
*   **Mengimplementasikan Pemrograman Terstruktur.**

Anda adalah seorang _Junior Web Developer_ yang ditugaskan oleh perusahaan untuk mengembangkan **aplikasi pemesanan rental mobil sederhana**.

#### Fitur Aplikasi

1\. Terdapat menu untuk menampilkan

Contoh tampilan: [(materi)](awal.md)

[https://github.com/amrinarosada2712/LSPXII/blob/main/XII/img/Picture3.png](https://github.com/amrinarosada2712/LSPXII/blob/main/XII/img/Picture3.png)

*   Produk (sertakan image 3 contoh jenis mobil : Fortuner, Creta, CRV) 
*   Daftar harga , tampilan tabel harga
*   Tentang kami, berisi uraian deskripsi alamat rental, no telp, alamat email
*   Pesan , tampil form dan ketentuannya dijelaskan pada butir

2\. Pengunjung dapat memesan  rental mobil dengan skenario sebagai berikut: [(materi)](pesan.md)

*   Tampilan form pemesanan Link gambar:  
    [https://raw.githubusercontent.com/amrinarosada2712/LSPXII/refs/heads/main/XII/img/Picture1.png](https://raw.githubusercontent.com/amrinarosada2712/LSPXII/refs/heads/main/XII/img/Picture1.png)

**Aturan pengisian form:**

| Field | Aturan |
| --- | --- |
| Nama Pemesan | Isi dengan nama pemesan. |
| Jenis Kelamin | Pilih **laki** atau **perempuan**. |
| Nomor Identitas | Isi dengan angka **16 digit**; jika tidak, muncul pesan: _“isian salah.. data harus 16 digit”_. |
| Tipe | Pilih **Fortuner**, **Creta**, **CRV**. |
| Harga | Isi nilai sesuai tipe: **Fortuner / Creta / CRV**. |
| Tanggal Pesan | Format tanggal: **dd/mm/yyyy**. |
| Durasi Menginap | Isi dengan **angka**; jika bukan angka, muncul pesan: _“harus isi angka”_. |
| Termasuk Breakfast | **Checkbox** dicentang berarti _Ya_. |
| Total Bayar | Terisi otomatis saat klik tombol **Hitung Total Bayar** sesuai ketentuan di bawah. |

**Ketentuan perhitungan Total Bayar:**

*   Jika **lama nyewa > 3 hari**, maka **diskon 10%**.
*   Jika **pilih supir**, maka **tambahan 100.000**.

**Penyimpanan data**: Hasil isian disimpan dalam **array** atau **tabel** pada **database MySQL**, dan ditampilkan kembali (mis. dalam tabel riwayat).

link gambar:  
[https://raw.githubusercontent.com/amrinarosada2712/LSPXII/refs/heads/main/XII/img/Picture2.png](https://raw.githubusercontent.com/amrinarosada2712/LSPXII/refs/heads/main/XII/img/Picture2.png)  
**Media**: Tambahkan **foto** dan **video** jenis mobil yang tersedia (Fortuner, Creta, CRV).  
Link Gambar:

[https://raw.githubusercontent.com/amrinarosada2712/LSPXII/refs/heads/main/XII/img/creta.jpg](https://raw.githubusercontent.com/amrinarosada2712/LSPXII/refs/heads/main/XII/img/creta.jpg)

[https://raw.githubusercontent.com/amrinarosada2712/LSPXII/refs/heads/main/XII/img/crv.jpg](https://raw.githubusercontent.com/amrinarosada2712/LSPXII/refs/heads/main/XII/img/crv.jpg)  
[https://raw.githubusercontent.com/amrinarosada2712/LSPXII/refs/heads/main/XII/img/fortuner.jpg](https://raw.githubusercontent.com/amrinarosada2712/LSPXII/refs/heads/main/XII/img/fortuner.jpg)

Soal Esay untuk mencari jawaban dari coding disini silahkan kerjakan dibuku tulis:

Klik [disini Soal Esay](soal.md) 

---

## Alat dan Bahan

**a. Perangkat Komputer (minimum):**

*   CPU Intel Pentium 4 @ 3 GHz atau sederajat
*   Sistem operasi: Microsoft Windows 7, Ubuntu 18.04.3 LTS, atau sederajat
*   Memori 4 GB
*   Ruang kosong hard disk 250 GB
*   Resolusi layar 1024 × 768 px

**b. Software Tools:**

*   XAMPP (PHP development environment)
*   Text Editor (Sublime Text 3 / Atom / VS Code / dll.)
*   Diagramming Tools (Visio / Visual Paradigm / Lucidchart / dll.)

**c. Alat tulis**

---

## Waktu Pengerjaan

**6 Jam = 360 Menit**

---

## Langkah Kerja

### 1) Menerapkan Perintah Eksekusi Bahasa Pemrograman Berbasis Teks, Grafik, dan Multimedia

**Mengidentifikasi mekanisme running/eksekusi source code**

*   Identifikasi cara dan tools untuk mengeksekusi source code.
*   Identifikasi parameter untuk mengeksekusi source code.
*   Identifikasi peletakan source code sehingga bisa dieksekusi dengan benar.

**Mengeksekusi source code**

*   Eksekusi source code sesuai mekanisme eksekusi dari tools pemrograman yang digunakan.
*   Identifikasi perbedaan antara _running_, _debugging_, atau membuat _executable file_.

**Mengidentifikasi hasil eksekusi**

*   Eksekusi source code sesuai skenario yang direncanakan.
*   Identifikasi permasalahan bila eksekusi source code gagal/tidak berhasil.

---

### 2) Menulis Kode dengan Prinsip Sesuai Guidelines dan Best Practices

**Menerapkan coding-guidelines dan best practices dalam penulisan program (kode sumber)**

*   Tulis kode sumber mengikuti coding-guidelines dan best practices.
*   Buat struktur program sesuai konsep paradigmanya.
*   Tangani galat/error.

**Menggunakan ukuran performansi dalam menuliskan kode sumber**

*   Hitung efisiensi penggunaan resources oleh kode.
*   Implementasikan kemudahan interaksi sesuai standar yang berlaku.

---

### 3) Mengimplementasikan Pemrograman Terstruktur

**Menggunakan tipe data dan kontrol program**

*   Tentukan tipe data yang sesuai standar.
*   Gunakan sintaks program yang dikuasai sesuai standar.
*   Gunakan struktur kontrol program yang dikuasai sesuai standar.

**Membuat program sederhana**

*   Buat program baca-tulis untuk memasukkan data dari keyboard dan menampilkan ke layar monitor, termasuk variasinya sesuai standar masukan/keluaran.
*   Gunakan struktur kontrol percabangan dan pengulangan dalam membuat program.

**Membuat program menggunakan prosedur dan fungsi**

*   Buat program dengan **prosedur** sesuai aturan penulisan program.
*   Buat program dengan **fungsi** sesuai aturan penulisan program.
*   Buat program dengan **prosedur dan fungsi** secara bersamaan sesuai aturan penulisan program.
*   Berikan keterangan untuk setiap prosedur dan fungsi.

**Membuat program menggunakan array**

*   Tentukan dimensi array.
*   Tentukan tipe data array.
*   Tentukan panjang array.
*   Gunakan pengurutan array.

**Membuat program untuk akses file**

*   Buat program untuk menulis data ke media penyimpan.
*   Buat program untuk membaca data dari media penyimpan.

**Mengompilasi program**

*   Koreksi kesalahan program.
*   Bebaskan kesalahan sintaks dalam program.

---

## ASESI

**Nama:** _(diisi)_  
**Tanda tangan & Tanggal:** _(diisi)_

## ASESOR

**Nama:**   
**No. Reg:** MET.000.010392 2023  
**Tanda tangan & Tanggal:** _(diisi)_

---

## Penyusun dan Validator

### Penyusun

| No | Nama | Nomor MET | Tanda Tangan & Tanggal |
| --- | --- | --- | --- |
| 1 |   | MET.000.010392 2023 |   |
| 2 |   |   |   |

### Validator

| No | Nama | Nomor MET | Tanda Tangan & Tanggal |
| --- | --- | --- | --- |
| 1 |   |   |   |
| 2 |   |   |   |