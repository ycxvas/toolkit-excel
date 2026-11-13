# Contoh Soal dan Jawaban

Pola soal yang sering muncul di tes Excel, beserta rumus jawabannya. Pelajari polanya, lalu sesuaikan kolom dan range dengan data di soal.

## Data contoh

Anggap data ada di sheet dengan judul di baris 1 dan isi di baris 2 sampai 9.

| | A | B | C | D | E | F | G |
|---|---|---|---|---|---|---|---|
| 1 | Tanggal | Sales | Wilayah | Produk | Qty | Harga | Total |
| 2 | 05/01/2026 | Andi | Jakarta | Laptop | 2 | 8.000.000 | |
| 3 | 12/01/2026 | Budi | Bandung | Mouse | 10 | 150.000 | |
| 4 | 20/01/2026 | Citra | Jakarta | Monitor | 3 | 2.500.000 | |
| 5 | 03/02/2026 | Andi | Surabaya | Mouse | 8 | 150.000 | |
| 6 | 15/02/2026 | Budi | Jakarta | Laptop | 1 | 8.000.000 | |
| 7 | 02/03/2026 | Citra | Bandung | Monitor | 4 | 2.500.000 | |
| 8 | 18/03/2026 | Dina | Surabaya | Laptop | 2 | 8.000.000 | |
| 9 | 25/03/2026 | Dina | Jakarta | Mouse | 20 | 150.000 | |

Tabel bantu untuk beberapa soal:

- Tabel harga di `P2:Q4`: Laptop 8.000.000, Mouse 150.000, Monitor 2.500.000.
- Ringkasan sales di `J2:L5`: nama di `J2:J5` (Andi, Budi, Citra, Dina), total di kolom K, peringkat di kolom L.

## Soal dan jawaban

### 1. Hitung kolom Total

```
=E2*F2
```

Salin ke baris 3 sampai 9. Hasil total semua baris: 63.200.000.

### 2. Total seluruh penjualan

```
=SUM(G2:G9)
```

Hasil: 63.200.000.

### 3. Total penjualan wilayah Jakarta

```
=SUMIFS(G2:G9,C2:C9,"Jakarta")
```

Hasil: 34.500.000.

### 4. Berapa transaksi untuk produk Laptop

```
=COUNTIFS(D2:D9,"Laptop")
```

Hasil: 3.

### 5. Total Qty Laptop yang terjual di Jakarta

```
=SUMIFS(E2:E9,D2:D9,"Laptop",C2:C9,"Jakarta")
```

Hasil: 3.

### 6. Rata-rata nilai per transaksi

```
=AVERAGE(G2:G9)
```

Hasil: 7.900.000.

### 7. Bonus: total transaksi minimal 10 juta dapat 5%, selain itu 2%

```
=IF(G2>=10000000,5%,2%)*G2
```

Baiknya taruh batas dan persen di sel terpisah (misalnya `N1`, `N2`, `N3`) lalu rujuk dengan `$`, supaya mudah diubah: `=IF(G2>=$N$1,$N$2,$N$3)*G2`.

### 8. Total per sales (ringkasan di K2:K5)

```
=SUMIFS($G$2:$G$9,$B$2:$B$9,J2)
```

Hasil: Andi 17.200.000, Budi 9.500.000, Citra 17.500.000, Dina 19.000.000. Jumlahnya sama dengan soal 2, itu cara mengecek.

### 9. Peringkat sales berdasarkan total (L2:L5)

```
=RANK.EQ(K2,$K$2:$K$5)
```

Hasil: Dina 1, Citra 2, Andi 3, Budi 4.

### 10. Persentase kontribusi tiap sales

```
=K2/SUM($K$2:$K$5)
```

Beri format Percentage. Hasil Dina sekitar 30,1%.

### 11. Ambil harga dari tabel harga

```
=VLOOKUP(D2,$P$2:$Q$4,2,FALSE)
```

Alternatif: `=INDEX($Q$2:$Q$4,MATCH(D2,$P$2:$P$4,0))` atau `=XLOOKUP(D2,$P$2:$P$4,$Q$2:$Q$4)`.

### 12. Tangani produk yang tidak ada di tabel harga

```
=IFERROR(VLOOKUP(D2,$P$2:$Q$4,2,FALSE),"Tidak ditemukan")
```

### 13. Tiga transaksi terbesar

```
=LARGE($G$2:$G$9,1)
=LARGE($G$2:$G$9,2)
=LARGE($G$2:$G$9,3)
```

Hasil: 16.000.000, 16.000.000, 10.000.000.

### 14. Nama sales dengan total tertinggi

```
=INDEX(J2:J5,MATCH(MAX(K2:K5),K2:K5,0))
```

Hasil: Dina.

### 15. Total penjualan per bulan

```
=SUMIFS($G$2:$G$9,$A$2:$A$9,">="&DATE(2026,1,1),$A$2:$A$9,"<"&DATE(2026,2,1))
```

Ubah tanggal untuk bulan lain. Kalau bulan ditulis di sel, misalnya `N5` berisi tanggal 1 Januari: `">="&N5` dan `"<"&EDATE(N5,1)`.

### 16. Buat ringkasan tanpa rumus

PivotTable: Insert > PivotTable. Rows = Wilayah, Columns = Produk, Values = Sum of Total. Cek bahwa Grand Total sama dengan 63.200.000.

### 17. Beri nilai huruf dari skor

Tabel batas di `F2:G6` (0 E, 55 D, 65 C, 75 B, 85 A):

```
=VLOOKUP(B2,$F$2:$G$6,2,TRUE)
```

### 18. Hitung umur dari tanggal lahir di A2

```
=DATEDIF(A2,TODAY(),"Y")
```

### 19. Gabungkan nama depan dan belakang

```
=A2&" "&B2
```

### 20. Pisahkan nama depan dari "Andi Pratama"

```
=LEFT(A2,FIND(" ",A2)-1)
```

### 21. Sorot baris dengan Total di atas 10 juta

Conditional Formatting > New Rule > Use a formula, pilih `A2:G9`, rumus `=$G2>10000000`.

### 22. Batasi kolom Wilayah hanya Jakarta, Bandung, Surabaya

Data > Data Validation > Allow: List > Source: `Jakarta,Bandung,Surabaya`.

## Cara memeriksa jawaban

- Total semua sales (K2:K5) harus sama dengan `SUM(G2:G9)`.
- Grand Total pivot harus sama dengan `SUM(G2:G9)`.
- Jumlah baris data: `=COUNTA(A2:A9)` harus 8.
- Kalau ada `#N/A`, cek spasi dan jenis data (angka atau teks) di kolom yang dicari.
