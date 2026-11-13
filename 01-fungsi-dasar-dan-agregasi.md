# Fungsi Dasar dan Agregasi

Contoh memakai koma sebagai pemisah argumen. Kalau Excel menolak koma, ganti dengan titik koma (`;`).

## Menjumlah dan menghitung

| Fungsi | Kegunaan | Contoh |
|---|---|---|
| `SUM` | Jumlah | `=SUM(B2:B100)` |
| `AVERAGE` | Rata-rata | `=AVERAGE(B2:B100)` |
| `MIN`, `MAX` | Terkecil, terbesar | `=MAX(B2:B100)` |
| `MEDIAN` | Nilai tengah | `=MEDIAN(B2:B100)` |
| `COUNT` | Hitung sel berisi angka | `=COUNT(B2:B100)` |
| `COUNTA` | Hitung sel tidak kosong (angka dan teks) | `=COUNTA(A2:A100)` |
| `COUNTBLANK` | Hitung sel kosong | `=COUNTBLANK(B2:B100)` |
| `ROUND` | Bulatkan | `=ROUND(A1,2)` (2 desimal) |
| `ROUNDUP`, `ROUNDDOWN` | Bulatkan ke atas, ke bawah | `=ROUNDUP(A1,0)` |
| `INT` | Buang desimal, bulatkan ke bawah | `=INT(7.9)` hasilnya 7 |
| `MOD` | Sisa bagi | `=MOD(10,3)` hasilnya 1 |
| `ABS` | Nilai mutlak | `=ABS(-5)` |
| `SUMPRODUCT` | Jumlah hasil kali beberapa kolom | `=SUMPRODUCT(E2:E9,F2:F9)` |
| `SUBTOTAL` | Jumlah yang mengikuti filter | `=SUBTOTAL(9,G2:G9)` |
| `LARGE`, `SMALL` | Terbesar atau terkecil ke-n | `=LARGE(G2:G9,3)` |
| `RANK.EQ` | Peringkat | `=RANK.EQ(K2,$K$2:$K$5)` |

Catatan:

- Digit negatif pada `ROUND` membulatkan ke puluhan, ratusan, dan seterusnya: `=ROUND(1234,-2)` menjadi 1200.
- `SUBTOTAL(9,...)` mengabaikan baris yang disembunyikan oleh filter. `SUBTOTAL(109,...)` juga mengabaikan baris yang disembunyikan manual.
- `RANK.EQ` secara bawaan mengurutkan dari terbesar (peringkat 1 untuk nilai tertinggi). Isi argumen ketiga dengan 1 untuk urutan terkecil.

## Dengan syarat

| Fungsi | Bentuk |
|---|---|
| `SUMIF` | `=SUMIF(range_syarat, syarat, range_jumlah)` |
| `SUMIFS` | `=SUMIFS(range_jumlah, range_syarat1, syarat1, range_syarat2, syarat2, ...)` |
| `COUNTIF` | `=COUNTIF(range_syarat, syarat)` |
| `COUNTIFS` | `=COUNTIFS(range_syarat1, syarat1, range_syarat2, syarat2, ...)` |
| `AVERAGEIFS` | `=AVERAGEIFS(range_rata, range_syarat1, syarat1, ...)` |
| `MAXIFS`, `MINIFS` | `=MAXIFS(range_nilai, range_syarat1, syarat1, ...)` (Excel 2019 ke atas) |

**Waspada urutan argumen:** pada `SUMIFS` range yang dijumlahkan ada di **depan**, sedangkan pada `SUMIF` ada di **belakang**.

Contoh:

```
=SUMIFS(G2:G9,C2:C9,"Jakarta")
=SUMIFS(G2:G9,C2:C9,"Jakarta",D2:D9,"Laptop")
=COUNTIFS(E2:E9,">=5")
=SUMIFS(G2:G9,A2:A9,">="&DATE(2026,2,1),A2:A9,"<"&DATE(2026,3,1))
```

### Cara menulis syarat

| Syarat | Penulisan |
|---|---|
| Sama dengan teks | `"Jakarta"` |
| Sama dengan isi sel | `A1` |
| Lebih besar atau sama | `">=100"` |
| Lebih besar dari isi sel | `">"&A1` |
| Tidak sama dengan | `"<>Jakarta"` |
| Tidak kosong | `"<>"` |
| Mengandung kata | `"*laptop*"` |
| Diawali huruf | `"A*"` |
| Rentang tanggal | `">="&DATE(2026,1,1)` |

Panjang semua range dalam satu rumus harus sama, kalau tidak hasilnya `#VALUE!`.

## Persentase

- Kontribusi: `=bagian/total`, lalu beri format Percentage. Contoh: `=K2/SUM($K$2:$K$5)`.
- Pertumbuhan: `=(baru-lama)/lama`. Contoh: `=(C2-B2)/B2`.
- Jangan mengalikan 100 lalu memberi format persen, karena hasilnya menjadi 100 kali lebih besar.
- Untuk menambah persen: `=A1*(1+10%)`.

## Referensi sel

| Bentuk | Arti |
|---|---|
| `A1` | Relatif: bergeser saat rumus disalin |
| `$A$1` | Absolut: baris dan kolom terkunci |
| `$A1` | Kolom terkunci, baris bergeser |
| `A$1` | Baris terkunci, kolom bergeser |

Tekan `F4` saat kursor di referensi untuk berganti bentuk. Contoh umum: `=B2/$B$10` agar penyebut tetap saat disalin ke bawah.
