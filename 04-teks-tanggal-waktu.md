# Teks, Tanggal, dan Waktu

## Fungsi teks

| Fungsi | Kegunaan | Contoh |
|---|---|---|
| `LEFT(teks, n)` | n karakter dari kiri | `=LEFT(A2,3)` |
| `RIGHT(teks, n)` | n karakter dari kanan | `=RIGHT(A2,4)` |
| `MID(teks, mulai, n)` | n karakter mulai posisi tertentu | `=MID(A2,4,2)` |
| `LEN(teks)` | Panjang teks | `=LEN(A2)` |
| `FIND(cari, teks)` | Posisi teks (peka huruf besar-kecil) | `=FIND(" ",A2)` |
| `SEARCH(cari, teks)` | Posisi teks (tidak peka huruf besar-kecil, boleh wildcard) | `=SEARCH("a",A2)` |
| `SUBSTITUTE(teks, lama, baru)` | Ganti teks | `=SUBSTITUTE(A2,"-","")` |
| `TRIM(teks)` | Hapus spasi berlebih | `=TRIM(A2)` |
| `CLEAN(teks)` | Hapus karakter tak tercetak | `=CLEAN(A2)` |
| `UPPER`, `LOWER`, `PROPER` | Huruf besar, kecil, kapital tiap kata | `=PROPER(A2)` |
| `&` | Gabung teks | `=A2&" "&B2` |
| `CONCAT` | Gabung (Excel 2019 ke atas) | `=CONCAT(A2:C2)` |
| `TEXTJOIN(pemisah, abaikan_kosong, range)` | Gabung dengan pemisah | `=TEXTJOIN(", ",TRUE,A2:A5)` |
| `VALUE(teks)` | Teks menjadi angka | `=VALUE(A2)` |
| `TEXT(nilai, format)` | Angka atau tanggal menjadi teks berformat | `=TEXT(A2,"0000")` |
| `REPT(teks, n)` | Ulang teks | `=REPT("*",5)` |

### Pola yang sering keluar

```
Nama depan   : =LEFT(A2,FIND(" ",A2)-1)
Nama belakang: =MID(A2,FIND(" ",A2)+1,100)
Kode 3 huruf pertama huruf besar: =UPPER(LEFT(A2,3))
Nomor jadi 4 digit (0007): =TEXT(A2,"0000")   atau   =RIGHT("0000"&A2,4)
Hapus semua spasi: =SUBSTITUTE(A2," ","")
Email dari nama: =LOWER(A2)&"@perusahaan.com"
Jumlah kata: =LEN(TRIM(A2))-LEN(SUBSTITUTE(TRIM(A2)," ",""))+1
```

### Memecah atau merapikan tanpa rumus

- **Text to Columns:** pilih kolom, Data > Text to Columns, pilih pemisah (spasi, koma, dan sebagainya).
- **Flash Fill:** ketik contoh hasil di sel pertama, lalu tekan `Ctrl+E` di sel berikutnya.
- **Find and Replace:** `Ctrl+H`.

## Fungsi tanggal

| Fungsi | Kegunaan | Contoh |
|---|---|---|
| `TODAY()` | Tanggal hari ini | `=TODAY()` |
| `NOW()` | Tanggal dan jam sekarang | `=NOW()` |
| `DATE(y, m, d)` | Membuat tanggal | `=DATE(2026,3,15)` |
| `YEAR`, `MONTH`, `DAY` | Ambil tahun, bulan, hari | `=MONTH(A2)` |
| `WEEKDAY(tgl, 2)` | Hari ke berapa (Senin = 1) | `=WEEKDAY(A2,2)` |
| `WEEKNUM(tgl)` | Minggu ke berapa | `=WEEKNUM(A2)` |
| `EOMONTH(tgl, n)` | Akhir bulan, n bulan dari tanggal | `=EOMONTH(A2,0)` |
| `EDATE(tgl, n)` | Geser n bulan | `=EDATE(A2,3)` |
| `DATEDIF(awal, akhir, kode)` | Selisih tahun, bulan, atau hari | `=DATEDIF(A2,TODAY(),"Y")` |
| `NETWORKDAYS(awal, akhir, [libur])` | Jumlah hari kerja | `=NETWORKDAYS(A2,B2,$H$2:$H$10)` |
| `WORKDAY(awal, n, [libur])` | Tanggal setelah n hari kerja | `=WORKDAY(A2,10)` |

Kode `DATEDIF`: `"Y"` tahun penuh, `"M"` bulan penuh, `"D"` hari, `"YM"` sisa bulan setelah tahun penuh. Fungsi ini tidak muncul di daftar saran Excel, tetapi tetap bisa dipakai.

### Pola yang sering keluar

```
Umur                : =DATEDIF(A2,TODAY(),"Y")
Masa kerja (tahun)  : =DATEDIF(A2,TODAY(),"Y")
Selisih hari        : =B2-A2
Jatuh tempo 30 hari : =A2+30
Akhir bulan         : =EOMONTH(A2,0)
Hari kerja          : =NETWORKDAYS(A2,B2)
Kuartal             : =ROUNDUP(MONTH(A2)/3,0)
```

## Jam dan durasi

- Excel menyimpan waktu sebagai pecahan hari. Selisih jam: `=B2-A2`, lalu format sel sebagai `[h]:mm` agar lebih dari 24 jam tetap tampil benar.
- Untuk jam dalam bentuk angka desimal: `=(B2-A2)*24`.

## Kalau tanggal tidak terbaca

| Gejala | Penyebab | Solusi |
|---|---|---|
| Tanggal rata kiri dan tidak bisa dihitung | Tersimpan sebagai teks | Data > Text to Columns > Finish, atau `=DATEVALUE(A2)` |
| Bulan dan hari tertukar | Format regional berbeda (bulan/hari/tahun atau hari/bulan/tahun) | Pakai `=DATE(tahun, bulan, hari)` dari potongan teks |
| `TEXT(A2,"mmmm")` memberi hasil aneh | Kode format bisa berbeda mengikuti bahasa Excel | Pakai `=MONTH(A2)` atau ubah lewat Format Cells > Custom |
