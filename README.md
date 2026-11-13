# Excel Toolkit

Alat bantu untuk tes Excel (tes kerja, ujian, tugas). Pilih alat, isi kolom dengan alamat sel dari datamu, lalu rumus langsung jadi dan tinggal disalin. Setiap alat dilengkapi langkah pemakaian.

## Cara pakai

1. Buka `index.html` di browser (klik dua kali, tidak perlu internet atau instalasi).
2. Pilih alat di daftar kiri, atau cari lewat kolom pencarian.
3. Isi kolom dengan alamat sel/nilai dari datamu. Klik **Isi contoh** untuk melihat bentuk isiannya.
4. Klik **Salin rumus**, lalu di Excel klik sel hasil, tekan `Ctrl + V`, dan `Enter`.
5. Untuk baris lain, tarik kotak kecil di pojok kanan bawah sel ke bawah.

Kalau Excel menolak rumus dengan koma, ubah **Pemisah rumus** di bagian atas ke titik koma. Ini umum terjadi di Excel dengan pengaturan regional Indonesia.

## Isi toolkit (32 alat)

**Hitung & Agregasi**: SUM, SUMIF, SUMIFS, COUNTIF, COUNTIFS, AVERAGEIF, RANK, ROUND, persentase

**Logika & Kondisi**: IF, IF dengan DAN/ATAU, IFS bertingkat, IFERROR

**Lookup**: VLOOKUP, XLOOKUP, INDEX + MATCH

**Teks**: LEFT/RIGHT, MID, TEXTJOIN, TRIM/PROPER/UPPER/LOWER

**Tanggal**: DATEDIF (umur), TEXT (format tanggal), NETWORKDAYS

**Panduan klik (tanpa rumus)**: Pivot Table, Conditional Formatting, Dropdown (Data Validation), hapus data ganda, Text to Columns, Freeze Panes, Filter & Urutkan, Flash Fill, jadikan Tabel

## Panduan lengkap

Penjelasan lebih dalam, contoh soal, dan jawabannya ada di file berikut:

- [01 Fungsi dasar dan agregasi](01-fungsi-dasar-dan-agregasi.md)
- [02 Logika dan kondisi](02-logika-dan-kondisi.md)
- [03 Lookup dan referensi](03-lookup-dan-referensi.md)
- [04 Teks, tanggal, waktu](04-teks-tanggal-waktu.md)
- [05 Pivot, grafik, alat data](05-pivot-grafik-alat-data.md)
- [06 Shortcut Excel](06-shortcut-excel.md)
- [07 Error dan troubleshooting](07-error-dan-troubleshooting.md)
- [08 Contoh soal dan jawaban](08-contoh-soal-dan-jawaban.md)

## Catatan

- Beberapa fungsi (XLOOKUP, IFS, TEXTJOIN) hanya ada di Excel 2019/365. Di versi lama, pakai VLOOKUP atau IF bertumpuk.
- Kode format tanggal pada alat TEXT bisa berbeda di Excel berbahasa Indonesia. Kalau hasilnya aneh, coba huruf lokal (mis. `hh/bb/tttt`).
- Toolkit ini hanya membuatkan teks rumus. Datamu tidak dikirim ke mana pun.
