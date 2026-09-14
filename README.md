# Sehat Harian — Versi Statis (Tanpa Build)

Ini adalah versi Sehat Harian yang **tidak butuh proses build sama sekali**.
React, Tailwind, dan transpiler JSX semuanya dimuat lewat CDN langsung di
`index.html`. Cocok untuk upload langsung ke GitHub lewat web (drag & drop),
tanpa perlu `npm install`, tanpa GitHub Actions.

## Isi folder

```
index.html          ← seluruh aplikasi (HTML + React + logika)
manifest.json        ← metadata PWA
service-worker.js    ← caching offline
icons/                ← ikon PWA (sudah lengkap, semua ukuran)
```

Cukup 4 item ini. Upload semuanya persis seperti struktur di atas ke root
repo GitHub kamu (folder `icons/` harus tetap jadi folder, bukan diflatten).

## Cara upload ke GitHub (lewat web, tanpa terminal)

1. Buka repo GitHub kamu → **Add file > Upload files**.
2. Drag folder ini (index.html, manifest.json, service-worker.js, dan folder
   icons/) ke area upload. Browser modern akan mempertahankan struktur folder
   icons/ selama kamu men-drag foldernya, bukan memilih file satu-satu.
3. Commit langsung ke branch `main`.
4. Buka **Settings > Pages**.
5. Di **Build and deployment > Source**, pilih **Deploy from a branch**.
6. Pilih branch `main`, folder `/ (root)`, lalu **Save**.
7. Tunggu 1–2 menit, buka URL yang muncul (biasanya
   `https://<username>.github.io/<nama-repo>/`).

Tidak perlu GitHub Actions untuk versi ini karena tidak ada langkah build.

## Kenapa versi sebelumnya putih?

Versi sebelumnya pakai Vite + JSX yang perlu di-*build* dulu (`npm run build`)
sebelum bisa dijalankan browser — browser tidak bisa membaca file `.jsx` atau
`import react from "react"` secara langsung. Kalau file itu diupload mentah
ke GitHub Pages tanpa proses build, halaman jadi putih kosong.

Versi ini berbeda: JSX ditranspile langsung di browser oleh Babel (dimuat
lewat CDN), dan React/Tailwind juga dari CDN — jadi `index.html` bisa
langsung dibuka apa adanya, tanpa proses build apa pun.

## Data pengguna

Semua data (profil, aktivitas, pengingat) disimpan di `localStorage`
browser pengguna masing-masing — bukan di server, dan tidak dibagikan ke
pihak manapun.

## Lanjut ke PWABuilder

Setelah live di GitHub Pages:
1. Buka https://www.pwabuilder.com
2. Tempel URL GitHub Pages kamu, klik **Start**.
3. Klik **Package For Stores** untuk membuat paket Android/iOS/Windows.
