# Ayuk Hapan QRIS (MVP)

Aplikasi web full-stack untuk monitoring ekspansi QRIS pada program **PASTI SIP – Ayuk Hapan QRIS**.

## Fitur MVP
- Registrasi/login dengan role `PJP` dan `BI`.
- PJP input **Readiness Checklist** dengan SLA H+2 (`on_time` / `late`).
- Dashboard BI real-time (polling 30 detik):
  - Hero metrics.
  - Tren onboarding mingguan.
  - Tabel kepatuhan SLA per PJP.
  - Daftar keterlambatan.
- Audit trail saat checklist diedit/dihapus.
- Export data checklist ke CSV.
- Notifikasi keterlambatan (simulasi via `console.log`).

## Tech Stack
- Node.js + Express + EJS
- Prisma ORM + SQLite
- Session-based auth + bcrypt hash
- Chart.js untuk grafik

## Menjalankan Lokal
1. Install dependency:
   ```bash
   npm install
   ```
2. Siapkan database:
   ```bash
   npm run db:push
   npm run db:seed
   ```
3. Jalankan server:
   ```bash
   npm run dev
   ```
4. Akses di `http://localhost:3000`.

## Akun Default
- BI:
  - email: `bi.admin@bi.go.id`
  - password: `password123`
- PJP:
  - email: `pjp.lapangan@bank.id`
  - password: `password123`

## Catatan SLA
SLA dihitung dari selisih tanggal kunjungan ke tanggal submit (`submitted_at`).
- `<= 2 hari` → `on_time`
- `> 2 hari` → `late`

## Struktur Inti
- `src/server.js`: API + auth + render halaman.
- `src/views/*`: UI halaman PJP/BI.
- `prisma/schema.prisma`: model User, Checklist, AuditLog.
