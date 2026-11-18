# Object Fit 
Adalah Sebuah Properti Untuk Menentukan bagaimana Sebuah Image Menyesuaikan Ukurannya Terhadap elemen Yang Membungkusnya

> Dari Ai

# Object-fit di CSS

`object-fit` mengatur bagaimana konten *replaced element* (seperti `<img>`, `<video>`, atau `<canvas>`) menyesuaikan ukurannya di dalam kotak elemen tersebut. Ini sangat berguna saat gambar punya rasio berbeda dari container-nya, sehingga tidak gepeng atau melar.

## Nilai-nilai `object-fit`

**1. `fill` (default)**
Gambar dipaksa mengisi seluruh kotak, tanpa menjaga rasio aspek. Hasilnya bisa melar atau gepeng.

**2. `contain`**
Gambar diperkecil/diperbesar agar *seluruhnya terlihat* di dalam kotak, dengan rasio aspek tetap terjaga. Bisa ada ruang kosong di sisi gambar (letterbox).

**3. `cover`**
Gambar memenuhi seluruh kotak dengan rasio aspek terjaga, tetapi bagian yang berlebih akan **terpotong**. Ini yang paling sering dipakai untuk thumbnail, banner, atau foto profil.

**4. `none`**
Gambar tidak diubah ukurannya sama sekali, tampil dengan ukuran aslinya dan dipotong jika lebih besar dari kotak.

**5. `scale-down`**
Gambar dibandingkan antara `none` dan `contain`, lalu dipilih yang hasilnya lebih kecil. Jadi gambar tidak akan pernah diperbesar melebihi ukuran aslinya.

## Contoh Kode

```html
<div class="galeri">
  <img src="foto.jpg" class="fill" alt="">
  <img src="foto.jpg" class="contain" alt="">
  <img src="foto.jpg" class="cover" alt="">
  <img src="foto.jpg" class="none" alt="">
  <img src="foto.jpg" class="scale-down" alt="">
</div>
```

```css
.galeri img {
  width: 200px;
  height: 200px;
  border: 2px solid #333;
}

.fill       { object-fit: fill; }
.contain    { object-fit: contain; }
.cover      { object-fit: cover; }
.none       { object-fit: none; }
.scale-down { object-fit: scale-down; }
```

## Mengatur Posisi dengan `object-position`

Secara default, gambar berada di tengah (`50% 50%`). Dengan `object-position`, kita bisa menentukan bagian mana yang ditampilkan, misalnya saat memakai `cover`:

```css
img {
  width: 300px;
  height: 200px;
  object-fit: cover;
  object-position: top;        /* fokus ke bagian atas */
}

/* Contoh lain */
object-position: left center;
object-position: 20% 80%;
object-position: 10px 30px;
```

Ini berguna misalnya untuk foto orang, agar wajah tidak terpotong.

## Contoh Kasus Umum

**Foto profil bulat:**
```css
.avatar {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  object-fit: cover;
}
```

**Gambar responsif di card:**
```css
.card img {
  width: 100%;
  aspect-ratio: 16 / 9;
  object-fit: cover;
}
```

**Video memenuhi background:**
```css
.bg-video {
  position: fixed;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1;
}
```

## Ringkasan Singkat

| Nilai | Rasio terjaga? | Terpotong? | Ruang kosong? |
|---|---|---|---|
| `fill` | Tidak | Tidak | Tidak |
| `contain` | Ya | Tidak | Mungkin |
| `cover` | Ya | Mungkin | Tidak |
| `none` | Ya | Mungkin | Mungkin |
| `scale-down` | Ya | Mungkin | Mungkin |

## Tips Penting

- `object-fit` hanya bekerja jika elemen punya **lebar dan tinggi yang jelas** (misalnya lewat `width`, `height`, atau `aspect-ratio`).
- Properti ini **tidak berlaku untuk `background-image`**. Untuk background, gunakan `background-size: cover` atau `contain`, yang konsepnya mirip.
- Dukungan browser modern sudah sangat baik (semua browser utama).

Mau saya buatkan demo interaktif agar kamu bisa langsung membandingkan semua nilainya, atau ada bagian tertentu yang ingin dibahas lebih dalam?
