# Lookup dan Referensi

## VLOOKUP

```
=VLOOKUP(nilai_dicari, tabel, nomor_kolom, FALSE)
=VLOOKUP(D2,$P$2:$Q$4,2,FALSE)
```

Aturan penting:

- Nilai yang dicari harus ada di **kolom pertama** tabel.
- `nomor_kolom` dihitung dari kolom pertama tabel yang kamu pilih, bukan dari kolom A lembar kerja.
- Argumen keempat `FALSE` (atau `0`) berarti cocok persis. Kalau dikosongkan, Excel memakai kecocokan perkiraan dan hasilnya bisa salah diam-diam.
- Kunci tabel dengan `$` agar tidak bergeser saat rumus disalin.
- `VLOOKUP` tidak bisa mengambil kolom di sebelah **kiri** kolom pencarian. Untuk itu pakai `INDEX`+`MATCH` atau `XLOOKUP`.

`HLOOKUP` sama, tetapi mencari ke arah baris: `=HLOOKUP(nilai, tabel, nomor_baris, FALSE)`.

## INDEX dan MATCH

```
=INDEX(kolom_hasil, MATCH(nilai_dicari, kolom_cari, 0))
=INDEX($Q$2:$Q$4,MATCH(D2,$P$2:$P$4,0))
```

Kelebihan: bisa mengambil dari kolom mana pun, dan tidak rusak kalau kolom disisipkan.

### Dua arah (baris dan kolom)

```
=INDEX($B$2:$E$10,MATCH(H1,$A$2:$A$10,0),MATCH(H2,$B$1:$E$1,0))
```

Satu `MATCH` mencari baris, satu lagi mencari kolom.

### Jenis MATCH

| Argumen ketiga | Arti |
|---|---|
| `0` | Cocok persis (paling sering dipakai) |
| `1` | Nilai terbesar yang kurang dari atau sama dengan (data urut naik) |
| `-1` | Nilai terkecil yang lebih besar dari atau sama dengan (data urut turun) |

## XLOOKUP (Excel 2021 dan Microsoft 365)

```
=XLOOKUP(nilai_dicari, kolom_cari, kolom_hasil, "Tidak ada")
=XLOOKUP(D2,$P$2:$P$4,$Q$2:$Q$4,"Tidak ada")
```

Bisa mencari ke kiri, bawaannya cocok persis, dan punya argumen bawaan untuk hasil yang tidak ditemukan. Kalau Excel di komputer tes lebih lama, pakai `INDEX`+`MATCH`.

## Tabel tingkatan (kecocokan perkiraan)

Untuk nilai huruf, tarif, komisi, atau diskon bertingkat. Susun batas bawah **urut naik**:

| Batas bawah | Nilai |
|---|---|
| 0 | E |
| 55 | D |
| 65 | C |
| 75 | B |
| 85 | A |

```
=VLOOKUP(B2,$F$2:$G$6,2,TRUE)
```

Nilai 78 menghasilkan B, karena Excel mengambil batas terbesar yang tidak melebihi 78 (yaitu 75). Kalau tabel tidak urut naik, hasilnya salah.

## Fungsi referensi lain

| Fungsi | Kegunaan | Contoh |
|---|---|---|
| `CHOOSE` | Pilih nilai berdasarkan nomor | `=CHOOSE(2,"Satu","Dua","Tiga")` |
| `ROW`, `COLUMN` | Nomor baris atau kolom | `=ROW(A5)` hasilnya 5 |
| `ROWS`, `COLUMNS` | Jumlah baris atau kolom dalam range | `=ROWS(A2:A100)` |
| `INDIRECT` | Referensi dari teks | `=SUM(INDIRECT("B2:B"&D1))` |
| `OFFSET` | Referensi bergeser dari titik awal | `=SUM(OFFSET(A1,1,1,3,1))` |

## Jebakan yang sering membuat lookup gagal

| Gejala | Penyebab | Solusi |
|---|---|---|
| `#N/A` padahal datanya ada | Spasi di depan atau belakang | `=TRIM(A2)` |
| `#N/A` padahal angkanya sama | Angka di satu sisi berupa teks | Ubah ke angka dengan `=VALUE(A2)` atau Text to Columns |
| Hasil salah tapi tanpa error | Lupa `FALSE` di `VLOOKUP` | Selalu isi argumen keempat |
| Hasil bergeser saat disalin | Tabel tidak dikunci | Pakai `$P$2:$Q$4` |
| `#REF!` | `nomor_kolom` lebih besar dari jumlah kolom tabel | Periksa angka kolom |
