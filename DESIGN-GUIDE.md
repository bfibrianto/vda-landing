# Design Guide — Landing Page PT Vascomm Digital Asia (VDA)

**Status:** Acuan desain, siap dieksekusi
**Tanggal:** 28 Juli 2026 · **Revisi 2** — setelah pemeriksaan visual situs induk
**Ruang lingkup:** Satu halaman profil anak perusahaan, ditempatkan di lingkungan brand vascomm.co.id
**Dokumen ini menentukan:** arah visual, design token, sistem komponen, arsitektur halaman, dan draft copy.

> **Yang berubah di revisi 2.** Revisi 1 disusun dari HTML + CSS produksi. Pemeriksaan tampilan jadi memunculkan perangkat brand yang tidak terbaca dari kode, dan membatalkan dua keputusan:
> 1. **Highlight kuning di headline** ternyata perangkat tanda tangan induk, bukan sekadar warna tombol → diangkat jadi elemen utama hero VDA, berbentuk pill (§2.2a, §4.1, §9).
> 2. **Band CTA gelap dibatalkan** → diganti band gradient + tombol kuning, mengikuti induk (§2.2b, §5, §8).
> 3. **Koreksi fakta:** induk mayoritas memakai **Title Case**, bukan sentence case seperti klaim revisi 1. Sentence case tetap direkomendasikan, tapi kini berstatus penyimpangan sadar (§2.3).
> 4. Ditambahkan aturan foto, aturan ikon, dan daftar cacat situs induk yang tidak boleh terulang (§5, §10).

---

## 1. Ringkasan Eksekutif

VDA bukan Vascomm versi kecil. Vascomm menjual **jasa membangun** (custom development, enterprise, perbankan, siklus penjualan panjang, berbasis kepercayaan). VDA menjual **produk yang sudah jadi** dan solusi AI — siklus lebih pendek, lebih self-serve, lebih product-led.

Perbedaan model bisnis itu harus terbaca dalam 3 detik pertama di halaman, tanpa VDA terlihat lepas dari induknya.

Arah yang saya pilih: **VDA adalah saudara kandung Vascomm, bukan kembarannya.** Mewarisi DNA biru dan nada bahasa Indonesia-B2B yang sama, tapi diekspresikan lewat geometri yang berbeda secara sistematis.

**Tesis desain — "Geometri yang sama, sudut yang dilunakkan."**

Logo Vascomm adalah dua **belah ketupat bersudut tajam** yang saling mengunci membentuk hati. Logo VDA adalah dua **goresan membulat** (lingkaran + stadium) yang saling mengunci membentuk loop. Konstruksinya identik, radiusnya berlawanan. Perbedaan itu sudah ada di logo — tugas halaman ini hanya mengangkatnya menjadi sistem desain.

> **Vascomm = sudut. VDA = radius.**
> Konsekuensinya: di halaman VDA tidak ada satu pun sudut siku-siku pada elemen brand. Radius adalah identitas, bukan dekorasi.

**Catatan penting soal ketepatan tesis ini.** Setelah memeriksa tampilan jadi situs induk, geometri tajam berlaku pada **logo, kartu, tombol, dan blok highlight** — di situlah kontrasnya bekerja. Tapi induk memakai **mask lingkaran** untuk foto tim dan tombol scroll-to-top yang bulat. Jadi induk bukan "tajam total", dan VDA tidak sedang melawan induk — VDA mengambil sisi membulat yang sudah ada di induk lalu menjadikannya sistem yang konsisten. Ini justru argumen yang lebih kuat: bukan pemberontakan, tapi pemurnian.

---

## 2. Temuan Riset

### 2.1 Audit vascomm.co.id (terukur dari CSS produksi)

Situs induk dibangun dengan WordPress + Elementor + LiteSpeed. Token global yang terpasang:

| Token | Nilai | Catatan |
|---|---|---|
| `--e-global-color-primary` | `#007EFF` | Biru utama brand — **inilah warna jangkar induk** |
| `--e-global-color-secondary` | `#54595F` | Abu netral |
| `--e-global-color-text` | `#7A7A7A` | Body text — terlalu terang, kontras lemah |
| Teks gelap | `#3D3D3D` | Dipakai untuk heading |
| Tombol primer | bg `#007EFF`, teks putih, Rubik 500, 1em | |
| Tombol sekunder | bg `#F7C505`, teks hitam | Aksen kuning satu-satunya |
| Gradient | `linear-gradient(100deg, #2575FC 0%, #6A11CB 100%)` | Biru→ungu generik |
| Wash section | `linear-gradient(180deg, #fff 0%, #00ACFF24 100%)` | Semburat biru sangat tipis |
| Font | Roboto (global), Rubik (tombol), Raleway (h1/h3–h5 tema), Roboto Slab, Nunito | Lima keluarga font — tidak disiplin. Yang **tampil** di layar terbaca sebagai sans geometris berterminal lembut, konsisten dengan Rubik. Identifikasi pasti perlu dicek di browser. |
| Radius | `0`, `3px`, `5px`, `10px`, `50%` | Kartu ≈ `0`. Tombol ≈ `4–6px`. Foto & tombol scroll-top = `50%`. |
| H1 | `3.3125em / 1.2`, weight 600, Raleway | |

**Warna logo Vascomm (hasil sampling piksel pada mark asli):**
`#283898` → `#2040A0` → `#2050A8` → `#1070C0` → `#0888D0` → `#00A0E8` (dominan) → `#70C8F0`

Gradient logo bergerak dari **indigo pekat ke cyan terang** — jauh lebih hidup daripada gradient biru→ungu yang dipakai di CSS situs.

**Penilaian jujur atas situs induk:**
- **Yang layak diwarisi:** warna jangkar `#007EFF`; **highlight kuning di headline** (§2.2); **band gradient + tombol kuning** (§2.2); pola copy (eyebrow + headline + paragraf pendukung); mask foto bulat; struktur footer (Link / Kontak / alamat / copyright); nada "kemitraan dan kepercayaan".
- **Yang jangan diwarisi:** lima keluarga font tanpa hierarki; gradient biru→ungu yang tidak ada hubungannya dengan logo; body text `#7A7A7A` (kontras di bawah standar); ritme spasi Elementor yang tidak konsisten; ikon ilustratif gaya stock; hero yang berlubang besar; header sticky yang menabrak konten.

### 2.2 Perangkat visual induk — hanya terlihat dari tampilan jadi

Empat hal berikut tidak terbaca dari CSS, tapi jelas begitu situsnya dilihat. Ketiganya perangkat brand sungguhan dan **wajib diwarisi** supaya VDA terbaca sekeluarga.

**a. Highlight kuning di headline — ini perangkat tanda tangan induk.**
Headline hero berbunyi "Bisnis `Optimal`, Hasil `Maksimal`" dengan **blok kuning `#F7C505` pekat sebagai latar** di balik dua kata kunci, teksnya hitam. Kuning di sini bukan sekadar warna tombol sekunder — ia **marker tipografis** yang menandai kata mana yang membawa janji.

> Ini temuan paling berharga dari screenshot. VDA harus memakai perangkat yang sama — **tapi bloknya berbentuk pill, bukan persegi.** Perangkat identik, radius berlawanan: satu detail kecil yang menyampaikan seluruh tesis §1 dalam sekali lihat, di elemen pertama yang dilihat orang.

**b. Band CTA = gradient biru + tombol kuning.**
Section ajakan bertindak digambar sebagai pita gradient biru melebar penuh, dengan tombol kuning di atasnya. Kombinasi gradient-plus-kuning inilah "suara CTA" induk.

> Konsekuensi: rencana awal saya memakai band **navy hampir hitam** untuk CTA VDA saya batalkan. Itu insting default saya, bukan turunan dari brand ini. Band CTA VDA memakai `--grad-vda` dengan tombol pill kuning. Lihat revisi di §4.1 dan §8.

**c. Foto bermask bulat dan bernada biru.**
Foto tim ditampilkan dalam mask lingkaran, dengan color grading kebiruan yang kuat (seragam biru + tint biru). Bukan foto stock persegi.

**d. Tombol membawa ikon di depan label.**
"Diskusikan dengan Kami", "Mari Berkolaborasi", "Ceritakan Kebutuhan Anda" — semuanya berikon. Detail kecil, tapi khas.

**Satu hal lagi yang terlihat, dan tidak boleh ditiru:** pada satu section CTA, header sticky menabrak konten — teks dan tombol kuning tumpang tindih dengan navigasi. Selain itu hero induk punya rongga kosong besar di bawah tombol. Dua-duanya harus dihindari; lihat §10.

### 2.3 Pola copy induk yang harus dipertahankan

Setiap section di vascomm.co.id memakai formula yang sama:

```
[eyebrow pendek, sering bahasa Inggris]   → "Our Unique Value" · "3 Simple Steps" · "Collaboration Opportunity"
[headline bahasa Indonesia]                → "Transformasi Digital Adalah Kunci Kesuksesan Bisnis Masa Kini"
[paragraf pendukung 1–2 kalimat]
```

Label CTA yang dipakai induk: *Diskusikan dengan Kami* · *Ceritakan Kebutuhan Anda* · *Mari Berkolaborasi* · *Selengkapnya*.

**Dua koreksi atas dokumen versi pertama saya**, setelah melihat tampilan jadinya:

1. **Induk mayoritas memakai Title Case, bukan sentence case.** "Transformasi Digital Adalah Kunci Kesuksesan Bisnis Masa Kini", "Kolaborasi Untuk Inovasi", "Mengoptimalkan Teknologi Untuk Digitalisasi Di Setiap Lini" — semuanya Title Case. Hanya sebagian kecil yang sentence case ("Bukan janji, tapi jaminan kualitas..."). Versi pertama dokumen ini menulis bahwa sentence case "mengikuti gaya induk" — itu keliru.
2. **Eyebrow induk berukuran kecil, warna abu, Title Case, tanpa titik penanda, tanpa warna** — bukan uppercase berwarna seperti yang saya spesifikasikan.

VDA tetap memakai sentence case dan eyebrow mono berwarna, tapi sekarang keduanya berstatus **penyimpangan yang disengaja**, bukan warisan. Alasannya: Title Case Pada Setiap Kata membuat headline terbaca seperti brosur korporat, dan VDA menjual produk yang dipakai sehari-hari. Kalau kamu ingin konsistensi keluarga lebih diutamakan daripada nada produk, ini titik yang paling masuk akal untuk diubah — cukup ganti dua aturan di §4.2 dan §5, sisanya tidak terpengaruh.

**Yang tetap diwarisi apa adanya:** struktur tiga-lapis (eyebrow → headline → paragraf), bahasa Inggris untuk eyebrow, dan kosakata CTA.

### 2.4 Audit empat produk VDA

| Produk | Warna brand | Font | Bahasa | Posisi | URL |
|---|---|---|---|---|---|
| **KelolaHR** | `#045157` teal pekat | — | Indonesia | "Solusi HRIS Modern #1 di Indonesia", mulai Rp 7.500. Absensi GPS + face recognition + biometrik, payroll otomatis. CTA "Coba Gratis" | kelolahr.id |
| **DIVA Creative** | `#EC4899` pink + `#001B85` | Plus Jakarta Sans | Indonesia | "Branding It Better!" — web & app, branding & desain, social media management | divacreative.id |
| **Sitamoto** | `#36C6B9` turquoise | — | **Inggris** | "Indonesia's Leading AI Business Platform" — WhatsApp CRM automation, AI agents, intelligent analytics | sitamoto.ai |
| **TalentGo** | `#2575FC` / `#0C83D4` | Inter | Indonesia | "IT Resource Hunter by Vascomm" — Talent Outsource, Sharing Talent, Talent Squad | talentgo.id |

**Masalah desain nyata yang harus dipecahkan:** empat produk ini punya warna yang saling bertabrakan (teal pekat, pink, turquoise, biru). Ditampilkan berdampingan tanpa aturan, section produk akan terlihat seperti kliping majalah.

**Aturan penyelesaiannya ada di §7.** Ringkasnya: kartu produk netral, warna brand hanya muncul sebagai aksen tipis.

**Catatan positif:** TalentGo memakai `#2575FC` — persis warna awal gradient Vascomm. Benang merah keluarga sudah ada, tinggal dirapikan.

---

## 3. Positioning & Pesan

**Satu pekerjaan halaman ini:** membuat pengunjung vascomm.co.id paham dalam 10 detik bahwa VDA menjual produk siap pakai + AI, lalu mengklik ke situs produk yang relevan.

**Metrik keberhasilan:** klik keluar ke empat domain produk. Bukan waktu di halaman, bukan scroll depth.

| | Vascomm (induk) | VDA (anak) |
|---|---|---|
| Yang dijual | Jasa membangun sistem | Produk jadi + solusi AI |
| Pembeli | Enterprise, bank, pemerintah | SME sampai enterprise, tim operasional |
| Waktu ke nilai | Bulan | Hari sampai minggu |
| Nada | Kepercayaan, rekam jejak, kemitraan | Kecepatan, kesiapan, hasil terukur |
| Ajakan | "Ceritakan kebutuhan Anda" | "Coba produknya" |

**Positioning statement (untuk dipakai di section Tentang):**
> VDA membawa hasil belajar Vascomm selama hampir satu dekade membangun sistem untuk perbankan dan enterprise, lalu mengemasnya jadi produk yang bisa langsung dipakai.

Ini kalimat penting: menjelaskan *kenapa* anak perusahaan ini kredibel, dan sekaligus membenarkan keberadaan halaman ini di domain induk.

---

## 4. Design Tokens

### 4.1 Warna

Palet diturunkan dari sumbu gradient logo VDA, bukan dari CSS situs induk. Alasannya: gradient biru→ungu di situs induk tidak merepresentasikan brand mana pun, sedangkan gradient logo adalah aset brand sungguhan.

```css
:root {
  /* ---- Inti VDA: sumbu gradient logo (TERUKUR dari Logo-FINAL.png) ---- */
  --vda-indigo:      #34509A;  /* ujung gelap logo — hover, awal gradient */
  --vda-blue:        #4368B2;  /* warna tanda tangan VDA — tombol, link, ikon. 5.4:1 di atas putih */
  --vda-sky:         #6098D0;  /* ujung terang logo — glow ambient, stroke. Dekoratif saja */

  /* ---- Jangkar induk ---- */
  --vascomm-blue:    #007EFF;  /* HANYA untuk elemen lineage: chip induk, link balik ke vascomm.co.id */
  --signal:          #F7C505;  /* kuning induk — perangkat highlight headline + tombol band CTA */

  /* ---- Netral bersemburat biru ---- */
  --ink:             #101728;  /* heading. Bukan hitam — hitam kebiruan, senapas dengan logo */
  --ink-body:        #4A5468;  /* body text. Kontras 8.1:1 di atas putih (induk hanya 4.0:1) */
  --ink-muted:       #7A869C;  /* caption, metadata */
  --line:            #E2E8F2;  /* border, divider */
  --paper:           #FFFFFF;
  --paper-tint:      #F4F7FC;  /* selang-seling section */
  --on-grad:         #FFFFFF;  /* teks di atas band gradient */

  /* ---- Gradient tanda tangan ---- */
  --grad-vda: linear-gradient(135deg, var(--vda-indigo) 0%, var(--vda-blue) 45%, var(--vda-sky) 100%);

  /* ---- Warna brand produk (aksen saja, tidak pernah jadi bidang besar) ---- */
  --brand-kelolahr:  #045157;
  --brand-diva:      #EC4899;
  --brand-sitamoto:  #36C6B9;
  --brand-talentgo:  #2575FC;
}
```

**Aturan pemakaian warna:**

1. `--vda-blue` adalah satu-satunya warna interaktif. Semua link dan tombol primer memakainya.
2. `--grad-vda` hanya boleh muncul di **tiga** tempat: mark logo, stroke rail produk (§6), dan band CTA penutup. Gradient yang tersebar di mana-mana adalah ciri halaman generik.
3. `--signal` (kuning) tepat **dua** pemakaian, mewarisi perangkat induk (§2.2):
   - **Highlight pill di headline hero** — blok kuning `--r-pill` di balik dua kata kunci, teks `--ink`. Padding `0.1em 0.4em`. Ini pemakaian utamanya.
   - **Tombol pada band CTA penutup** — pill kuning, teks `--ink`, di atas `--grad-vda`.
   Tidak ada pemakaian ketiga. Badge "AI" pada kartu Sitamoto memakai warna brand produknya sendiri, bukan kuning.
4. Tidak ada section berlatar gelap. **Band CTA memakai `--grad-vda`, bukan navy.** Ini revisi dari versi pertama dokumen — lihat §2.2b.
5. Warna brand produk **tidak pernah** menjadi background. Hanya: garis 3px di atas kartu, tint ikon, dan warna hover.
6. Kontras kuning: `#F7C505` dengan teks `--ink` mencapai ±11:1. Kuning **tidak pernah** dipasangkan dengan teks putih.

> ✅ **Sudah diverifikasi (28 Juli 2026).** Ketiga nilai di atas diambil dengan sampling piksel dari `Logo-FINAL.png`. Estimasi awal saya (`#2B44A0` / `#2E6FD4` / `#5EA9E5`) ternyata **terlalu pekat dan terlalu cyan**; logo aslinya jauh lebih lembut, ke arah periwinkle/steel. Struktur paletnya tetap, hanya angkanya yang diganti.
>
> ⚠️ **Yang masih kurang:** logo hanya tersedia sebagai raster (PNG 3000×3000). Konsekuensinya, mark tidak bisa lagi "menggambar dirinya sendiri" lewat `stroke-dashoffset` seperti rencana di §4.6. Kalau versi SVG-nya muncul, animasi itu bisa dihidupkan lagi.

> ⚠️ **Bentuk mark, koreksi penting.** Tesis §1 menyebut mark VDA sebagai "dua belah ketupat membulat". Setelah melihat file aslinya, itu **keliru**. Bentuk sebenarnya: **cincin lingkaran di kiri, stadium diagonal di tengah, dan stadium di kanan bawah**, membentuk satu loop menerus. Tesis besarnya tetap berdiri (induk bersudut, VDA membulat), tapi jangan pakai deskripsi "belah ketupat" saat menjelaskan logo ke siapa pun.

### 4.2 Tipografi

> ✅ **Diperbarui (28 Juli 2026): font brand resmi ditemukan.** VDA punya font sendiri — **Vascomm Sans** (`vascomm-sans-v1.1/`, 12 file statis WOFF2: Thin–Bold × normal/italic). Ini menggantikan rencana awal di bawah, yang menyusun pasangan Sora + Inter dari font pihak ketiga karena saat itu belum ada font brand. Prinsip "satu display + satu body yang dipasangkan sengaja" **tidak lagi berlaku** — dengan font brand tunggal, display dan body memakai **keluarga yang sama**, dibedakan lewat bobot saja. Ini justru lebih benar secara brand: satu wajah tipografi yang konsisten, bukan pasangan yang dipilih AI.
>
> Hanya 4 dari 12 bobot yang dipakai (Regular 400, Medium 500, Semibold 600, Bold 700) — cocok pas dengan seluruh nilai `font-weight` yang sudah ada di kode, tidak ada perubahan struktur CSS lain yang diperlukan. Thin, Light, dan seluruh varian italic di-skip supaya payload font tetap kecil (4 file, ±54KB) karena tidak ada elemen di halaman yang memakainya.

```css
@font-face { font-family:'Vascomm Sans'; src:url('vascomm-sans-v1.1/VascommSans-Regular.woff2') format('woff2'); font-weight:400; font-display:swap; }
@font-face { font-family:'Vascomm Sans'; src:url('vascomm-sans-v1.1/VascommSans-Medium.woff2') format('woff2'); font-weight:500; font-display:swap; }
@font-face { font-family:'Vascomm Sans'; src:url('vascomm-sans-v1.1/VascommSans-Semibold.woff2') format('woff2'); font-weight:600; font-display:swap; }
@font-face { font-family:'Vascomm Sans'; src:url('vascomm-sans-v1.1/VascommSans-Bold.woff2') format('woff2'); font-weight:700; font-display:swap; }

--font-display: 'Vascomm Sans', system-ui, sans-serif;   /* 600, 700 */
--font-body:    'Vascomm Sans', system-ui, sans-serif;   /* 400, 500, 600 */
--font-mono:    'JetBrains Mono', ui-monospace, monospace; /* 500 — TETAP, lihat alasan di bawah */
```

**Kenapa mono tetap JetBrains Mono, bukan Vascomm Sans:** brand font ini tidak punya potongan monospace. Prinsip §4.2 awal tetap berlaku untuk peran ini — utility face terpisah untuk eyebrow, label statistik, dan **nama domain produk** (`kelolahr.id`, `sitamoto.ai`). Domain memang alamat, dan menyetelnya dengan mono membuatnya *terbaca sebagai alamat*.

⚠️ **Belum di-QA visual:** nilai `letter-spacing` di bawah ini (mis. `-.03em` pada display) dikalibrasi untuk metrik Sora/Clash Display, bukan Vascomm Sans. Font brand kemungkinan punya lebar dan tinggi-x yang berbeda. Cek tracking secara visual setelah font brand tampil dan sesuaikan angkanya kalau terasa terlalu rapat atau terlalu longgar — jangan anggap angka lama otomatis benar untuk font baru.

<details>
<summary>Rencana awal sebelum font brand ditemukan (diarsipkan, tidak lagi dipakai)</summary>

Situs induk memakai lima keluarga font tanpa hierarki. VDA awalnya direncanakan memakai tiga font pihak ketiga:

- **Sora (display)** — sans geometris dengan bowl bulat dan potongan terminal yang datar. Konstruksi hurufnya (`o`, `a`, `g`, `d`) adalah lingkaran-dan-stadium — mengulang primitif bentuk logo VDA.
- **Inter (body)** — terbukti terbaca pada ukuran kecil untuk teks bahasa Indonesia yang cenderung panjang.
- **JetBrains Mono (utility)** — tetap dipakai, lihat di atas.

Alasan Sora/Inter sudah tidak relevan sekarang karena keduanya bukan font brand — begitu Vascomm Sans tersedia, font brand asli selalu menang atas pasangan pihak ketiga sebaik apa pun alasannya.

</details>

**Skala tipe (fluid, clamp) — nilai tetap sama, hanya nama font di komentar yang diperbarui:**

```css
--t-display:  clamp(2.75rem, 6.5vw, 4.5rem);   /* H1 hero — Vascomm Sans 700, ls -0.03em, lh 1.05 */
--t-h2:       clamp(2rem, 4vw, 3rem);          /* judul section — Vascomm Sans 600, ls -0.02em, lh 1.15 */
--t-h3:       clamp(1.375rem, 2vw, 1.75rem);   /* judul kartu — Vascomm Sans 600, ls -0.01em, lh 1.25 */
--t-lead:     clamp(1.0625rem, 1.5vw, 1.25rem);/* paragraf hero — Vascomm Sans 400, lh 1.6 */
--t-body:     1rem;                            /* Vascomm Sans 400, lh 1.7 */
--t-sm:       0.875rem;                        /* Vascomm Sans 400, lh 1.6 */
--t-eyebrow:  0.75rem;                         /* JetBrains Mono 500, ls 0.12em, UPPERCASE */
```

**Aturan tipografi:**
- Heading selalu **sentence case**, tidak pernah Title Case. ⚠️ Ini **penyimpangan disengaja** dari induk yang mayoritas Title Case — alasan dan opsi pembatalannya di §2.3.
- Uppercase hanya untuk eyebrow mono. Tidak untuk yang lain.
- **Highlight headline:** dua kata kunci pada H1 hero dibungkus `<mark>` berlatar `--signal`, `--r-pill`, teks `--ink`. Ini perangkat warisan induk (§2.2a) dan satu-satunya tempat H1 memakai warna latar.
- Panjang baris paragraf maksimal **68 karakter** (`max-width: 62ch`).
- Tracking negatif hanya pada display dan H2. Body selalu `0`.

### 4.3 Spasi

Basis 8px. Tidak ada nilai di luar skala ini.

```css
--s-1: 8px;   --s-2: 16px;  --s-3: 24px;  --s-4: 32px;
--s-5: 48px;  --s-6: 64px;  --s-7: 96px;  --s-8: 128px;
```

- Jarak antar-section: `--s-7` (96px) desktop, `--s-6` (64px) di bawah 768px.
- Padding dalam kartu: `--s-4` (32px) desktop, `--s-3` (24px) mobile.
- Container: `max-width: 1200px`, padding samping `--s-3`.
- Grid: 12 kolom, gutter `--s-3`.

### 4.4 Radius — inilah identitasnya

```css
--r-pill: 999px;  /* tombol, chip, eyebrow, badge, avatar — SEMUA elemen kecil */
--r-card: 24px;   /* kartu, panel, gambar */
--r-in:   12px;   /* input, tile kecil di dalam kartu */
```

**Tidak ada `border-radius: 0`. Tidak ada `4px`. Tidak ada `8px`.**

Situs induk memakai `0/3px/5px`. Kontras inilah yang membedakan anak dari induk secara instan, dan kontras ini punya alasan: bentuk logonya memang begitu.

### 4.5 Elevasi

Bayangan berwarna, bukan hitam transparan. Rona biru menjaga seluruh halaman terasa berada di dalam palet.

```css
--sh-1: 0 1px 2px rgba(16, 23, 40, .06),  0 2px 8px rgba(46, 111, 212, .05);
--sh-2: 0 4px 12px rgba(16, 23, 40, .07), 0 12px 28px rgba(46, 111, 212, .08);
--sh-3: 0 8px 24px rgba(16, 23, 40, .09), 0 24px 56px rgba(46, 111, 212, .12);
```

Kartu diam di `--sh-1`, hover naik ke `--sh-2`. `--sh-3` hanya untuk elemen mengambang (header saat scroll).

### 4.6 Motion

```css
--ease: cubic-bezier(.22, 1, .36, 1);   /* ease-out tegas, terasa mekanis-presisi */
--dur-fast: 160ms;   /* hover, focus */
--dur-mid:  320ms;   /* reveal, transisi kartu */
--dur-slow: 640ms;   /* stroke-draw logo, path rail */
```

Satu momen terkoreografi saja, di hero — bukan efek yang tersebar:

1. `0ms` — mark VDA menggambar dirinya sendiri (`stroke-dashoffset` → 0, `--dur-slow`).
2. `180ms` — headline naik + fade (`translateY(16px)` → 0, `--dur-mid`).
3. `300ms` — paragraf pendukung, transisi sama.
4. `420ms` — tombol CTA.

Setelah hero, motion hanya: path rail produk yang menggambar saat scroll (§6), dan hover kartu. Tidak ada yang lain.

**Wajib:**
```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: .01ms !important;
    transition-duration: .01ms !important;
  }
  /* path rail langsung tergambar penuh, bukan animasi */
}
```

---

## 5. Sistem Komponen

**Tombol**
- Primer: bg `--vda-blue`, teks putih, `--r-pill`, padding `14px 28px`, Inter 600, `--t-body`. Hover: `--vda-indigo` + naik 2px. Focus: outline `2px solid var(--vda-blue)`, offset `2px`.
- Sekunder: bg transparan, border `1.5px solid var(--line)`, teks `--ink`. Hover: border `--vda-blue`, teks `--vda-blue`.
- Tersier / link produk: teks `--vda-blue` + panah `→` yang bergeser 4px saat hover.
- Kuning: bg `--signal`, teks `--ink`. **Hanya** untuk tombol di band CTA penutup.
- **Ikon di depan label** pada tombol primer dan kuning — mewarisi kebiasaan induk (§2.2d). Glyph monoline 18px, `stroke-linecap: round`, jarak `--s-1`. Tombol sekunder dan tersier tanpa ikon.
- Tinggi sentuh minimum **44px** di semua ukuran layar.

**Eyebrow**
Teks mono uppercase `--t-eyebrow`, warna `--vda-blue`, didahului titik 6px `--r-pill` berwarna sama, jarak `--s-1`.
⚠️ Penyimpangan disengaja: eyebrow induk kecil, abu, Title Case, tanpa penanda (§2.3).

**Chip lineage**
`--r-pill`, bg `rgba(0,126,255,.08)`, border `1px solid rgba(0,126,255,.2)`, teks `--vascomm-blue`, `--t-sm`. Isi: mark Vascomm 16px + "Anak perusahaan Vascomm". Satu-satunya tempat `--vascomm-blue` muncul selain footer.

**Kartu produk** — lihat §7 untuk anatominya.

**Band CTA gradient** *(revisi — menggantikan "band gelap" di versi pertama)*
Full-bleed `--grad-vda` arah `135deg`, radius `--r-card` pada kedua sudut atas kalau tidak menempel viewport. Teks `--on-grad`. Tombol kuning pill di dalamnya. Mewarisi perangkat induk (§2.2b), tapi gradientnya milik VDA dan tombolnya membulat penuh.

**Ikon**
Satu bahasa saja: **glyph monoline** stroke 1.5px, `stroke-linecap: round`, ujung membulat, di dalam chip `--r-pill` berlatar `--vda-blue` opacity 8%.
❌ **Dilarang:** ikon ilustratif gaya stock (tangan memegang bintang, jari menekan slider, bohlam) seperti yang dipakai induk di section "Our Unique Value". Gayanya tidak konsisten dengan ikon glyph-dalam-kotak-biru yang dipakai induk di halaman lain, dan keduanya membuat brand terasa tidak dikelola. VDA pilih satu dan pegang.

**Foto**
Mask lingkaran atau `--r-card`, tidak pernah persegi bersudut tajam — mewarisi induk (§2.2c). Color grading condong biru supaya menyatu dengan palet. Foto tim asli lebih baik daripada stock; kalau belum ada, lebih baik tidak memakai foto sama sekali daripada memakai stock generik.

---

## 6. Elemen Tanda Tangan: "Rail Produk"

Ini satu hal yang membuat halaman ini diingat. Semua elemen lain dijaga tenang agar ini menonjol.

Empat produk VDA **bukan menu berisi empat ubin setara** — mereka rantai yang menutup satu siklus operasional bisnis:

```
DIVA          →  TalentGo      →  KelolaHR      →  Sitamoto
bangun brand     rekrut orang     kelola orang     otomasi kerjanya
```

Urutan itu membawa informasi. Maka section produk tidak digambar sebagai grid 2×2, melainkan sebagai **satu goresan membulat yang mengalir dari kartu ke kartu** — SVG path dengan tebal stroke dan radius sudut yang sama persis dengan mark VDA, diisi `--grad-vda`, menggambar dirinya sendiri saat pengguna men-scroll masuk.

Goresan itu tidak menghubungkan kartu dengan garis lurus. Ia **melengkung dan melipat** di antara kartu, mengulang gerakan loop pada logo. Di akhir kartu keempat, goresan itu berbelok kembali ke atas — siklusnya menutup.

```
        ╭──────────────╮
   ╭────┤   DIVA       │
   │    ╰──────────────╯
   │            ╰──────╮
   │    ╭──────────────┴╮
   ╰────┤   TalentGo    │
        ╰───────────────╯
                ╰───────╮
        ╭───────────────┴╮
   ╭────┤   KelolaHR     │
   │    ╰────────────────╯
   │            ╰────────╮
   │    ╭────────────────┴╮
   ╰────┤   Sitamoto      │
        ╰─────────────────╯
                ╰──── kembali ke atas
```

**Alasan ini bukan gimmick:** bentuknya diturunkan langsung dari logo, dan urutannya mengkodekan fakta nyata tentang produk. Kalau urutan produk diacak, gambarnya jadi bohong — itu tanda struktur ini benar-benar membawa informasi.

**Implementasi:** SVG path tunggal, `stroke-linecap: round`, `stroke-linejoin: round`, `stroke-width: 3`, `stroke: url(#gradVda)`. Animasi via `stroke-dasharray` + `stroke-dashoffset` yang dikendalikan `IntersectionObserver`.

**Fallback di bawah 768px:** rail berubah jadi garis vertikal lurus tunggal di sisi kiri dengan titik `--r-pill` di setiap kartu. Lekukan hilang, gradient dan ritme tetap.

**Fallback jika waktu produksi tidak cukup:** grid 2×2 kartu produk, tapi urutan kartu tetap DIVA → TalentGo → KelolaHR → Sitamoto, dan di atas grid ditambahkan satu baris kecil yang menjelaskan siklusnya. Informasinya tetap sampai, tanda tangannya hilang. Ini kompromi yang sadar, bukan default.

---

## 7. Menangani Empat Brand yang Bertabrakan

Teal pekat, pink, turquoise, dan biru dalam satu section akan berantakan kalau dibiarkan. Aturannya:

**Kartu produk seragam dan netral. Warna brand hanya hadir dalam tiga cara, semuanya kecil:**

1. Garis `3px` di tepi atas kartu, `--r-pill`, lebar `40%`. Saat hover melebar jadi `100%` (`--dur-mid`).
2. Ikon produk diberi tint warna brand pada latar `8%` opacity, bentuk `--r-pill`.
3. Panah `→` pada link keluar mengambil warna brand saat hover.

Selebihnya — background, teks, border, tipografi — identik untuk keempat kartu.

**Anatomi kartu:**

```
┌────────────────────────────────────────────┐
│ ━━━━━━━                       ← rule 3px, warna brand
│                                            │
│  ⬤  KelolaHR                 [HRIS]        │  Sora 600 + chip mono
│                                            │
│  HRIS lengkap dengan absensi geolocation   │  Inter 400
│  dan face recognition lewat aplikasi       │  maks 2 baris
│  Android dan iOS.                          │
│                                            │
│  Absensi GPS · Face recognition · Payroll  │  chip pill, --t-sm
│                                            │
│  kelolahr.id                          →    │  JetBrains Mono
└────────────────────────────────────────────┘
```

Domain produk ditulis dengan mono di kaki kartu, berfungsi sebagai link keluar. Pengunjung langsung tahu ini akan membawanya ke situs lain — jujur dan berguna.

**Semua link produk:** `target="_blank"` + `rel="noopener noreferrer"`, dengan ikon external-link kecil agar tidak mengejutkan.

---

## 8. Arsitektur Halaman

```
┌──────────────────────────────────────────────────────────────┐
│ HEADER — sticky, blur, translucent                           │
│ [mark VDA] Vascomm Digital Asia    Tentang Produk Kontak [CTA]│
├──────────────────────────────────────────────────────────────┤
│                                                              │
│ HERO                                        [ mark VDA       │
│ ( Anak perusahaan Vascomm )  ← chip lineage   menggambar     │
│                                               dirinya,       │
│ ( Siap pakai ),                ← highlight    ukuran besar,  │
│ cepat ( berdampak ).             pill kuning  gradient )     │
│                                                              │
│ VDA menghadirkan produk software dan solusi                  │
│ AI yang sudah teruji...                                      │
│                                                              │
│ [ ⊳ Lihat produk kami ]  [ Hubungi tim ]                     │
├──────────────────────────────────────────────────────────────┤
│ TENTANG — bg --paper-tint                                    │
│ TENTANG VDA                                                  │
│ Produk jadi, bukan proyek dari nol.                          │
│ [3 kolom: Siap pakai · Ditenagai AI · Ditopang Vascomm]      │
├──────────────────────────────────────────────────────────────┤
│ PRODUK — bg --paper  ★ SECTION TANDA TANGAN (rail, §6)       │
│ EMPAT PRODUK, SATU SIKLUS                                    │
│ Dari membangun brand sampai mengotomasi operasional.         │
│ [DIVA] → [TalentGo] → [KelolaHR] → [Sitamoto]                │
├──────────────────────────────────────────────────────────────┤
│ KENAPA VDA — bg --paper-tint                                 │
│ [4 poin, layout selang-seling, tanpa ikon generik]           │
├──────────────────────────────────────────────────────────────┤
│ CARA MULAI — 3 langkah (mengikuti pola "3 Simple Steps"      │
│ milik induk — sinyal keluarga yang disengaja)                │
├──────────────────────────────────────────────────────────────┤
│ CTA — band --grad-vda full-bleed, tombol pill KUNING         │
│ Belum yakin mulai dari mana?                                 │
│ [ ✎ Hubungi kami ]  [ vascomm.co.id ]                        │
├──────────────────────────────────────────────────────────────┤
│ FOOTER — struktur mengikuti induk: Link · Kontak · Alamat    │
│ "PT Vascomm Digital Asia — bagian dari PT Vascomm Solusi     │
│  Teknologi"  ← lineage ditegaskan sekali lagi                │
└──────────────────────────────────────────────────────────────┘
```

**Catatan struktural:**
- **Band berwarna hanya satu** (CTA, `--grad-vda`). Footer tetap terang, seperti induk. Ini menjaga band CTA punya bobot.
- **Judul section rata tengah, blok konten selang-seling kiri/kanan** — persis ritme induk (judul "Our Unique Value" dan "Tiga Langkah Mudah" rata tengah; blok "Transformasi Digital", "Kolaborasi Untuk Inovasi", dan "Mengoptimalkan Teknologi" dua kolom bergantian). Ritme ini diwarisi apa adanya.
- **Hero dua kolom, bukan rata tengah.** Ini penyimpangan sadar: hero induk rata tengah dan meninggalkan rongga kosong besar di bawah tombol. Kolom kanan VDA diisi mark yang menggambar dirinya, jadi tidak ada ruang mati. Di bawah 1024px hero bertumpuk dan otomatis jadi rata tengah — jadi versi mobilnya justru kembali seirama dengan induk.
- Section produk mendapat ruang paling besar — ia yang mengerjakan tujuan halaman.
- Chip lineage muncul dua kali: hero dan footer. Cukup untuk membangun kredibilitas tanpa terkesan menempel pada induk.
- **Footer mengikuti struktur induk:** logo di kiri; kolom "Link" dan "Kontak" dengan judul berwarna `--vascomm-blue`; baris kontak berawalan ikon kecil (WhatsApp, telepon, email, lokasi); ikon sosial di kanan. Baris tipis "We Build Our Solutions With ❤️" di atas footer boleh dipertahankan sebagai sinyal keluarga.

---

## 9. Draft Copy

Nada: mengikuti induk — profesional, hangat, bahasa Indonesia dengan istilah teknis Inggris seperlunya. Eyebrow bahasa Inggris, headline bahasa Indonesia, sentence case.

**Hero**
> `( Anak perusahaan Vascomm )`
> # Produk 〈siap pakai〉, dampak 〈lebih cepat〉.
> VDA menghadirkan produk software dan solusi AI yang sudah teruji — mulai dari HR, branding, otomasi, sampai talenta IT. Bisnis Anda tidak perlu membangun semuanya dari nol.
> `[ ⊳ Lihat produk kami ]` `[ Hubungi tim ]`

`〈 〉` = **highlight pill kuning** (§2.2a). Ini pemakaian utama `--signal`.

*Kenapa kalimat ini:* strukturnya menyalin persis irama headline induk — `[kata benda] + [frasa di-highlight]`, dua kali. Induk: "Bisnis 〈Optimal〉, Hasil 〈Maksimal〉". VDA: "Produk 〈siap pakai〉, dampak 〈lebih cepat〉". Bedanya, induk menjanjikan sifat ("optimal", "maksimal") sedangkan VDA menjanjikan kondisi yang bisa diverifikasi ("siap pakai", "lebih cepat") — sesuai posisinya sebagai penjual produk, bukan penjual jasa.

*Alternatif lebih pendek kalau hero terasa sesak:* "〈Siap pakai〉, cepat 〈berdampak〉."

**Tentang**
> `TENTANG VDA`
> ## Produk jadi, bukan proyek dari nol.
> PT Vascomm Digital Asia adalah anak perusahaan PT Vascomm Solusi Teknologi. Kalau Vascomm membangun sistem sesuai pesanan, VDA mengemas apa yang sudah terbukti jadi produk yang bisa langsung Anda pakai.
>
> **Siap pakai** — Produk sudah berjalan di pelanggan. Anda mulai dari hari pertama, bukan dari dokumen kebutuhan.
> **Ditenagai AI** — Otomasi dan analitik yang benar-benar dipakai sehari-hari, bukan sekadar label.
> **Ditopang Vascomm** — Rekam jejak membangun sistem perbankan dan enterprise sejak 2016.

**Produk**
> `EMPAT PRODUK, SATU SIKLUS`
> ## Dari membangun brand sampai mengotomasi operasional.
> Setiap produk berdiri sendiri. Dipakai bersama, keempatnya menutup satu siklus operasional bisnis Anda.

| Produk | Kategori | Deskripsi kartu | Chip fitur |
|---|---|---|---|
| **DIVA** | Branding & Digital Marketing | Agensi branding dan digital marketing. Dari website company profile sampai pengelolaan media sosial perusahaan dan produk Anda. | Website · Branding · Social media |
| **TalentGo** | Talent Outsourcing | Penyedia talenta IT dan AI Engineer untuk perusahaan yang butuh menambah kapasitas tim tanpa proses rekrutmen panjang. | Outsource · Sharing talent · Talent squad |
| **KelolaHR** | HRIS | HRIS dengan absensi geolocation dan face recognition lewat aplikasi Android dan iOS. Payroll, cuti, dan administrasi dalam satu tempat. | Absensi GPS · Face recognition · Payroll |
| **Sitamoto** | AI Products & Consulting | Produk bertenaga AI dan konsultan implementasinya. CRM dan chatbot yang bekerja di kanal yang sudah dipakai pelanggan Anda. | CRM · Chatbot · Konsultasi AI |

**Cara mulai**
> `3 SIMPLE STEPS`
> ## Tiga langkah untuk mulai.
> 1. **Pilih produknya** — Kunjungi situs produk yang paling dekat dengan kebutuhan Anda.
> 2. **Coba dan diskusikan** — Tim kami bantu menyesuaikan dengan proses yang sudah berjalan.
> 3. **Jalankan** — Implementasi dalam hitungan hari, bukan bulan.

**CTA** — di atas band `--grad-vda`, teks putih
> ## Belum yakin mulai dari mana?
> Ceritakan kebutuhan Anda. Kami bantu petakan produk mana yang paling masuk akal untuk bisnis Anda.
> `[ ✎ Ceritakan kebutuhan Anda ]` ← pill kuning  `[ Kunjungi vascomm.co.id ]` ← pill garis putih

*Label "Ceritakan kebutuhan Anda" diambil apa adanya dari induk. Pengunjung yang datang dari vascomm.co.id akan mengenalinya.*

---

## 10. Quality Floor

Wajib dipenuhi, tanpa perlu diumumkan di halaman.

**Aksesibilitas**
- Kontras teks minimum 4.5:1 — `--ink-body` (`#4A5468`) di atas putih mencapai 8.1:1. Jangan turunkan.
- Focus ring terlihat di semua elemen interaktif: `outline: 2px solid var(--vda-blue); outline-offset: 2px`.
- Urutan heading semantik: satu `<h1>`, lalu `<h2>` per section. Tidak ada lompatan level.
- Target sentuh minimum 44×44px.
- Setiap logo produk punya `alt` deskriptif; mark dekoratif diberi `aria-hidden="true"`.
- SVG rail diberi `aria-hidden="true"` — murni dekoratif, informasinya sudah ada di urutan DOM kartu.

**Responsif**
- Breakpoint: `768px`, `1024px`. Tidak lebih dari dua.
- Hero: dua kolom di ≥1024px, satu kolom bertumpuk di bawahnya. Mark logo mengecil, tidak dihilangkan.
- Rail produk: berlekuk di ≥768px, lurus di bawahnya.
- Uji sampai lebar 360px.

**Performa**
- Font di-subset ke `latin`, `font-display: swap`, preload hanya bobot yang benar-benar dipakai (Sora 600/700, Inter 400/500/600, JetBrains Mono 500).
- Mark logo sebagai SVG inline, bukan `<img>` — perlu di-animasikan.
- Logo produk sebagai SVG. Kalau hanya tersedia PNG, sediakan `@2x` dan `loading="lazy"`.
- Target: tanpa framework. HTML + CSS + JavaScript vanilla sudah cukup untuk halaman ini.

**Cacat situs induk yang tidak boleh terulang** *(terlihat dari screenshot)*
- **Header sticky menabrak konten.** Di salah satu band CTA induk, teks dan tombol tumpang tindih dengan navigasi. Penyebab lazimnya section yang dituju anchor tidak diberi `scroll-margin-top`, dan/atau header tidak punya `background` solid saat sudah ter-scroll. Wajib: `scroll-margin-top: calc(var(--header-h) + var(--s-3))` pada setiap target anchor, `z-index` header di atas semua section, dan header memakai `backdrop-filter: blur()` + latar solid semi-transparan begitu `scrollY > 0`.
- **Hero berongga.** Hero induk rata tengah lalu menyisakan ruang kosong besar sebelum konten berikutnya. Hero VDA harus terisi penuh sampai batas viewport, atau tingginya dikurangi. Jangan pakai `min-height: 100vh` kalau isinya tidak sampai memenuhi.
- **Latar hero yang terlalu pudar.** Kolase screenshot aplikasi di hero induk begitu transparan sampai hanya terbaca sebagai noda abu. Kalau elemen latar tidak terbaca, hapus — jangan diturunkan opacity-nya lagi.
- **Dua bahasa ikon dalam satu situs.** Lihat §5.

---

## 11. Yang Perlu Diputuskan Sebelum Eksekusi

Ini tidak memblokir — saya bisa mulai membangun dengan asumsi di kolom kanan, tapi kalau ada jawabannya, hasilnya lebih tepat.

| Pertanyaan | Asumsi kalau tidak dijawab |
|---|---|
| **File logo VDA** — ada versi SVG/AI? Ada varian horizontal (mark + wordmark)? | Saya trace ulang mark dari PNG jadi SVG, dan set wordmark "Vascomm Digital Asia" dengan Sora 600. Warna pakai estimasi di §4.1. |
| **Target akhir: WordPress/Elementor atau halaman statis?** URL-nya `vascomm.co.id/vda`? | Bangun sebagai HTML + CSS + JS statis dulu (folder `lp-vda` mengarah ke sini). Porting ke WordPress belakangan kalau perlu. |
| **Logo empat produk** — ada file resminya? | Pakai monogram huruf pertama di dalam bentuk pill, ditint warna brand masing-masing. |
| **Kontak VDA** — nomor/email sendiri atau pakai milik Vascomm? | Pakai kontak Vascomm: `hello@vascomm.co.id`, WA `+62 811 3304 455`, alamat Sidoarjo. |
| **Bahasa** — Indonesia saja, atau perlu ID/EN? | Indonesia saja. Catatan: Sitamoto berbahasa Inggris penuh, jadi ada lompatan bahasa saat pengunjung mengklik keluar. |
| **Angka pendukung** — ada jumlah klien/pengguna VDA yang boleh ditampilkan? | Tidak menampilkan statistik. Lebih baik kosong daripada mengarang angka. |
| **Title Case atau sentence case?** Induk mayoritas Title Case; saya usulkan sentence case (§2.3) | Pakai sentence case. Kalau kamu lebih mengutamakan keseragaman dengan induk, cukup bilang — dua aturan berubah, sisanya tidak. |
| **Font heading induk yang sebenarnya apa?** CSS memuat lima keluarga; yang tampil terbaca seperti Rubik | Tidak menyamakan font dengan induk. VDA pakai Sora (§4.2). Perbedaan font justru membantu memisahkan anak dari induk. |

---

## 12. Cek Anti-Generik

Sebelum menulis kode, setiap keputusan diuji: "apakah ini yang akan saya hasilkan untuk profil anak perusahaan B2B mana pun?"

| Keputusan | Kenapa spesifik untuk brief ini |
|---|---|
| Radius sebagai identitas | Diturunkan dari perbedaan nyata antara mark Vascomm (bersudut) dan mark VDA (membulat). Tidak bisa dipindah ke brand lain. |
| Sora sebagai display | Konstruksi hurufnya lingkaran-dan-stadium, primitif yang sama dengan logo VDA. |
| Mono untuk domain produk | Halaman ini tugasnya mengirim orang ke empat situs lain. Domain adalah kontennya, bukan hiasan. |
| Rail produk, bukan grid | Urutan keempat produk membawa informasi nyata (siklus operasional). Diacak, gambarnya jadi salah. |
| Palet dari gradient logo | Bukan dari CSS situs induk, yang gradient biru→ungunya tidak merepresentasikan brand mana pun. |
| Warna brand produk direm ketat | Menjawab masalah nyata: teal + pink + turquoise + biru dalam satu section. |
| Highlight kuning berbentuk pill | Perangkat tipografis milik induk, dipertahankan, hanya radiusnya dibalik. Tesis §1 tersampaikan di elemen pertama yang dilihat orang. |
| Band CTA gradient + tombol kuning | Diambil dari perilaku induk, bukan dari kebiasaan saya. Lihat catatan koreksi di bawah. |

**Koreksi yang lahir dari screenshot.** Versi pertama dokumen ini menetapkan band CTA berlatar **navy hampir hitam** (`#0D1424`). Setelah melihat tampilan jadi induk, itu keputusan yang salah — dan tepat salah satu default yang seharusnya saya hindari: "latar nyaris hitam dengan satu aksen terang". Induk sudah punya jawabannya sendiri (gradient biru + tombol kuning), yang lebih khas dan lebih menyambung. Band gelapnya dibatalkan.

**Yang sengaja dihindari:** background krem dengan serif kontras tinggi dan aksen terracotta; latar hitam dengan satu aksen hijau-asam; layout ala koran dengan garis rambut dan radius nol. Ketiganya adalah default, bukan pilihan — dan tidak satu pun cocok untuk perusahaan software Indonesia yang menjual produk siap pakai.

**Satu risiko yang diambil:** rail produk berlekuk. Kalau produksinya terlalu berat, fallback di §6 tersedia dan sudah dipikirkan.

---

*Berikutnya: eksekusi halaman berdasarkan dokumen ini.*
