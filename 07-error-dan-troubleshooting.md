# Error dan Troubleshooting

## Arti pesan error

| Error | Arti | Penyebab umum dan solusi |
|---|---|---|
| `#N/A` | Nilai tidak ditemukan | Lookup tidak menemukan data: cek ejaan, spasi (`TRIM`), angka berupa teks, dan `FALSE` di `VLOOKUP` |
| `#VALUE!` | Jenis data salah | Menghitung teks dengan angka, range beda ukuran di `SUMIFS`, atau tanggal berupa teks |
| `#REF!` | Referensi hilang | Kolom atau baris yang dirujuk terhapus, atau nomor kolom `VLOOKUP` melebihi tabel |
| `#DIV/0!` | Dibagi nol | Penyebut kosong atau nol. Bungkus dengan `=IF(B2=0,0,A2/B2)` atau `IFERROR` |
| `#NAME?` | Nama tidak dikenal | Salah ketik nama fungsi, teks tanpa tanda kutip, atau fungsi tidak ada di versi Excel ini |
| `#NUM!` | Angka tidak valid | Hasil terlalu besar atau kecil, atau argumen tidak wajar (misalnya akar bilangan negatif) |
| `#NULL!` | Irisan range kosong | Ada spasi di tempat yang seharusnya koma atau titik dua |
| `#SPILL!` | Hasil tumpah terhalang | Ada sel terisi di area tempat hasil rumus akan mengalir |
| `####` | Kolom terlalu sempit | Lebarkan kolom. Tanggal negatif juga bisa menampilkan ini |

## Rumus tidak menghitung atau salah hasil

| Masalah | Penyebab | Solusi |
|---|---|---|
| Rumus tampil sebagai teks | Sel berformat Text, atau diawali tanda petik | Ubah format ke General, tekan `F2` lalu `Enter` |
| Hasil tidak berubah saat data diubah | Mode hitung manual | Formulas > Calculation Options > Automatic |
| Angka tidak mau dijumlah | Angka tersimpan sebagai teks (rata kiri, ada segitiga hijau) | Pilih sel > ikon peringatan > Convert to Number |
| Angka tersimpan sebagai teks, massal | Banyak sel | Ketik 1 di sel kosong, salin, pilih data, Paste Special > Multiply |
| Rumus berhenti di tengah | Circular reference | Cek Formulas > Error Checking > Circular References |
| Hasil beda dari perhitungan manual | Pembulatan tampilan | Format hanya mengubah tampilan, nilai asli tetap. Pakai `ROUND` kalau perlu |
| `SUM` lebih kecil dari seharusnya | Sebagian sel berupa teks | Cek dengan `=COUNT(range)` dibanding `=COUNTA(range)` |

## Pemisah dan bahasa Excel

- **Koma ditolak, minta titik koma:** pengaturan regional komputer menentukan pemisah argumen. Kalau `=SUM(A1,A2)` ditolak, tulis `=SUM(A1;A2)`.
- **Desimal memakai koma:** pada pengaturan regional Indonesia, 3,5 berarti tiga setengah. Mengetik titik bisa terbaca sebagai teks atau tanggal.
- **Nama fungsi dalam bahasa lain:** Excel bisa menampilkan nama fungsi sesuai bahasa yang terpasang. Kalau ejaan Inggris memberi `#NAME?`, buka **Formulas > Insert Function** dan cari fungsinya dengan deskripsi, atau pakai pemilih fungsi (`Shift+F3`) agar Excel menuliskan nama yang tepat.
- Microsoft menyediakan add-in **Excel Functions Translator** untuk melihat padanan nama fungsi antar bahasa.

## Data yang kotor

| Masalah | Solusi |
|---|---|
| Spasi berlebih | `=TRIM(A2)` |
| Karakter aneh | `=CLEAN(A2)` |
| Huruf besar-kecil tidak seragam | `=PROPER(A2)`, `UPPER`, `LOWER` |
| Duplikat | Data > Remove Duplicates |
| Sel kosong di tengah data | Filter kolom, atau Go To Special (`F5` > Special > Blanks) |
| Dua kolom digabung jadi satu | Text to Columns atau `Ctrl+E` |
| Tanggal berupa teks | Text to Columns > Date, atau `=DATEVALUE(A2)` |
| Angka ada simbol (Rp, titik) | `=VALUE(SUBSTITUTE(SUBSTITUTE(A2,"Rp",""),".",""))` |

## Alat bantu memeriksa rumus

- **F9 di dalam rumus:** saat mengedit rumus, blok sebagian lalu tekan `F9` untuk melihat hasil bagian itu. Tekan `Esc` untuk membatalkan.
- **Evaluate Formula:** Formulas > Evaluate Formula, untuk melihat rumus dihitung langkah demi langkah.
- **Trace Precedents / Dependents:** Formulas > Trace Precedents, untuk melihat sel mana yang dirujuk.
- **Tampilkan semua rumus:** ``Ctrl+` ``.
