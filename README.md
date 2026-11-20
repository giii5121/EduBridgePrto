# EduBridge — Studi Kasus Frontend

Situs portofolio satu halaman yang membahas satu project: **EduBridge**, platform deteksi learning gap Matematika kelas XI SMA. Halaman ini berfokus pada peran **Frontend Developer**: apa yang dikerjakan, bagaimana alurnya, teknologi yang dipakai, dan hasil verifikasinya.

Dibuat dengan HTML, CSS, dan JavaScript murni. Tanpa build tool, tanpa framework, tanpa backend. Konten ditulis langsung di `index.html` supaya tetap terbaca tanpa JavaScript dan ramah mesin pencari.

## Struktur

```
index.html                    Konten, struktur, dan metadata
css/styles.css                Token warna, layout, komponen, animasi
js/main.js                    Reveal on scroll, active nav, tahun footer
assets/edubridge/             Screenshot EduBridge (desktop dan mobile)
assets/fonts/                 Instrument Sans variable (WOFF2)
assets/og.png                 Gambar pratinjau 1200 x 630
assets/favicon.svg            Ikon situs
vercel.json                   Header keamanan dan cache untuk Vercel
netlify.toml                  Konfigurasi publish untuk Netlify
```

## Menjalankan lokal

Buka `index.html` langsung di browser. Semua fitur tetap berjalan dari file system.

Kalau ingin lewat server lokal:

```powershell
npx serve .
```

Atau:

```powershell
python -m http.server 8000
```

Lalu buka `http://localhost:8000`.

## Mengganti konten

### 1. Identitas dan tautan

Cari dan ganti di `index.html`:

- `Soaloon Yogi` menjadi namamu. Muncul di header, footer, `<title>`, dan metadata.
- `soaloonpoerba13@gmail.com` menjadi emailmu. Muncul di header, kontak, dan footer.
- `https://github.com/giii5121` dan `https://www.linkedin.com/in/soaloon-poerba-32714437a` menjadi profilmu.
- `https://github.com/giii5121/EduBridge` menjadi tautan repository project.
- `https://domainkamu.com/` menjadi domain final. Muncul di canonical, `og:url`, dan `og:image`.
- `2026` di footer hanya nilai awal; `js/main.js` mengisi tahun berjalan secara otomatis.

### 2. Section halaman

Halaman terdiri dari tujuh bagian:

1. **Hero** — nama project, tagline, peran, stack, konteks, tahun, dan cover.
2. **Ringkasan** (`#proyek`) — masalah, pendekatan, statistik, dan alur lima langkah.
3. **Peran saya** (`#peran`) — kontribusi utama dan pembagian kerja dengan tim.
4. **Fitur utama** (`#fitur`) — empat kartu fitur dan galeri empat screenshot.
5. **Teknologi** (`#teknologi`) — stack, arsitektur, dan catatan rendering KaTeX.
6. **Hasil** (`#hasil`) — metrik verifikasi dan batasan yang perlu disebut.
7. **Kontak** (`#kontak`) — ajakan menghubungi dan email.

Setiap section diberi penanda `data-reveal` agar muncul saat di-scroll. Delay animasi diatur lewat `--reveal-delay` pada elemen.

### 3. Screenshot

Screenshot di `assets/edubridge/` berasal dari repository project dan memakai rasio **8:5** (2400 x 1500). Untuk mengganti:

- Letakkan gambar baru di `assets/edubridge/`.
- Perbarui atribut `src`, `alt`, `width`, dan `height` di `index.html`.
- Cover hero memakai `01-homepage-desktop.png` dan `01-homepage-mobile.png`.
- Kartu fitur memakai `02-belajar-desktop.png`, `07-kuis-desktop.png`, `06-progres-desktop.png`, dan `08-guru-desktop.png`.
- Galeri memakai `10-editor-ai-desktop.png`, `03-mode-gelap-desktop.png`, `04-katalog-desktop.png`, dan `12-admin-desktop.png`.

Gunakan format PNG, JPG, atau WebP. Pertahankan rasio 8:5 agar `object-fit: cover` tidak memotong bagian penting.

### 4. Warna dan tipografi

Semua token ada di bagian atas `css/styles.css`:

```css
--ground: #0b0b0c;
--ink: #f4f4f2;
--accent: #4265db;
--accent-text: #9db1ff;
```

- `--accent` dipakai untuk tombol, bidang kontak, dan footer.
- `--accent-text` dipakai untuk teks aksen, link, dan angka agar kontras di atas latar gelap.
- `--accent-ink` adalah warna teks di atas bidang biru.
- Font memakai satu keluarga variabel di `assets/fonts/`; ganti file dan `@font-face` bila ingin typeface lain.

### 5. Gambar Open Graph

`assets/og.png` adalah gambar pratinjau 1200 x 630. Ganti dengan tangkapan layar atau komposisi milikmu, lalu perbarui `og:image` dengan URL absolut domain final.

## Deploy

### Vercel

Dari folder ini:

```powershell
npx vercel
```

Saat diminta konfigurasi, pilih framework **Other**, biarkan build command kosong, dan output directory `.`. Untuk deploy otomatis, hubungkan repository GitHub di dashboard Vercel dengan pengaturan yang sama.

### Netlify

Cara tercepat: buka [app.netlify.com/drop](https://app.netlify.com/drop), lalu seret folder ini ke halaman tersebut.

Untuk Netlify dari Git, publish directory `.` dan build command kosong. `netlify.toml` sudah menyiapkan publish directory.

## Sebelum publish

- [ ] Ganti domain placeholder di canonical, `og:url`, dan `og:image`.
- [ ] Pastikan email, GitHub, dan LinkedIn sudah benar.
- [ ] Periksa kembali klaim peran dan kontribusi di section "Peran saya".
- [ ] Ganti `assets/og.png` bila perlu, lalu perbarui URL absolutnya.
- [ ] Cek tampilan di lebar 1440, 1024, 768, dan 390 piksel.
- [ ] Uji navigasi keyboard dan tautan eksternal.
- [ ] Pastikan screenshot tidak memuat data pribadi atau kredensial.

## Catatan project

EduBridge memakai CDA dan CDM P-DINA untuk mendeteksi learning gap Matematika kelas XI. Kalibrasi P-DINA pada project ini masih sintetis; halaman studi kasus menampilkan batasan tersebut secara eksplisit agar tidak diklaim sebagai validasi untuk siswa nyata.

## Lisensi dan kredit

- Typeface: [Instrument Sans](https://fonts.google.com/specimen/Instrument+Sans), SIL Open Font License, disajikan lewat [Fontsource](https://fontsource.org/).
- Screenshot: repository [EduBridge](https://github.com/giii5121/EduBridge).
- Ikon dan aset lain mengikuti repository project.
