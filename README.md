# Analisis Berita Daring DIY Oktober 2025

Proyek ini merupakan analisis data yang dilakukan menggunakan metodologi **CRISP-DM (Cross Industry Standard Process for Data Mining)** untuk menganalisis kumpulan berita daring dari berbagai media di wilayah **Yogyakarta pada bulan Oktober 2025**.  
Tujuan utama proyek ini adalah untuk memahami pola pemberitaan, sentimen terhadap institusi kepolisian, serta dinamika publikasi berita di media daring.

---

## Tujuan Analisis
1. Mengidentifikasi topik dan kategori berita paling dominan di wilayah Yogyakarta.  
2. Menganalisis sentimen umum dan sentimen terhadap kepolisian.  
3. Mengevaluasi emosi dalam pemberitaan berdasarkan topik.  
4. Mengukur kecepatan publikasi dan pembaruan berita.  
5. Menganalisis efektivitas sistem distribusi berita melalui Elasticsearch.  
6. Menampilkan hasil analisis dalam dashboard interaktif menggunakan Tableau.

---

## Dataset
Dataset berisi **2.109 baris** dan **37 atribut**, mencakup:
- **Informasi umum berita** (judul, ringkasan, media, tanggal publikasi, dll)  
- **Analisis teks & emosi** (sentimen, emotion, SDGs, keywords, NERs)  
- **Informasi lokasi** (kota, provinsi, koordinat geografis)  
- **Informasi waktu** (created, published, updated, known_by_police)  
- **Metadata tambahan** (authors, hashtags, site)

---

## Tahapan CRISP-DM

### Business Understanding
Analisis dilakukan untuk mengetahui:
- Pola sentimen publik dan media terhadap isu tertentu (khususnya polisi)  
- Topik yang sering muncul dan sebaran lokasi peliputan  
- Pola waktu publikasi, pembaruan, dan distribusi berita  
- Efisiensi sistem publikasi digital

### Data Understanding
Eksplorasi awal data dilakukan untuk memahami struktur, tipe data, serta nilai kosong.  
Beberapa kolom seperti `is_updated`, `published_to_es`, dan `geo` memiliki missing values yang kemudian ditangani pada tahap berikutnya.

### Data Preparation
Langkah-langkah pembersihan data meliputi:
- Menghapus atribut yang tidak relevan (`authors`, `favicon`, `geo`, dll)
- Mengisi nilai kosong dengan kategori *“lainnya”*
- Mengonversi tipe data waktu menjadi format `datetime`
- Mengubah atribut boolean seperti `is_updated` dan `published_to_es`
- Membuat kolom waktu publikasi kategori (`pagi`, `siang`, `sore`, `malam`)
- Mengekstraksi koordinat `latitude` dan `longitude` dari kolom `provinsi`

Kode preprocessing ditulis di [**Google Colab**](DIY_NEWS_2025.ipynb) menggunakan Python

### Modelling & Visualization
Data yang telah dibersihkan divisualisasikan menggunakan **Tableau Public**.  
Dashboard menampilkan berbagai analisis seperti:
- Distribusi berita berdasarkan topik dan kota  
- Sebaran sentimen dan emosi berita  
- Tren publikasi per hari  
- Waktu publikasi (pagi/siang/sore/malam)  
- Citra polisi di media  
- Perbandingan berita yang diperbarui dan tidak diperbarui  
- Analisis hubungan topik–SDGs dan topik–lokasi  

**Link Dashboard Tableau:**  
[Lihat di Tableau Public](https://public.tableau.com/views/PSD_17657771014070/Dashboard2?:language=en-US&publish=yes)

---

## Hasil Utama
- Mayoritas berita memiliki **sentimen netral**, baik secara umum maupun terhadap kepolisian.  
- **Topik budaya, sport, dan wisata** menjadi kategori berita paling dominan.  
- Sebagian besar berita dipublikasikan pada **malam hari**.  
- **Pulau Jawa (khususnya Yogyakarta)** memiliki jumlah berita tertinggi.  
- Proses publikasi berita ke sistem digital (Elasticsearch) masih belum optimal.

---

[Dokumentasi CRISP DM](Dokumentasi%20CRISP%20DM.pdf)
