# Proyek Data Science: Prediksi Attrition Karyawan

## 1. Business Understanding
Jaya Jaya Maju adalah perusahaan besar dengan lebih dari 1000 karyawan yang tersebar di berbagai wilayah. Perusahaan ini menghadapi masalah tinggi dalam attrition rate (rasio keluar-masuknya karyawan) yang melebihi 10%. Oleh karena itu, departemen HR memerlukan bantuan untuk mengidentifikasi faktor-faktor yang mempengaruhi karyawan untuk keluar dari perusahaan dan untuk memonitor faktor-faktor tersebut. Proyek ini bertujuan untuk membangun model machine learning yang dapat memprediksi apakah seorang karyawan akan keluar atau tetap bekerja, dengan tujuan membantu mengurangi tingkat attrition.

## 2. Data Understanding
Data yang digunakan dalam proyek ini mencakup berbagai atribut yang menggambarkan profil karyawan, seperti:

### Demografi:
- Usia
- Jenis kelamin
- Status perkawinan

### Kinerja Kerja:
- Kepuasan kerja
- Keterlibatan pekerjaan
- Gaji

### Faktor Lain:
- Jarak rumah ke kantor
- Tingkat pendidikan
- Jabatan

Fitur utama dalam dataset ini adalah kolom **Attrition** yang menunjukkan apakah karyawan keluar (1) atau tetap (0), yang akan dijadikan sebagai target variabel.

## 3. Exploratory Data Analysis (EDA)
Proses eksplorasi data dilakukan untuk memahami distribusi data dan hubungan antar variabel.

### Distribusi Attrition:
Hasil menunjukkan bahwa sebagian besar karyawan tidak mengalami attrition, dengan proporsi kecil yang keluar dari perusahaan.

### Distribusi JobRole:
Visualisasi distribusi pekerjaan menunjukkan bahwa sebagian besar karyawan berada di posisi "Sales Executive" dan "Research Scientist".

### Distribusi Department:
Departemen yang memiliki jumlah karyawan terbanyak adalah "Sales" dan "Research & Development".

### OverTime:
Lebih banyak karyawan yang bekerja lembur, namun hubungan antara overtime dan attrition perlu dianalisis lebih lanjut.

### Boxplot antara Attrition dan MonthlyIncome:
Boxplot menunjukkan bahwa karyawan yang keluar memiliki variasi penghasilan yang lebih tinggi daripada mereka yang tetap bekerja.

### Korelasi antar fitur numerik:
Korelasi antar fitur numerik juga dianalisis, meskipun sebagian besar hubungan tidak terlalu kuat.

## 4. Data Preparation
Data dibersihkan dengan menghapus baris yang memiliki nilai missing pada kolom **Attrition**. Fitur kategori seperti **Department** dan **JobRole** diubah menjadi format numerik dengan teknik encoding menggunakan **LabelEncoder**.

## 5. Modeling
Setelah melakukan persiapan data, tahap berikutnya adalah pemilihan model. Menggunakan **Random Forest** sebagai model machine learning, yang dikenal efektif untuk klasifikasi dengan banyak fitur dan mampu menangani data yang tidak seimbang.

### Train-Test Split:
Data dibagi menjadi data latih (80%) dan data uji (20%).

### SMOTE (Synthetic Minority Over-sampling Technique):
SMOTE diterapkan untuk menangani ketidakseimbangan kelas antara karyawan yang keluar dan yang tetap.

### Hyperparameter Tuning:
Dilakukan menggunakan **GridSearchCV** untuk menemukan parameter terbaik bagi model Random Forest, seperti jumlah pohon keputusan (n_estimators), kedalaman maksimum pohon (max_depth), dan jumlah sampel minimum pada setiap split (min_samples_split).

## 6. Evaluation
Setelah model dilatih dengan menggunakan data latih yang sudah disesuaikan dengan SMOTE dan parameter terbaik, model diuji pada data uji.

### Hasil evaluasi menunjukkan:
- **Accuracy:** Model mencapai akurasi sekitar 85%. Ini menunjukkan bahwa model cukup baik dalam memprediksi apakah seorang karyawan akan keluar atau tetap bekerja.
- **Precision:** Precision untuk kelas 0 (karyawan tetap) lebih tinggi dibandingkan kelas 1 (karyawan keluar), yang menunjukkan model cenderung lebih akurat dalam memprediksi karyawan yang tetap.
- **Recall:** Recall untuk kelas 1 (karyawan keluar) relatif rendah, menunjukkan bahwa model belum optimal dalam menangani kasus karyawan keluar.
- **F1-Score:** F1-Score menunjukkan performa model yang seimbang antara precision dan recall, namun tetap perlu peningkatan pada kelas 1.

## 7. Kesimpulan dan Saran untuk HR
Berdasarkan hasil analisis dan evaluasi model, terdapat beberapa faktor yang berpengaruh terhadap keputusan karyawan untuk keluar atau tetap bekerja di perusahaan, di antaranya:
1. **JobSatisfaction (Kepuasan Kerja):** Karyawan yang merasa kurang puas dengan pekerjaan mereka lebih cenderung untuk keluar. Oleh karena itu, departemen HR dapat memantau tingkat kepuasan kerja secara berkala dan mengambil langkah-langkah untuk meningkatkan pengalaman kerja.
2. **StockOptionLevel (Tingkat Opsi Saham):** Karyawan dengan opsi saham yang lebih tinggi memiliki kecenderungan lebih besar untuk tetap bekerja. Program insentif saham bisa menjadi salah satu cara untuk meningkatkan retensi.
3. **MonthlyIncome (Penghasilan Bulanan):** Penghasilan bulanan berperan besar dalam keputusan karyawan untuk bertahan. Oleh karena itu, departemen HR perlu memastikan struktur gaji yang kompetitif dan mempertimbangkan kenaikan gaji bagi karyawan yang berisiko.
4. **JobInvolvement (Keterlibatan Pekerjaan):** Karyawan yang lebih terlibat dalam pekerjaan mereka lebih cenderung untuk tetap bertahan. Departemen HR bisa meningkatkan keterlibatan ini melalui peluang pengembangan karier atau proyek-proyek yang lebih menantang.

### **Evaluasi Model:**
Model yang telah dibangun mencapai akurasi sekitar 85%, namun recall untuk kelas "karyawan keluar" (attrition) masih relatif rendah. Ini berarti model kurang sensitif dalam mendeteksi karyawan yang akan keluar, yang merupakan masalah utama dalam mengurangi attrition. Hal ini menandakan bahwa meskipun model cukup baik, ada kebutuhan untuk **peningkatan recall** pada karyawan yang berisiko keluar.

### **Saran untuk HR:**
1. **Program Kepuasan Kerja:** Meningkatkan program kebijakan yang mendukung kepuasan kerja dan mendengarkan masukan dari karyawan untuk memperbaiki area-area yang membuat mereka tidak puas.
2. **Analisis Penghasilan dan Insentif:** Melakukan peninjauan terhadap penghasilan bulanan dan mempertimbangkan bonus atau program insentif lainnya untuk karyawan yang berisiko tinggi.
3. **Fokus pada Keterlibatan Karyawan:** Memberikan peluang bagi karyawan untuk terlibat lebih dalam dalam pekerjaan mereka, melalui pelatihan atau peran yang lebih menantang.
4. **Pemantauan Program Stock Option:** Meningkatkan program opsi saham atau tunjangan lainnya untuk memberikan motivasi lebih bagi karyawan agar tetap bekerja.

Dengan pendekatan ini, HR dapat memanfaatkan hasil analisis untuk mengambil langkah-langkah yang lebih tepat dalam mengurangi tingkat attrition dan mempertahankan karyawan berkinerja tinggi.

## 8. Business Dashboard
Untuk mendukung proses pemantauan dan pengambilan keputusan oleh departemen HR, telah dibuat **dashboard bisnis** menggunakan **Metabase**. Dashboard ini berisi beberapa visualisasi utama, antara lain:

**Tujuan Dashboard**
Dashboard ini bertujuan membantu tim HR untuk:

- Memantau distribusi attrition berdasarkan berbagai atribut
- Mengidentifikasi pola-pola signifikan
- Mengambil keputusan berbasis data untuk mengurangi attrition

**Visualisasi pada Dashboard**

- OverTime vs Attrition: Karyawan yang lembur memiliki resign rate lebih tinggi (31%) dibanding yang tidak lembur (11%).
- Attrition per JobRole: "Laboratory Technician" dan "Sales Executive" mendominasi attrition.
- Attrition per Department: Departemen Sales dan R&D punya attrition tertinggi.
- Monthly Income vs Attrition: Rata-rata gaji lebih rendah pada yang resign.
- Job Satisfaction vs Attrition: Skor kepuasan kerja rendah (1-2) dominan pada yang resign.
- Stock Option vs Attrition: Karyawan dengan opsi saham rendah lebih banyak resign.
- Attrition vs Tenure Group: Masa kerja 0–2 tahun paling tinggi tingkat attrition-nya.
- Distance from Home: Tidak terlalu signifikan perbedaannya.
- Proporsi Resign vs Stay: Visual donut chart menunjukkan 16.9% resign.
- Analisi Korelasi : 

| Variabel                   | Nilai Korelasi | Interpretasi                                                                 |
|----------------------------|----------------|------------------------------------------------------------------------------|
| Age                        | -0.17          | Semakin tua usia karyawan, semakin kecil kemungkinan mereka untuk keluar.   |
| MonthlyIncome              | -0.16          | Semakin tinggi penghasilan bulanan, semakin kecil kemungkinan untuk resign. |
| YearsAtCompany             | -0.14          | Karyawan yang lebih lama bekerja cenderung lebih setia.                     |
| TotalWorkingYears          | -0.18          | Semakin banyak pengalaman kerja, makin kecil kemungkinan attrition.         |
| DistanceFromHome           | 0.078          | Jarak rumah tidak terlalu memengaruhi keputusan resign.                     |
| NumCompaniesWorked         | 0.037          | Pengaruh jumlah perusahaan sebelumnya sangat kecil terhadap attrition.      |
| PercentSalaryHike          | 0.0049         | Hampir tidak ada pengaruh dari kenaikan gaji tahunan.                       |
| TrainingTimesLastYear      | -0.048         | Sedikit pengaruh negatif, tapi sangat kecil terhadap keputusan keluar.      |

## Kesimpulan dari analisis korelasi terhadap Attrition
- Faktor-faktor yang paling berkorelasi negatif (walaupun tidak terlalu kuat) dengan attrition adalah: TotalWorkingYears, Age, dan MonthlyIncome
- Artinya, karyawan dengan pengalaman lebih, usia lebih tua, dan gaji lebih tinggi cenderung lebih loyal.
- Sementara variabel seperti DistanceFromHome, Training, dan SalaryHike memiliki pengaruh yang sangat kecil terhadap keputusan resign.


### Akses Dashboard
- **Email:** root@mail.com
- **Password:** root123

### Ekspor Database Metabase
Untuk menjaga konfigurasi dashboard dan query yang telah dibuat, database Metabase telah diekspor menggunakan perintah berikut:
```bash
docker cp metabase:/metabase.db/metabase.db.mv.db ./
```





