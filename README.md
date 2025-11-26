# Exploring Customer Experience and Sentiment Analysis among Gojek Users

## Deskripsi Singkat
Proyek ini bertujuan mengeksplorasi pengalaman pelanggan (customer experience) dan sentimen pengguna aplikasi Gojek melalui ulasan di Google Play Store. Dengan pendekatan pemodelan berbasis bahasa alami, tim memetakan sentimen, dimensi layanan, hingga topik isu untuk menghasilkan insight perbaikan produk dan layanan.

## Latar Belakang
Gojek adalah super-app dengan ekosistem layanan luas (GoRide, GoFood, GoPay, dll.). Google Play Store menjadi kanal utama untuk menerima User-Generated Content (UGC) berupa ulasan dan keluhan. Volume ulasan yang tinggi membuat analisis manual tidak efektif sehingga risiko kehilangan loyalitas pelanggan meningkat apabila pain point tidak terdeteksi cepat, seperti masalah aplikasi, promosi gagal, atau pembatalan pesanan oleh mitra.

## Rumusan Masalah
- Kesulitan mengidentifikasi sentimen keseluruhan secara cepat dan akurat.
- Kesulitan menemukan dimensi customer experience dengan keluhan terbanyak.
- Kesulitan memahami topik atau isu spesifik yang menjadi keluhan utama (misal: aplikasi error saat pembaruan, promo gagal, atau driver melakukan pembatalan).

## Tujuan Penelitian & Hasil yang Diharapkan
| Tujuan | Hasil yang Diharapkan |
| --- | --- |
| Mengidentifikasi sentimen pengguna secara otomatis | Menentukan apakah ulasan bernada positif, negatif, atau netral tanpa membaca satu per satu |
| Memetakan dimensi customer experience (CX) | Menemukan area layanan yang paling banyak menerima keluhan atau pujian |
| Mendukung pengambilan keputusan berbasis data | Menetapkan prioritas perbaikan, pengembangan fitur, serta strategi komunikasi pelanggan yang lebih tepat |

## Metodologi Singkat
1. **Data acquisition:** Scraping ulasan aplikasi Gojek dari Google Play Store menggunakan `google-play-scraper`.
2. **Pre-processing:** Pembersihan teks (lowercasing, penghapusan karakter khusus/URL, normalisasi singkatan, stopword removal) agar siap diproses model.
3. **Modeling Sentimen:** Klasifikasi positif/negatif/netral dengan IndoBERT (`mdhugol/indonesia-bert-sentiment-classification`).
4. **Modeling Dimensi Layanan:** Klasifikasi semi-supervised dimensi layanan menggunakan IndoBERT dengan label seperti *Marketing and Sales*, *Customer Support*, *Brand*, *Product and service portfolio*, *Billing, Charging and Cost Management*, dan *Service quality*.
5. **Modeling Topic:** Pemetaan topik utama per dimensi layanan dengan BERTopic untuk menemukan isu dominan.
6. **Validation:** Evaluasi model klasifikasi menggunakan Confusion Matrix, Accuracy, Precision, Recall, dan F1 Score.
7. **Analysis:** Visualisasi (grafik tren, word cloud) serta interpretasi bisnis untuk menyusun rekomendasi perbaikan.

## Struktur Repositori
- `data/`: Dataset ulasan yang diperoleh dari Google Play Store (mentah/terproses).
- `notebooks/`: Notebook eksplorasi, eksperimen model, evaluasi, dan visualisasi.
- `README.md`: Dokumentasi proyek dan panduan umum.

## Kebutuhan Utama
- Python 3.10 atau lebih baru
- Pustaka kunci: `google-play-scraper`, `pandas`, `numpy`, `scikit-learn`, `transformers`, `torch`, `bertopic`, `matplotlib`, `seaborn`, `wordcloud`
- GPU (opsional) untuk mempercepat pelatihan atau inferensi model berbasis transformer.

## Cara Memulai Singkat
1. Buat dan aktifkan environment Python (contoh: `python -m venv .venv && source .venv/bin/activate`).
2. Instal dependensi utama: `pip install google-play-scraper pandas numpy scikit-learn transformers torch bertopic matplotlib seaborn wordcloud`.
3. Jalankan notebook pada folder `notebooks/` untuk proses scraping, pra-pemrosesan, pelatihan model, dan analisis.

## Tim & Pembagian Tugas
| Tugas | Anggota | Deskripsi |
| --- | --- | --- |
| Data Acquisition | Navaly, Muhammad Rasyid Ismail | Scraping ulasan pengguna Gojek di Google Play Store menggunakan `google-play-scraper`. |
| Pre-processing Data | Razita Hafsah Januar, Lydia Cong Andinata | Pembersihan dan transformasi data teks mentah untuk mengurangi noise sebelum modeling. |
| Modeling - Sentiment | Muhammad Rasyid Ismail | Membangun model klasifikasi sentimen (positif/negatif/netral) dengan IndoBERT `mdhugol/indonesia-bert-sentiment-classification`. |
| Modeling - Dimensi Layanan | Vernando | Klasifikasi dimensi layanan menggunakan IndoBERT dengan pendekatan semi-supervised. |
| Modeling - Topic | Navaly | Menemukan topik utama per dimensi layanan menggunakan BERTopic. |
| Validation | Lydia Cong Andinata, Razita Hafsah Januar | Validasi model klasifikasi (Confusion Matrix, Accuracy, Precision, Recall, F1 Score). |
| Analysis | Vernando | Menyusun visualisasi (grafik, word cloud) dan insight bisnis dari hasil model. |

## Kontribusi & Lisensi
Kontribusi terbuka untuk perbaikan kode, dokumentasi, maupun analisis tambahan. Harap buat branch baru dan ajukan pull request. Lisensi mengikuti ketentuan yang berlaku di repository ini.
