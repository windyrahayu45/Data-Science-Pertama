
# Proyek Akhir: Menyelesaikan Permasalahan Perusahaan Jaya Jaya Maju

## 1. Business Understanding

Jaya Jaya Maju adalah perusahaan besar di sektor edutech dengan lebih dari 1000 karyawan. Perusahaan menghadapi tingkat *attrition* (pergantian karyawan) yang tinggi, yakni mencapai lebih dari 10% per tahun. Hal ini mengganggu stabilitas operasional serta berdampak pada biaya rekrutmen dan pelatihan. Departemen HR membutuhkan bantuan untuk mengidentifikasi faktor-faktor yang menyebabkan karyawan keluar dan bagaimana memprediksi serta mengurangi risiko tersebut secara proaktif.

### Permasalahan Bisnis

- Tingginya tingkat attrition karyawan.
- Kurangnya wawasan berbasis data untuk memahami alasan di balik keputusan karyawan keluar.
- Ketidakefisienan dalam mendeteksi karyawan yang berisiko resign.
- Perlunya alat bantu visualisasi untuk mendukung pengambilan keputusan HR secara real-time.

### Cakupan Proyek

- Membangun model machine learning (Random Forest) untuk memprediksi attrition karyawan.
- Melakukan eksplorasi data (EDA) dan pembersihan data.
- Melakukan encoding pada fitur kategorikal.
- Melakukan evaluasi model dengan berbagai metrik.
- Membangun business dashboard berbasis Metabase untuk menyajikan hasil prediksi dan insight.

### Persiapan

**Sumber Data:**  
Dataset internal perusahaan Jaya Jaya Maju yang berisi data profil dan riwayat kerja karyawan.

**Setup Environment:**
```bash
# Environment setup
pip install pandas matplotlib seaborn scikit-learn imbalanced-learn
# Metabase setup (assumes Docker)
docker run -d -p 3000:3000 --name metabase metabase/metabase
```

---

## 2. Business Dashboard

Dashboard dibuat menggunakan **Metabase**, yang memungkinkan tim HR untuk memantau metrik utama terkait attrition, seperti:

- **Attrition Rate berdasarkan Job Role & Department**
- **Distribusi OverTime vs Attrition**
- **Distribusi Stock Option vs Attrition**
- **Distribusi Tenure Group vs Attrition**
- **Distance from Home vs Attrition**
- **Income dan JobSatisfaction vs Attrition**
- **Proporsi Resign dan Korelasi antar variabel**

### Tujuan Dashboard

- Memberikan insight mendalam terkait faktor-faktor penyebab attrition.
- Membantu HR dalam mengambil tindakan berbasis data.
- Monitoring berkelanjutan terhadap risiko resign.

### Akses Dashboard

- **Email:** root@mail.com  
- **Password:** root123

### Ekspor Database Metabase

Untuk menjaga konfigurasi dashboard dan query yang telah dibuat:
```bash
docker cp metabase:/metabase.db/metabase.db.mv.db ./
```

---

## 3. Conclusion

Model prediksi berhasil dibuat dengan akurasi ~85%, cukup andal untuk mendeteksi kemungkinan resign seorang karyawan. Beberapa faktor utama yang memengaruhi attrition antara lain:

- **Kepuasan kerja yang rendah**
- **Gaji bulanan yang tidak kompetitif**
- **Tingkat keterlibatan kerja yang rendah**
- **Kurangnya insentif seperti stock option**

Dengan mengintegrasikan dashboard visual ke dalam proses bisnis, tim HR dapat memonitor karyawan berisiko dan melakukan intervensi lebih awal.

---

### Rekomendasi Action Items

- **Tingkatkan program kepuasan kerja** secara berkala melalui survei dan feedback terbuka.
- **Tinjau ulang struktur kompensasi**, khususnya untuk posisi dengan risiko tinggi attrition.
- **Dorong keterlibatan kerja** melalui proyek kolaboratif dan pengembangan karier.
- **Perkuat program insentif saham** untuk meningkatkan loyalitas.
