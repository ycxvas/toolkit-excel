# Contekan Excel untuk Tes Kerja

Ringkasan rumus, langkah, dan contoh soal Excel yang sering muncul di tes rekrutmen. Semua bisa dibaca langsung di GitHub tanpa mengunduh apa pun.

> Cek aturan tes dari perusahaan lebih dulu. Sebagian tes tidak membolehkan membuka referensi luar. Repositori ini dibuat untuk belajar dan latihan.

## Isi

1. [Fungsi dasar dan agregasi](01-fungsi-dasar-dan-agregasi.md): SUM, SUMIFS, COUNTIFS, persentase, referensi sel
2. [Logika dan kondisi](02-logika-dan-kondisi.md): IF, IFS, AND, OR, IFERROR
3. [Lookup dan referensi](03-lookup-dan-referensi.md): VLOOKUP, INDEX+MATCH, XLOOKUP, tabel tingkatan
4. [Teks, tanggal, dan waktu](04-teks-tanggal-waktu.md): LEFT, MID, TEXTJOIN, DATEDIF, NETWORKDAYS
5. [PivotTable, grafik, dan alat data](05-pivot-grafik-alat-data.md): pivot, filter, conditional formatting, validasi
6. [Shortcut keyboard](06-shortcut-excel.md)
7. [Error dan troubleshooting](07-error-dan-troubleshooting.md)
8. [Contoh soal dan jawaban](08-contoh-soal-dan-jawaban.md): pola soal tes beserta rumusnya

## Catatan penulisan rumus

Contoh di sini memakai **koma** sebagai pemisah argumen, misalnya `=SUMIFS(G2:G9,C2:C9,"Jakarta")`. Kalau Excel kamu memakai pengaturan regional Indonesia dan koma ditolak, ganti semua koma pemisah argumen dengan **titik koma** (`;`).

Nama fungsi juga bisa tampil dalam bahasa lain mengikuti bahasa Excel yang terpasang. Kalau muncul `#NAME?` padahal ejaan benar, lihat [troubleshooting](07-error-dan-troubleshooting.md).

## Mau apa, pakai apa

| Kebutuhan | Pakai | Contoh |
|---|---|---|
| Jumlahkan dengan satu atau lebih syarat | `SUMIFS` | `=SUMIFS(G2:G9,C2:C9,"Jakarta",D2:D9,"Laptop")` |
| Hitung banyak data dengan syarat | `COUNTIFS` | `=COUNTIFS(D2:D9,"Laptop")` |
| Rata-rata dengan syarat | `AVERAGEIFS` | `=AVERAGEIFS(G2:G9,C2:C9,"Jakarta")` |
| Ambil data dari tabel lain | `VLOOKUP`, `INDEX`+`MATCH`, `XLOOKUP` | `=VLOOKUP(D2,$P$2:$Q$4,2,FALSE)` |
| Cari di tabel tingkatan (nilai, tarif) | `VLOOKUP` kecocokan perkiraan | `=VLOOKUP(B2,$F$2:$G$6,2,TRUE)` |
| Jika ... maka ... | `IF`, `IFS` | `=IF(G2>=10000000,"Bonus","Biasa")` |
| Sembunyikan error | `IFERROR` | `=IFERROR(rumus,"Tidak ada")` |
| Peringkat | `RANK.EQ` | `=RANK.EQ(K2,$K$2:$K$5)` |
| Nilai terbesar ke-n | `LARGE` | `=LARGE(G2:G9,3)` |
| Potong teks | `LEFT`, `MID`, `RIGHT` | `=LEFT(A2,3)` |
| Gabung teks | `&`, `TEXTJOIN` | `=A2&" "&B2` |
| Bersihkan teks | `TRIM`, `CLEAN`, `PROPER` | `=TRIM(A2)` |
| Selisih tanggal | `DATEDIF`, `NETWORKDAYS` | `=DATEDIF(A2,TODAY(),"Y")` |
| Ringkas data besar | PivotTable | Insert > PivotTable |
| Sorot data tertentu | Conditional Formatting | Home > Conditional Formatting |
| Persentase | bagian dibagi total, lalu format % | `=K2/SUM($K$2:$K$5)` |

### Ketersediaan fungsi menurut versi Excel

- `IFS`, `SWITCH`, `CONCAT`, `TEXTJOIN`, `MAXIFS`, `MINIFS`: Excel 2019 ke atas dan Microsoft 365.
- `XLOOKUP`: Excel 2021 dan Microsoft 365. Tidak ada di Excel 2016 atau 2019.
- Kalau fungsi tidak tersedia, pakai pengganti: `IF` bersarang untuk `IFS`, `INDEX`+`MATCH` untuk `XLOOKUP`, operator `&` untuk `CONCAT` dan `TEXTJOIN`.
- Cek versi lewat File > Account > About Excel.

## Strategi saat mengerjakan tes

1. **Baca seluruh soal dulu** dan catat format keluaran yang diminta: nama sheet, nama kolom, format angka atau tanggal.
2. **Jangan menimpa data sumber.** Kerjakan di sheet atau kolom baru, dan simpan data asli apa adanya.
3. **Pakai rumus, jangan mengetik hasil.** Penguji sering memeriksa rumusnya, bukan hanya angkanya.
4. **Kunci referensi dengan `$`** sebelum menyalin rumus ke bawah (tekan `F4`).
5. **Cek kewajaran hasil.** Total pivot harus sama dengan `SUM` data. Jumlah baris harus sama dengan `COUNTA`.
6. **Rapikan hasil:** judul tebal, format angka, tanggal, dan persen yang tepat, lebar kolom pas, nama sheet yang jelas.
7. **Kerjakan soal yang pasti dulu.** Tandai yang macet, lalu kembali di akhir.
8. **Simpan sering** (`Ctrl+S`) dan beri nama file sesuai instruksi.
9. **Tulis asumsi singkat** di sheet catatan kalau soal ambigu, misalnya cara membulatkan atau menangani data kosong.
10. **Sisakan 5 sampai 10 menit terakhir** untuk mengecek `#N/A`, `#REF!`, spasi berlebih, dan format.

## Lisensi

MIT. Bebas dipakai, diubah, dan dibagikan.
