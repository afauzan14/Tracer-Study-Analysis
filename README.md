# 🎓 Alumni Tracer Study Analytics & Career Clustering Using K-Prototypes

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Clustering](https://img.shields.io/badge/Algorithm-K--Prototypes-blue?style=for-the-badge)
![Domain](https://img.shields.io/badge/Domain-Higher%20Education%20Analytics-success?style=for-the-badge)

---

## 📌 Ringkasan Proyek & Business Understanding

*Tracer Study* (studi penelusuran alumni) merupakan instrumen krusial bagi perguruan tinggi untuk mengukur mutu luaran pendidikan, relevansi kurikulum terhadap kebutuhan industri, serta pemenuhan **Indikator Kinerja Utama (IKU)** perguruan tinggi. Namun, data survei alumni sering kali berupa data campuran (*mixed data types*) yang memuat isian teks bebas, format tanggal tidak standar, dan ketidakseragaman pengisian kuesioner.

Proyek ini menganalisis data survei alumni Fakultas Sains dan Teknologi (FST) UIN Syarif Hidayatullah Jakarta lintas 7 program studi (Teknik Informatika, Agribisnis, Biologi, Kimia, Fisika, Matematika, dan Teknik Pertambangan) dengan objektif:
1. **Pembersihan & Rekayasa Fitur Data Survei:** Mengeliminasi anomali isian survei bebas dan merekayasa fitur analitis baru seperti masa tunggu kerja, durasi studi, dan status kebekerjaan.
2. **Evaluasi Relevansi Kurikulum & Lapangan Kerja:** Mengukur tingkat keselarasan vertikal (*curriculum relevance*) dan horizontal (*field-of-study alignment*) terhadap profil karier alumni.
3. **Segmentasi Alumni Berbasis Machine Learning:** Mengelompokkan profil alumni menggunakan algoritma **K-Prototypes Clustering** yang mampu memproses atribut numerik dan kategorik secara simultan.
4. **Rekomendasi Kebijakan Fakultas & Program Studi:** Memberikan panduan strategis berbasis data untuk percepatan kelulusan, penyerapan kerja lulusan (*graduate employability*), serta inkubasi karier dan studi lanjut.

---

## 🔬 Metodologi Analisis & Pemodelan Data

1. **Data Preprocessing & Text Normalization:**
   * **Pembersihan Noise Teks:** Melakukan standarisasi isian manual kuesioner pada variabel waktu mendapatkan pekerjaan, nominal penghasilan bulanan, nama perguruan tinggi studi lanjut, dan penamaan program studi.
   * **Filtering Outlier & Duplikasi:** Menghapus baris ganda hasil submission berulang serta menangani *outlier* waktu tunggu dan lama studi yang tidak realistis.
2. **Feature Engineering:**
   * `lama studi`: Menghitung total durasi studi sarjana berdasarkan tahun masuk dan tahun wisuda.
   * `status bekerja`: Standardisasi kategori status alumni (*Bekerja, Belum Bekerja, Melanjutkan Studi, Wirausaha*).
   * Transformasi skala ordinal untuk persepsi kesesuaian kurikulum dan bidang ilmu (skala Likert 1–5).
3. **Machine Learning: K-Prototypes Clustering:**
   * Algoritma **K-Prototypes** dipilih karena dataset survei memadukan fitur **numerik** (*penghasilan, lama studi*) dan fitur **kategorik** (*program studi, status bekerja, waktu dapat kerja, keselarasan kurikulum*).
   * Jarak numerik dihitung menggunakan *Euclidean distance*, sedangkan ketidaksamaan variabel kategorik diukur menggunakan *simple matching dissimilarity*.
   * Jumlah klaster optimal ditentukan sebanyak **$k = 3$** untuk segmentasi profil karier yang *actionable*.

---

## 📊 Temuan Kunci (Key Findings)

### 1. Komparasi Relevansi & Hasil Karier Berdasarkan Program Studi

| Program Studi | Karakteristik Masa Studi | Profil Waktu Tunggu Kerja | Kesesuaian Kurikulum & Bidang Ilmu |
| :--- | :--- | :--- | :--- |
| **Teknik Informatika** | Cenderung tepat waktu (4–4,5 tahun) | Sangat cepat (< 3 bulan); tingkat serapan kerja langsung tertinggi | Sangat tinggi; kompetensi teknis sangat selaras dengan kebutuhan industri teknologi |
| **Matematika & Fisika** | 4 hingga 5 tahun | Relatif singkat (3–6 bulan); serapan kuat di sektor analitik & edukasi | Relevansi tinggi di bidang komputasi, aktuaria, dan analisis data |
| **Biologi & Kimia** | 4 hingga 5 tahun | Cepat s.d. menengah; persentase tertinggi melanjutkan studi lanjut (S2) | Sangat sesuai dengan bidang riset laboratorium, QA/QC, dan akademik |
| **Teknik Pertambangan**| 4,5 hingga 5,5 tahun | Mayoritas terserap di sektor industri energi/sumber daya | Tingkat kesesuaian keahlian spesifik tinggi dengan rentang gaji kompetitif |
| **Agribisnis** | Cenderung lebih panjang (> 5 tahun) | Masa tunggu lebih panjang; proporsi pencari kerja aktif lebih besar | Penyerapan sektor agritech/perbankan terbuka, namun membutuhkan penguatan portofolio |

---

### 2. Profiling Segmentasi Klaster Alumni (K-Prototypes, $k = 3$)

| Profil Klaster | Karakteristik Utama Klaster | Dominasi Program Studi | Status & Waktu Mendapatkan Kerja |
| :--- | :--- | :--- | :--- |
| **Cluster 1: Cepat Mendapatkan Pekerjaan** | • Lulusan tahun 2023 ke atas<br>• Rata-rata masa studi efisien<br>• Skor kesesuaian kurikulum & bidang tinggi (skor 4–5) | Teknik Informatika, Matematika, Biologi | • **> 90% Berstatus Sedang Bekerja**<br>• Waktu tunggu kerja: **< 3 bulan**<br>• Preferensi kuat pada sektor profesional swasta |
| **Cluster 2: Seimbang (Transisi Adaptif)** | • Didominasi lulusan tahun 2024 (wisuda pertengahan tahun)<br>• Sebagian besar memilih jalur karier profesional ketimbang wirausaha | Agribisnis, Biologi, Teknik Informatika | • **Proporsi berimbang** antara yang sudah mulai bekerja dan sedang aktif proses seleksi kerja<br>• Waktu tunggu: 0–6 bulan |
| **Cluster 3: Belum Bekerja / Eksplorasi** | • Didominasi wisudawan baru periode akhir 2024<br>• Sebagian memiliki rencana melanjutkan studi pascasarjana (S2) | Agribisnis, Biologi, Matematika | • **Mayoritas berstatus belum bekerja** karena masih berada di masa tunggu awal pascakelulusan<br>• Membutuhkan jembatan transisi karier |

---

## 💡 Rekomendasi Strategis untuk Fakultas & Program Studi

### 1. Intervensi Program Akselerasi Karier (*Career Acceleration*)
* **Bursa Kerja & Kemitraan Kampus Terfokus:** Membangun kemitraan strategis dengan industri untuk prodi dengan masa tunggu kerja lebih panjang (seperti Agribisnis) melalui program *campus hiring*, sertifikasi kompetensi digital, dan magang industri bersertifikat sebelum kelulusan.
* **Inkubasi Praktik Kewirausahaan:** Data menunjukkan minat wirausaha alumni masih tergolong rendah dibandingkan pekerja kantoran. Fakultas disarankan merombak kurikulum kewirausahaan menjadi *project-based incubator* yang memfasilitasi pendanaan rintisan usaha nyata.

### 2. Penyelarasan Kurikulum Berkelanjutan (*Curriculum-Industry Alignment*)
* Mempertahankan kurikulum adaptif pada prodi dengan tingkat *employability* tinggi (TI & Matematika) serta memperkuat *soft skills* (komunikasi bisnis, kemampuan bahasa asing, dan pemecahan masalah) yang menjadi faktor diferensiasi saat wawancara kerja.

### 3. Fasilitas & Bimbingan Studi Lanjut (S2/S3)
* Mengingat alumni dari rumpun sains murni (Biologi, Kimia, Fisika) memiliki minat tinggi untuk studi lanjut baik di dalam maupun luar negeri, fakultas perlu menyediakan *advisory desk* untuk persiapan beasiswa, penulisan proposal riset, dan publikasi ilmiah terindeks sejak semester akhir.
