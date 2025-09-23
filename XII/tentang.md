# 6) Section “Tentang Kami”

```
<section id="tentang">
  <div class="card shadow-lg">
    <div class="card-body text-center">
      <h2 class="card-title">Tentang Kami</h2>
      <p>Selamat datang di <strong>Rental Kami</strong> ...</p>
      ...
      <h5>Hubungi Kami</h5>
      <p><strong>📍 Alamat:</strong>Jalan Flamboyan III</p>
      <p><strong>📞 Telepon:</strong> <a href="tel:[+62895383875089]">+62895383875089</a></p>
      <p><strong>📧 Email:</strong> <a href="mailto:[rentalkami@gmail.com]">rentalkami@gmail.com</a></p>
    </div>
  </div>
</section>
```

*   Pakai kartu Bootstrap untuk tampilan bersih + `shadow-lg`.
*   Link telepon & email bisa diklik di HP/desktop.

> Perbaikan kecil:
> 
> Hapus tanda kurung siku di `tel:` dan `mailto:`:
> 
> `<a href="tel:+62895383875089">+62895383875089</a> <a href="mailto:rentalkami@gmail.com">rentalkami@gmail.com</a>`

# 7) Footer

`<footer class="bg-dark text-white text-center py-3 mt-5">  <p>&copy; 2025 Rental.</p> </footer>`

Footer sederhana dengan warna gelap dan teks center.

---

# 8) JavaScript Bootstrap

`<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>`

Memuat komponen interaktif (collapse navbar, dsb). Pakai “bundle” yang sudah termasuk Popper.