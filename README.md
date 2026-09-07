# Web Zakat — Kalkulator, Pembayaran, Transparansi

## Isi project
- `pages/index.js` — halaman publik: total tersalurkan, kalkulator zakat, rekening + tombol WA, riwayat transparansi.
- `pages/login.js` — login bendahara.
- `pages/admin.js` — dashboard bendahara: catat transaksi (langsung tampil ke publik, tanpa approval kedua), atur data rekening & WA.
- `sql/schema.sql` — jalankan ini di Supabase SQL Editor untuk membuat tabel.

## Langkah setup (setelah upload ke GitHub & Vercel)

1. **Buat tabel di Supabase**
   Buka Supabase project kamu → menu **SQL Editor** → **New query** → tempel seluruh isi `sql/schema.sql` → klik **Run**.

2. **Buat akun bendahara pertama**
   Di Supabase, buka menu **Authentication** → **Users** → **Add user** → isi email & password bendahara. Ini akun untuk login di halaman `/login`.

3. **Sambungkan ke Vercel**
   Di Vercel, buka project → **Settings** → **Environment Variables**, tambahkan:
   - `NEXT_PUBLIC_SUPABASE_URL`
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY`

   Nilainya diambil dari Supabase: **Project Settings** → **API**. Setelah itu klik **Redeploy**.

4. **Isi data lembaga**
   Login di `/login` dengan akun bendahara → buka `/admin` → isi nama lembaga, bank, nomor rekening, dan nomor WhatsApp di form "Data Lembaga" → simpan.

5. **Mulai catat transaksi**
   Di halaman `/admin`, tiap ada zakat masuk atau tersalurkan, isi form "Catat Transaksi Baru" lalu simpan — otomatis langsung tampil di halaman publik (`/`), tidak perlu persetujuan tambahan.

## Menjalankan di komputer sendiri (opsional)
```
npm install
cp .env.local.example .env.local   # lalu isi dengan kunci Supabase kamu
npm run dev
```
Buka http://localhost:3000
