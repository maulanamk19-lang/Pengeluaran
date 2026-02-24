# Panduan Deploy Buku Kas Rumah Tangga dengan Google Sheets

## Langkah 1: Setup Google Spreadsheet

1. **Buat Google Spreadsheet baru**
   - Buka https://sheets.google.com
   - Klik "Blank" untuk membuat spreadsheet baru
   - Beri nama: "Buku Kas Rumah Tangga"

2. **Setup Header (Opsional)**
   - Di baris pertama, masukkan header: Tanggal | Kategori | Keterangan | Jumlah | Timestamp
   - Atau biarkan kosong, script akan otomatis membuat header

## Langkah 2: Setup Google Apps Script

1. **Buka Apps Script Editor**
   - Di Google Spreadsheet, klik menu "Extensions" > "Apps Script"
   - Hapus kode default yang ada

2. **Paste Kode Apps Script**
   - Copy seluruh kode dari file `google-apps-script.js`
   - Paste ke Apps Script Editor
   - Klik "Save" (Ctrl+S)

3. **Deploy sebagai Web App**
   - Klik tombol "Deploy" > "New deployment"
   - Di "Type", pilih "Web app"
   - Di "Description", isi: "Buku Kas API"
   - Di "Execute as", pilih "Me"
   - Di "Who has access", pilih "Anyone" 
   - Klik "Deploy"
   - **PENTING**: Copy URL yang diberikan (contoh: https://script.google.com/macros/s/ABC123.../exec)

4. **Authorize Permissions**
   - Saat pertama kali deploy, akan muncul dialog permission
   - Klik "Review permissions"
   - Pilih akun Google Anda
   - Klik "Advanced" > "Go to [Project Name] (unsafe)"
   - Klik "Allow"

## Langkah 3: Setup HTML File

1. **Edit URL di HTML**
   - Buka file `buku_kas_google_sheets.html`
   - Cari baris: `const GOOGLE_APPS_SCRIPT_URL = 'https://script.google.com/macros/s/YOUR_SCRIPT_ID/exec';`
   - Ganti `YOUR_SCRIPT_ID` dengan URL yang Anda copy dari langkah 2.3

2. **Test Lokal**
   - Buka file HTML di browser
   - Coba tambah pengeluaran baru
   - Cek apakah data masuk ke Google Spreadsheet

## Langkah 4: Deploy HTML (Pilihan)

### Opsi A: GitHub Pages (Gratis)
1. Upload file HTML ke repository GitHub
2. Enable GitHub Pages di Settings
3. Akses via URL: https://username.github.io/repository-name/

### Opsi B: Netlify (Gratis)
1. Drag & drop file HTML ke https://app.netlify.com/drop
2. Dapatkan URL otomatis

### Opsi C: Vercel (Gratis)
1. Upload ke GitHub
2. Connect repository di https://vercel.com
3. Deploy otomatis

## Troubleshooting

### Error "Script function not found"
- Pastikan fungsi `doGet` dan `doPost` ada di Apps Script
- Re-deploy Web App setelah mengubah kode

### Error CORS
- Pastikan "Who has access" di Web App deployment adalah "Anyone"
- Coba hard refresh browser (Ctrl+F5)

### Data tidak tersimpan
- Cek Console browser (F12) untuk error
- Pastikan URL Apps Script sudah benar di HTML
- Cek permission Apps Script

### Grafik tidak muncul
- Pastikan Chart.js CDN ter-load
- Cek Console untuk error JavaScript

## Fitur yang Tersedia

✅ **Form Input Lengkap**
- Tanggal, Kategori, Keterangan, Jumlah
- Auto-format angka dengan titik pemisah ribuan
- Validasi input

✅ **Integrasi Google Sheets**
- Simpan otomatis ke spreadsheet
- Load data real-time
- Fallback ke data dummy jika offline

✅ **Visualisasi Data**
- Grafik mingguan (Bar Chart)
- Grafik bulanan (Line Chart) 
- Grafik tahunan (Line Chart)

✅ **UI/UX Modern**
- Responsive design
- Loading states
- Status koneksi
- Empty states

## Keamanan & Limitasi

- **Public Access**: Web App dapat diakses siapa saja yang punya URL
- **Rate Limiting**: Google Apps Script memiliki quota harian
- **Data Size**: Cocok untuk penggunaan personal/keluarga
- **Backup**: Data tersimpan di Google Drive Anda

## Tips Penggunaan

1. **Backup Regular**: Export spreadsheet secara berkala
2. **Kategori Custom**: Edit dropdown kategori di HTML sesuai kebutuhan
3. **Multi User**: Buat copy spreadsheet untuk setiap user
4. **Mobile**: Tambahkan ke home screen untuk akses cepat
