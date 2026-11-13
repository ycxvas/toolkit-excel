# PivotTable, Grafik, dan Alat Data

## PivotTable

Siapkan data dulu: satu baris judul, tiap kolom punya judul, tidak ada baris atau kolom kosong di tengah, dan tidak ada sel yang digabung.

1. Klik satu sel di dalam data.
2. **Insert > PivotTable**, lalu OK.
3. Seret kolom ke area **Rows**, **Columns**, **Values**, atau **Filters**.
4. Klik kolom di area Values > **Value Field Settings** untuk mengganti Sum, Count, Average, dan sebagainya.

| Kebutuhan | Cara |
|---|---|
| Tampilkan persen dari total | Value Field Settings > Show Values As > % of Grand Total |
| Kelompokkan tanggal per bulan atau tahun | Klik kanan sel tanggal di pivot > Group > pilih Months, Years |
| Urutkan terbesar ke terkecil | Klik kanan nilai > Sort > Largest to Smallest |
| Tampilkan 3 teratas | Klik panah di Row Labels > Value Filters > Top 10 |
| Filter interaktif | PivotTable Analyze > Insert Slicer |
| Rumus sendiri di pivot | PivotTable Analyze > Fields, Items & Sets > Calculated Field |
| Perbarui setelah data berubah | Klik kanan pivot > Refresh, atau `Alt+F5` |
| Grafik dari pivot | PivotTable Analyze > PivotChart |

Jebakan:

- Pivot **tidak otomatis** ikut berubah saat data sumber diedit. Selalu Refresh.
- Kalau tanggal tidak bisa dikelompokkan, ada sel di kolom itu yang berupa teks atau kosong.
- Kalau angka terhitung sebagai Count padahal seharusnya Sum, ada sel teks atau kosong di kolom itu.

## Sort dan Filter

- **Sort:** Data > Sort. Tambah level untuk urutan bertingkat (misalnya wilayah, lalu total).
- **Filter:** Data > Filter (`Ctrl+Shift+L`). Untuk menjumlah hasil filter, pakai `SUBTOTAL(9,...)`.
- **Remove Duplicates:** Data > Remove Duplicates, centang kolom yang dibandingkan.
- Sebelum sort, pastikan seluruh kolom ikut terpilih supaya baris tidak terpisah dari datanya.

## Conditional Formatting

Home > Conditional Formatting.

| Kebutuhan | Menu |
|---|---|
| Sorot angka di atas nilai tertentu | Highlight Cells Rules > Greater Than |
| Sorot 10 teratas | Top/Bottom Rules |
| Sorot duplikat | Highlight Cells Rules > Duplicate Values |
| Bar atau skala warna | Data Bars, Color Scales |
| Ikon status | Icon Sets |

Untuk menyorot satu baris penuh berdasarkan satu kolom, pakai rumus:

1. Pilih seluruh range data (misalnya `A2:G9`).
2. New Rule > Use a formula to determine which cells to format.
3. Isi rumus dengan sel baris pertama dan kunci **kolom** saja: `=$G2>=10000000`.
4. Atur Format (warna isi), lalu OK.

## Data Validation

Data > Data Validation.

- **Daftar pilihan (dropdown):** Allow = List, isi Source dengan range atau teks dipisah koma, misalnya `Jakarta,Bandung,Surabaya`.
- **Batasi angka atau tanggal:** Allow = Whole number, Decimal, atau Date.
- Tab Input Message dan Error Alert untuk pesan petunjuk dan penolakan.
- Menandai data yang sudah terlanjur salah: Data Validation > Circle Invalid Data.

## Format sebagai Tabel

`Ctrl+T` mengubah data menjadi tabel: filter otomatis, rumus ikut menyalin ke baris baru, dan range ikut membesar. Di dalam tabel, rumus bisa memakai nama kolom, misalnya `=[@Qty]*[@Harga]`.

## Grafik

1. Pilih data (termasuk judul kolom).
2. Insert > Recommended Charts, atau pilih jenis sendiri.
3. Tambahkan judul dan label sumbu lewat tombol **+** di samping grafik.

| Tujuan | Jenis grafik |
|---|---|
| Bandingkan antar kategori | Column atau Bar |
| Tren dari waktu ke waktu | Line |
| Bagian dari keseluruhan (sedikit kategori) | Pie |
| Hubungan dua angka | Scatter |
| Dua skala berbeda dalam satu grafik | Combo (kolom + garis, sumbu sekunder) |

Penilaian tes biasanya melihat: jenis grafik yang tepat, judul, label sumbu, dan legenda yang jelas.

## Alat lain yang berguna

| Alat | Lokasi atau cara |
|---|---|
| Freeze Panes | View > Freeze Panes |
| Goal Seek (cari input agar hasil tertentu) | Data > What-If Analysis > Goal Seek |
| Nama range | Formulas > Define Name, atau ketik nama di kotak Name Box |
| Proteksi sheet | Review > Protect Sheet |
| Subtotal otomatis | Data > Subtotal (data harus sudah diurutkan) |
| Print: judul berulang | Page Layout > Print Titles |
| Print: muat satu halaman | Page Layout > Width: 1 page |
| Sparklines (grafik mini dalam sel) | Insert > Sparklines |
| Paste Special (nilai saja) | `Ctrl+Alt+V`, lalu pilih Values |
