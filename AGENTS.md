# mazid-docs — Dokumentasi Resmi Platform Mazid

> File ini adalah konteks utama untuk Claude Code saat bekerja di repo `mazid-docs`.
> Baca seluruh file ini sebelum membuat atau mengedit halaman dokumentasi apapun.

---

## Tentang Proyek Ini

**Repo ini** adalah dokumentasi resmi Mazid, dibangun dengan [Mintlify](https://mintlify.com).
Dokumentasi ini ditujukan untuk tiga audiens utama:
1. **Admin Pesantren** — mengoperasikan platform sehari-hari
2. **Orang Tua / Wali Santri** — menggunakan portal publik
3. **Developer / Tim Teknis Mazid** — referensi API dan integrasi

**URL Live:** `https://docs.mazid.id`
**Repo GitHub:** `github.com/[org]/mazid-docs`
**Deploy:** Mintlify Hosted → custom domain via Cloudflare DNS (CNAME `docs` → `hosted.mintlify.com`)

---

## Tentang Produk Mazid

Platform SaaS multi-tenant untuk manajemen pesantren, madrasah, dan lembaga pendidikan Islam.
Satu platform melayani ratusan lembaga dengan isolasi data penuh via PostgreSQL RLS.

**Tagline:** "Beyond administration."
**Brand color:** `#00E5A0` (Zid Green)

### User Types yang Harus Diketahui
| Role | Akses | Tempat |
|------|-------|--------|
| Super Admin | Semua lembaga (internal Mazid) | `/super-admin` |
| Admin Lembaga | Data lembaganya sendiri | `/admin` |
| Operator | Fokus keuangan saja | `/admin` |
| Pengajar | Presensi, hafalan, santri | `/admin` |
| Orang Tua / Wali | Portal baca-saja | Portal `nama.mazid.id` |
| Santri | Portal baca-saja | Portal `nama.mazid.id` |

### Modul Platform
- **SPP & Keuangan** — tagihan, pembayaran, kode unik, tabungan
- **Santri** — biodata, wali, NIS, kelas
- **Presensi** — sesi kehadiran harian
- **Hafalan** — target dan pencapaian hafalan Quran
- **Perizinan** — pengajuan izin keluar/pulang
- **Pelanggaran** — catatan pelanggaran dan sanksi
- **PPDB** — penerimaan peserta didik baru (pendaftaran online)
- **Laporan** — ringkasan keuangan dan aktivitas
- **Subscription** — paket Free / Basic / Pro / Enterprise

### Terminologi Domain (WAJIB konsisten di semua halaman)
| Istilah | Arti | Jangan Pakai |
|---------|------|--------------|
| `lembaga` | Institusi pesantren/madrasah | "sekolah", "instansi" |
| `santri` | Siswa/peserta didik | "siswa", "murid" |
| `orang tua / wali` | Parent/guardian | "wali murid" |
| `NIS` | Nomor Induk Santri | "NISN" (berbeda) |
| `kode unik` | 3-digit suffix tagihan SPP | "kode pembayaran" |
| `tabungan` | Wallet saldo santri di platform | "dompet", "saldo" |
| `presensi` | Absensi/kehadiran | "absen" |
| `perizinan` | Izin keluar/pulang santri | "izin" saja |
| `pelanggaran` | Catatan disiplin | "kesalahan" |
| `hafalan` | Qur'an memorization progress | "tahfidz" (OK juga) |
| `PPDB` | Penerimaan Peserta Didik Baru | "pendaftaran" saja |
| `kelas` | Classroom / angkatan | "grade" |

---

## Struktur Repo

```
mazid-docs/
├── docs.json                        ← Konfigurasi utama Mintlify (navigasi, tema, dll)
├── favicon.png
├── logo/
│   ├── light.svg
│   └── dark.svg
│
├── pengantar.mdx                    ← Halaman utama (homepage docs)
├── mulai-cepat.mdx                  ← Onboarding 5 menit untuk admin baru
│
├── panduan-admin/                   ← Semua panduan untuk Admin Lembaga
│   ├── setup-awal.mdx
│   ├── manajemen-santri.mdx
│   ├── spp-dan-keuangan.mdx         ← Halaman PRIORITAS (fitur paling unik)
│   ├── presensi.mdx
│   ├── hafalan.mdx
│   ├── perizinan.mdx
│   ├── pelanggaran.mdx
│   └── laporan.mdx
│
├── ppdb/                            ← Modul PPDB
│   ├── pengantar-ppdb.mdx
│   ├── setup-formulir.mdx
│   ├── alur-pendaftar.mdx           ← Dari sudut pandang calon santri
│   └── konversi-ke-santri.mdx
│
├── portal-ortu/                     ← Panduan untuk Orang Tua / Wali
│   ├── cara-akses.mdx
│   ├── lihat-tagihan.mdx
│   └── pantau-perkembangan.mdx
│
├── subscription/                    ← Paket & billing Mazid
│   ├── paket-harga.mdx
│   └── upgrade-downgrade.mdx
│
├── api-reference/                   ← (Opsional, dikembangkan belakangan)
│   └── overview.mdx
│
└── snippets/                        ← Konten yang bisa di-reuse antar halaman
    ├── tip-kode-unik.mdx
    └── warning-rls.mdx
```

---

## Konfigurasi `docs.json` (Template)

```json
{
  "name": "Mazid",
  "logo": {
    "light": "/logo/light.svg",
    "dark": "/logo/dark.svg",
    "href": "https://mazid.id"
  },
  "favicon": "/favicon.png",
  "colors": {
    "primary": "#00E5A0",
    "light": "#00E5A0",
    "dark": "#00B87A"
  },
  "topbarLinks": [
    { "name": "Dashboard", "url": "https://dashboard.mazid.id" }
  ],
  "topbarCtaButton": {
    "name": "Daftar Gratis",
    "url": "https://mazid.id/daftar"
  },
  "anchors": [
    {
      "name": "Panduan Admin",
      "icon": "book-open",
      "url": "panduan-admin"
    },
    {
      "name": "Portal Orang Tua",
      "icon": "users",
      "url": "portal-ortu"
    },
    {
      "name": "PPDB",
      "icon": "graduation-cap",
      "url": "ppdb"
    }
  ],
  "navigation": [
    {
      "group": "Memulai",
      "pages": ["pengantar", "mulai-cepat"]
    },
    {
      "group": "Panduan Admin",
      "pages": [
        "panduan-admin/setup-awal",
        "panduan-admin/manajemen-santri",
        "panduan-admin/spp-dan-keuangan",
        "panduan-admin/presensi",
        "panduan-admin/hafalan",
        "panduan-admin/perizinan",
        "panduan-admin/pelanggaran",
        "panduan-admin/laporan"
      ]
    },
    {
      "group": "PPDB",
      "pages": [
        "ppdb/pengantar-ppdb",
        "ppdb/setup-formulir",
        "ppdb/alur-pendaftar",
        "ppdb/konversi-ke-santri"
      ]
    },
    {
      "group": "Portal Orang Tua",
      "pages": [
        "portal-ortu/cara-akses",
        "portal-ortu/lihat-tagihan",
        "portal-ortu/pantau-perkembangan"
      ]
    },
    {
      "group": "Subscription",
      "pages": [
        "subscription/paket-harga",
        "subscription/upgrade-downgrade"
      ]
    }
  ],
  "footerSocials": {
    "instagram": "https://instagram.com/mazid.id"
  },
  "feedback": {
    "thumbsRating": true,
    "suggestEdit": true
  }
}
```

---

## Konvensi Penulisan

### Bahasa
- **Bahasa Indonesia** untuk semua konten panduan user (admin, orang tua, santri)
- Bahasa yang digunakan: **formal tapi santai** — seperti berbicara ke admin pesantren yang melek teknologi
- Hindari jargon teknis yang tidak perlu (tidak perlu sebutkan "PostgreSQL", "RLS", "API" di panduan user biasa)
- Boleh pakai bahasa teknis di halaman `api-reference/` dan halaman developer

### Format Halaman `.mdx`

Setiap halaman **wajib** dimulai dengan frontmatter:

```mdx
---
title: "Judul Halaman"
description: "Deskripsi singkat satu kalimat, muncul di SEO dan card preview."
---
```

### Komponen Mintlify yang Tersedia

Gunakan komponen ini secara aktif — jangan hanya pakai plain text:

```mdx
{/* Informasi tambahan */}
<Note>Gunakan untuk catatan penting yang mendukung, tapi bukan peringatan.</Note>

{/* Peringatan */}
<Warning>Gunakan untuk hal yang bisa menyebabkan masalah jika diabaikan.</Warning>

{/* Tips berguna */}
<Tip>Gunakan untuk cara pintas atau best practice.</Tip>

{/* Informasi kontekstual */}
<Info>Gunakan untuk latar belakang atau konteks tambahan.</Info>

{/* Langkah-langkah berurutan */}
<Steps>
  <Step title="Langkah Pertama">
    Deskripsi langkah pertama.
  </Step>
  <Step title="Langkah Kedua">
    Deskripsi langkah kedua.
  </Step>
</Steps>

{/* Card link navigasi */}
<CardGroup cols={2}>
  <Card title="Judul Card" icon="icon-name" href="/path/ke/halaman">
    Deskripsi singkat card.
  </Card>
</CardGroup>

{/* Tabs untuk konten berbeda */}
<Tabs>
  <Tab title="Tab Satu">Konten tab satu.</Tab>
  <Tab title="Tab Dua">Konten tab dua.</Tab>
</Tabs>

{/* Accordion / expandable */}
<Accordion title="Pertanyaan atau topik yang bisa di-expand">
  Jawaban atau konten detail di sini.
</Accordion>
```

### Struktur Tipikal Halaman Panduan

```mdx
---
title: "Nama Fitur"
description: "Apa yang bisa dilakukan dengan fitur ini."
---

## Apa Itu [Nama Fitur]?

Satu paragraf singkat menjelaskan fitur dan manfaatnya bagi pesantren.

## Cara Menggunakan

<Steps>
  <Step title="Langkah pertama">...</Step>
  ...
</Steps>

## Hal yang Perlu Diperhatikan

<Warning>...</Warning>

## Pertanyaan Umum (FAQ)

<AccordionGroup>
  <Accordion title="Pertanyaan 1?">Jawaban 1.</Accordion>
  <Accordion title="Pertanyaan 2?">Jawaban 2.</Accordion>
</AccordionGroup>
```

---

## Halaman Prioritas & Catatan Konten

### 1. `panduan-admin/spp-dan-keuangan.mdx` ← PALING PENTING

Halaman ini harus menjelaskan **sistem kode unik** dengan sangat jelas karena ini keunikan Mazid:

- Setiap tagihan SPP mendapat **3 digit kode unik** yang ditambahkan ke nominal transfer
- Contoh: tagihan Rp 500.000 → santri transfer Rp 500.**123**
- Kelebihan (Rp 123) otomatis masuk ke **tabungan** santri
- Gunakan diagram atau tabel contoh untuk memperjelas

```mdx
<Tip>
Kode unik memungkinkan rekonsiliasi otomatis tanpa konfirmasi manual.
Admin tidak perlu cek satu per satu transfer masuk.
</Tip>
```

### 2. `ppdb/alur-pendaftar.mdx`

- Alur PPDB **tidak butuh login** — calon santri daftar via link publik
- Tracking status via **token** yang dikirim ke email/WhatsApp
- Status flow: `pending → reviewing → payment_required → ... → accepted / rejected`

### 3. `portal-ortu/cara-akses.mdx`

- Portal diakses via subdomain lembaga: `namalembaga.mazid.id`
- Login menggunakan akun yang dibuat oleh admin lembaga

### 4. `subscription/paket-harga.mdx`

- 4 paket: **Free, Basic, Pro, Enterprise**
- Harga dinamis berdasarkan jumlah santri aktif per bulan
- Fitur diatur per modul — pesantren bisa aktifkan modul a la carte

---

## Aturan Snippet (Reusable Content)

Buat snippet di folder `snippets/` untuk konten yang muncul di banyak halaman.

Contoh penggunaan:
```mdx
<Snippet file="tip-kode-unik.mdx" />
```

Snippet yang sudah direncanakan:
- `snippets/tip-kode-unik.mdx` — penjelasan singkat sistem kode unik (muncul di SPP, PPDB, dll)
- `snippets/warning-hapus-data.mdx` — peringatan standar sebelum aksi delete
- `snippets/info-multi-tenant.mdx` — penjelasan isolasi data per lembaga

---

## Perintah Berguna

```bash
# Install Mintlify CLI (sekali saja)
npm i -g mintlify

# Preview lokal di http://localhost:3000
mintlify dev

# Validasi broken links dan config
mintlify broken-links
```

---

## Alur Kerja Deploy

```
Edit file .mdx di local
    ↓
git add . && git commit -m "docs: ..."
    ↓
git push origin main
    ↓
Mintlify auto-deploy (1–2 menit)
    ↓
Live di docs.mazid.id
```

**Konvensi commit message:**
- `docs: tambah panduan presensi`
- `docs: update alur PPDB fase 2`
- `fix: perbaiki broken link di halaman SPP`
- `chore: update navigasi docs.json`

---

## Hal yang JANGAN Dilakukan

- ❌ Jangan sebutkan nama database, tabel, atau kode internal di halaman panduan user
- ❌ Jangan pakai kata "klik" — pakai "pilih" atau "tekan"
- ❌ Jangan buat halaman tanpa frontmatter `title` dan `description`
- ❌ Jangan hardcode URL `dashboard.mazid.id` sebagai contoh subdomain lembaga — pakai `namalembaga.mazid.id`
- ❌ Jangan campur istilah: pilih satu (contoh: selalu "santri", bukan ganti-ganti dengan "siswa")
- ❌ Jangan buat halaman API Reference sebelum backend API selesai dan stabil

---

## Kontak & Referensi

- **Repo utama Mazid (Laravel/Next.js):** referensi untuk fitur yang sedang dikembangkan
- **PPDB.md** di repo utama: spesifikasi lengkap modul PPDB
- **mazid-ai-implementation.html** di repo utama: roadmap fitur AI
- **Domain:** `mazid.id`, email `hello@mazid.id`
- **Mintlify Docs:** https://mintlify.com/docs