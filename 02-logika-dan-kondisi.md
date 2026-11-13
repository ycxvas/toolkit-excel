# Logika dan Kondisi

## IF

```
=IF(syarat, nilai_jika_benar, nilai_jika_salah)
=IF(G2>=10000000,"Bonus","Biasa")
=IF(G2>=10000000,5%,2%)*G2
```

## IF bersarang

Dipakai untuk lebih dari dua kemungkinan. Urutkan syarat dari yang paling ketat.

```
=IF(B2>=85,"A",IF(B2>=75,"B",IF(B2>=65,"C",IF(B2>=55,"D","E"))))
```

Untuk banyak tingkatan, tabel batas dengan `VLOOKUP` kecocokan perkiraan lebih rapi. Lihat [lookup](03-lookup-dan-referensi.md).

## IFS (Excel 2019 ke atas)

```
=IFS(B2>=85,"A",B2>=75,"B",B2>=65,"C",B2>=55,"D",TRUE,"E")
```

`TRUE` di pasangan terakhir berfungsi sebagai "selain semua di atas". Tanpa itu, nilai yang tidak memenuhi syarat apa pun menghasilkan `#N/A`.

## AND, OR, NOT

| Fungsi | Arti | Contoh |
|---|---|---|
| `AND` | Semua syarat benar | `=IF(AND(C2="Jakarta",E2>=5),"Ya","Tidak")` |
| `OR` | Salah satu benar | `=IF(OR(C2="Jakarta",C2="Bandung"),"Jawa","Luar")` |
| `NOT` | Kebalikan | `=IF(NOT(ISBLANK(A2)),"Ada","Kosong")` |

## IFERROR dan IFNA

```
=IFERROR(VLOOKUP(D2,$P$2:$Q$4,2,FALSE),"Tidak ditemukan")
=IFNA(VLOOKUP(D2,$P$2:$Q$4,2,FALSE),"Tidak ditemukan")
```

`IFERROR` menangkap semua jenis error. `IFNA` hanya `#N/A`, jadi error lain (misalnya `#REF!`) tetap terlihat dan tidak tertutupi. Pakai `IFNA` kalau kamu ingin kesalahan rumus tetap kelihatan.

## SWITCH (Excel 2019 ke atas)

```
=SWITCH(C2,"Jakarta","Barat","Bandung","Barat","Surabaya","Timur","Lainnya")
```

Argumen terakhir tanpa pasangan menjadi nilai bawaan.

## Fungsi pemeriksa (IS)

| Fungsi | Benar jika |
|---|---|
| `ISBLANK(A1)` | Sel kosong |
| `ISNUMBER(A1)` | Berisi angka |
| `ISTEXT(A1)` | Berisi teks |
| `ISERROR(A1)` | Berisi error apa pun |
| `ISNA(A1)` | Berisi `#N/A` |

Contoh kegunaan: cek angka yang tersimpan sebagai teks dengan `=ISNUMBER(A2)`. Kalau hasilnya `FALSE` padahal terlihat angka, datanya berupa teks.

## Pola umum

| Soal | Rumus |
|---|---|
| Status lulus kalau nilai minimal 70 | `=IF(B2>=70,"Lulus","Tidak lulus")` |
| Bonus bertingkat | `=IF(G2>=20000000,0.1,IF(G2>=10000000,0.05,0.02))*G2` |
| Kosongkan kalau sumber kosong | `=IF(A2="","",B2*C2)` |
| Tandai duplikat | `=IF(COUNTIF($A$2:$A$100,A2)>1,"Duplikat","")` |
| Telat atau tepat waktu | `=IF(B2>C2,"Telat","Tepat waktu")` |
