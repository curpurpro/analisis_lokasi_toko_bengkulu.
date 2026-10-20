# analisis_lokasi_toko_bengkulu.
# Analisis Lokasi Potensial Toko Ritel di Kota Bengkulu

Studi kasus berdasarkan materi kuliah *Karier dan Kompetisi di Era Industri dengan GIS*. Pada bisnis ritel, GIS membantu menentukan lokasi toko berdasarkan jumlah penduduk dan jarak antarcabang. Proyek ini menerapkan gagasan itu dengan Python, data terbuka, dan Google Earth Engine.

Ini analisis awal berbasis data terbuka. Hasilnya adalah daftar area untuk survei lanjutan, bukan rekomendasi final lokasi.

## Pertanyaan

Area mana di Kota Bengkulu yang padat penduduk, masih jauh dari toko yang sudah ada, dan dekat jalan utama?

## Data

| Data | Sumber |
| --- | --- |
| Populasi (estimasi 2020, 100 m) | WorldPop via Google Earth Engine (`WorldPop/GP/100m/pop`) |
| Toko (`shop=convenience`, `shop=supermarket`) | OpenStreetMap (osmnx) |
| Jalan utama (primary, secondary, tertiary) | OpenStreetMap (osmnx) |
| Batas Kota Bengkulu | OpenStreetMap (Nominatim) |

## Metode

1. Membagi wilayah menjadi grid 500 m (UTM 48S, EPSG:32748).
2. Menghitung populasi, jarak ke toko terdekat, dan jarak ke jalan utama per sel.
3. Skor gabungan berbobot: populasi 0,5, celah layanan 0,3, akses jalan 0,2. Sel dengan populasi di bawah 200 jiwa dianggap tidak layak.
4. Uji sensitivitas dengan lima skenario bobot untuk mencari sel yang konsisten masuk 10 besar.

## Struktur repositori

| File | Isi |
| --- | --- |
| `analisis_lokasi_toko_bengkulu.ipynb` | Notebook Google Colab |
| `hasil_skor_grid_bengkulu.csv` | Skor dan atribut tiap sel grid |
| `kandidat_lokasi_toko_bengkulu.geojson` | 10 sel kandidat teratas |
| `peta_skor_lokasi_toko.png` | Peta statis skor kelayakan |
| `peta_lokasi_toko_bengkulu.html` | Peta web interaktif (unduh lalu buka di browser) |
| `requirements.txt` | Daftar pustaka Python |

## Cara menjalankan

1. Buka notebook di Google Colab.
2. Jalankan sel berurutan dan login ke Google Earth Engine saat diminta.

## Hasil

> Isi setelah notebook dijalankan.

- Jumlah toko OSM, sel grid, dan total populasi: *(isi)*
- 10 sel kandidat teratas: *(isi ringkasan)*
- Sel yang stabil di semua skenario bobot: *(isi)*

## Keterbatasan

- Populasi WorldPop adalah estimasi model, bukan sensus.
- Data OSM bisa belum lengkap.
- Jarak berupa garis lurus, bukan waktu tempuh.
- Bobot dan ambang adalah asumsi. Harga lahan, pesaing yang tidak ada di OSM, dan daya beli belum diperhitungkan.

## Kesimpulan

> Isi setelah hasil tersedia.
