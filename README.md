# mazid-docs — Dokumentasi Resmi Platform Mazid

Repo ini berisi sumber dokumentasi resmi [Mazid](https://mazid.id), dibangun dengan [Mintlify](https://mintlify.com).

**Live:** https://panduan.mazid.id

## Tentang Mazid

**Mazid** adalah platform SaaS untuk lembaga pendidikan di Indonesia. Tagline: *"Beyond administration."*

Satu platform melayani ratusan lembaga dengan isolasi data penuh melalui PostgreSQL Row Level Security (RLS).

### Modul Utama

- **SPP & Keuangan** — tagihan, pembayaran, kode unik otomatis, tabungan santri
- **Santri** — biodata, wali, NIS, kelas
- **Presensi** — sesi kehadiran harian
- **Hafalan** — target dan pencapaian hafalan Quran
- **Perizinan** — pengajuan izin keluar/pulang
- **Pelanggaran** — catatan disiplin dan sanksi
- **PPDB** — penerimaan peserta didik baru (pendaftaran online tanpa login)
- **Laporan** — ringkasan keuangan dan aktivitas
- **Subscription** — paket Free, Basic, Pro, Enterprise

### Audiens Dokumentasi

1. **Admin Pesantren** — mengoperasikan platform sehari-hari
2. **Orang Tua / Wali Santri** — menggunakan portal publik
3. **Developer / Tim Teknis** — referensi API dan integrasi

---

## Development

### Instalasi

Install Mintlify CLI (cukup sekali):

```bash
npm i -g mintlify
```

### Preview Lokal

Jalankan di root repo (tempat `docs.json` berada):

```bash
mintlify dev
```

Preview tersedia di `http://localhost:3000`.

### Troubleshooting

- Jika env dev tidak berjalan: jalankan `mintlify update` untuk update ke versi terbaru
- Jika halaman 404: pastikan ada file `docs.json` di root folder

---

## Deploy

Perubahan di-deploy otomatis ke **https://panduan.mazid.id** setelah push ke branch `main` (1–2 menit).

### GitHub Integration

Pastikan Mintlify GitHub App sudah terpasang di [dashboard](https://dashboard.mintlify.com/settings/organization/github-app).

### Konvensi Commit Message

```bash
# Menambah konten baru
docs: tambah panduan presensi

# Memperbaiki konten
docs: update alur PPDB fase 2

# Memperbaiki link atau error teknis
fix: perbaiki broken link di halaman SPP

# Konfigurasi atau metadata
chore: update navigasi docs.json
```

---

## Struktur Repo

```
mazid-docs/
├── docs.json                 ← Konfigurasi Mintlify (navigasi, tema, warna, dll)
├── README.md                 ← File ini
├── favicon.svg
├── logo/                     ← Logo light/dark
├── pengantar.mdx             ← Homepage docs ("Apa Itu Mazid?")
├── mulai-cepat.mdx           ← Onboarding 5 menit untuk admin
├── panduan-admin/            ← Panduan lengkap Admin Lembaga
├── ppdb/                     ← Modul PPDB (pendaftaran online)
├── portal-ortu/              ← Panduan Portal Orang Tua / Wali
├── subscription/             ← Paket & billing Mazid
├── api-reference/            ← (Dikembangkan belakangan)
└── snippets/                 ← Konten reusable antar halaman
```

---

## Kontribusi & Editing

### Hal yang Wajib Diikuti

1. **Bahasa:** Gunakan Bahasa Indonesia yang formal namun santai
2. **Terminologi:** Konsisten dengan istilah domain Mazid (lihat `AGENTS.md` untuk daftar lengkap)
   - `santri` bukan `siswa`
   - `lembaga` bukan `sekolah`
   - `kode unik` bukan `kode pembayaran`
3. **Format Halaman:** Setiap file `.mdx` wajib dimulai dengan frontmatter:
   ```mdx
   ---
   title: "Judul Halaman"
   description: "Deskripsi singkat satu kalimat."
   ---
   ```

4. **Komponen:** Gunakan komponen Mintlify (`<Note>`, `<Warning>`, `<Tip>`, `<Steps>`, dll) untuk clarity

Baca **`AGENTS.md`** di root repo untuk konvensi lengkap dan petunjuk detail.

### Validasi

```bash
# Cek broken links sebelum push
mintlify broken-links
```

---

## Link & Referensi

- **Website Mazid:** https://mazid.id
- **Dokumentasi Live:** https://panduan.mazid.id
- **Dashboard App:** https://dashboard.mazid.id
- **Email:** hello@mazid.id
- **Mintlify Docs:** https://mintlify.com/docs
- **Repo Konteks:** Baca `AGENTS.md` untuk spesifikasi lengkap proyek

---

## Lisensi

Lihat file `LICENSE` untuk detail lisensi.
