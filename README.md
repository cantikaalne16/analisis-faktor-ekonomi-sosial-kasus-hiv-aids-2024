# Analisis Faktor Ekonomi Sosial Kasus HIV & AIDS 2024
## Project Akhir Data Wrangling Semester Gasal 2025/2026 S1 Sains Data Universitas Negeri Surabaya

### **1. Deskripsi Project:**
Project ini melakukan proses data wrangling terhadap beberapa dataset (PDF dan CSV) yang berkaitan dengan kasus HIV/AIDS serta faktor sosial ekonomi di Indonesia tahun 2024. Proses meliputi scraping PDF, data cleaning, integrasi dataset, dan eksplorasi sederhana.

### **2. Fitur:**
- Melakukan scraping data HIV/AIDS dari file PDF menggunakan PyMuPDF.
- Mengekstrak tabel PDF dengan pdfplumber & Tabula-py
- Menggabungkan dataset sosial-ekonomi dari berbagai sumber:
    1. Data jumlah kasus HIV & AIDS di Indonesia tahun 2024 >> https://kemkes.go.id/id/profil-kesehatan-indonesia-2024
    2. Data jumlah penduduk miskin (ribu) di Indonesia tahun 2024 >> https://www.bps.go.id/id/pressrelease/2025/01/15/2401/persentase-penduduk-miskin-september-2024-turun-menjadi-8-57-persen-.html
    3. Data indeks tingkat pengangguran terbuka (%) di Indonesia tahun 2024 >> https://opendata.jabarprov.go.id/id/dataset/tingkat-pengangguran-terbuka-berdasarkan-provinsi--di-indonesia 
    4. Data rata-rata lama sekolah (Tahun) di Indonesia tahun 2024 >> https://www.bps.go.id/id/statistics-table/2/NDE1IzI=/-metode-baru--rata-rata-lama-sekolah--tahun-.html
- Melakukan data cleaning dan standarisasi kolom.
- Pembuatan variabel Rasio HIV/AIDS.
- Eksplorasi data (EDA) dan visualisasi.

### **3. Struktur Folder:**
📂 project-data-wrangling-hiv-aids-2024
<br>
│
<br>
|--- 📁 data raw
<br>
|   |-- Profil Kesehatan Indonesia 2024.pdf
<br>
|   |-- Profile Kemiskinan di Indonesia.pdf
<br>
|   |-- Rata Rata Lama Sekolah 2024.csv
<br>
|   |-- Tingkat Pengangguran 2024.csv
<br>
|   |-- scrape_aids_raw.csv
<br>
|   |-- scrape_hiv_raw.csv
<br>
|   |__ scrape_kemiskinan_raw.csv
<br>
│
<br>
|--- 📁 data clean
<br>
│   |-- data_hiv_clean.csv
<br>
│   |-- data_aids_clean.csv
<br>
│   |-- data_kemiskinan_clean.csv
<br>
│   |-- data_pengangguran_clean.csv
<br>
│   |__ data_lama_sekolah_clean.csv
<br>
│
<br>
|--- 📁 data final
<br>
│   |__ DATA FINAL.csv
<br>
│
<br>
|--- 📁 dokumentasi pipeline
<br>
│   |__ pipeline.png
<br>
│
<br>
|--- 📁 laporan & ppt
<br>
|   |__ LAPORAN KELOMPOK 26.pdf
<br>
|   |__ PPT KELOMPOK 26.pptx
<br>
│
<br>
|--- 📁 source code python
<br>
|   |__ SOURCE CODE_KELOMPOK 26.ipynb
<br>
│   
<br>
│--- 📁 visualisasi
<br>
|   |-- boxplot_sosialekonomi_hivaids.png
<br>
|   |-- barplot_rasio_hivaids.png
<br>
|   |-- heatmap_sosialekonomi_hivaids.png
<br>
|   |__ scatterplot_sosialekonomi_hivaids.png
<br>
|
<br>
|___ README.md

### **4. Pipeline Wrangling:**
Berikut tahapan lengkapnya sesuai dengan kode:
<br>
#### 4.1 Pengambilan Data
a. Scraping Kasus HIV dari PDF
    Menggunakan tabula-py pada halaman 472 di dokumen Profil Kesehatan Indonesia 2024. Data diekstraksi ke CSV "scrape_hiv_raw.csv" pada folder "data clean".
<br>
<br>
b. Scraping Kasus AIDS dari PDF
    Menggunakan tabula-py pada halaman 475 di dokumen Profil Kesehatan Indonesia 2024. Data diekstraksi ke CSV "scrape_aids_raw.csv" pada folder "data clean".
<br>
<br>
c. Scraping Data Kemiskinan dari PDF
    Menggunakan pdfplumber pada halaman 9 di dokumen Profile Kemiskinan di Indonesia.pdf. Data diekstraksi ke CSV "scrape_kemiskinan_raw.csv" pada folder "data clean".
<br>
<br>
d. Load Data Indeks Tingkat Pengangguran Terbuka (TPT) dan Rata-rata Lama Sekolah, tersimpan pada folder "data clean".

#### 4.2 Data Cleaning
Cleaning mencakup:
- Menghapus baris header ganda
- Filter data yang relevan
- Menghapus titik pada angka seperti "1.234" menjadi "1234"
- Uppercase seluruh nama provinsi
- File output setelah cleaning disimpan dalam folder data clean:
<br>
  |--- 📁 data clean
  <br>
      |-- data_hiv_clean.csv
  <br>
      |-- data_aids_clean.csv
  <br>
      |-- data_kemiskinan_clean.csv
  <br>
      |-- data_pengangguran_clean.csv
  <br>
      |-- data_lama_sekolah_clean.csv
  
#### 4.3 Integrasi
Data cleaning HIV, AIDS, Kemiskinan, Pengangguran, dan Rata-Rata Lama Sekolah digabung dengan cara merge menggunakan provinsi sebagai common key.

#### 4.4 Exploratory Data Analysis (EDA)
a. Cek missing value
<br>
<br>
b. Cek data duplicate
<br>
<br>
c. Cek tipe data
<br>
<br>
d. Cek statistik deskriptif
<br>
<br>
e. Deteksi outlier
<br>
    Menggunakan boxplot untuk mengidentifikasi provinsi yang memiliki nilai ekstrem pada variabel sosial ekonomi dan jumlah kasus HIV/AIDS. Menyimpan boxplot di folder "visualisasi" nama file "boxplot_sosialekonomi_hivaids.png"
<br>
<br>
f. Menghitung rasio kasus HIV & AIDS
<br>
    Membuat variabel baru berupa rasio Kasus HIV / Kasus AIDS untuk melihat proporsi penyebaran di setiap provinsi. Membuat "visualisasi" bar plot top 10 provinsi dengan rasio tertinggi ke terendah dan disimpan di folder visualisasi nama file "barplot_rasio_hivaids.png"
<br>
<br>
g. Visualisasi heatmap korelasi
<br>
    Menghasilkan heatmap antar variabel sosial-ekonomi untuk mengidentifikasi hubungan awal antara:
- Jumlah penduduk miskin
- Indeks TPT
- Rata-rata lama sekolah
- Jumlah Kasus HIV
- Jumlah Kasus AIDS
<br>
    Menyimpan visualisasi heatmap di folder "visualisasi" dengan nama file "heatmap_sosialekonomi_hivaids.png".
<br>
<br>
h. Visualisasi scatter plot
<br>
    Visualisasi hubungan antar variabel:
  <br>
- Jumlah penduduk miskin vs jumlah kasus HIV
- Indeks TPT vs jumlah kasus HIV
- Rata rata lama sekolah vs jumlah kasus HIV
- Jumlah penduduk miskin vs jumlah kasus AIDS
- Indeks TPT vs jumlah kasus AIDS
- Rata rata lama sekolah vs jumlah kasus AIDS
  Menyimpan visualisasi heatmap di folder "visualisasi" dengan nama file "scatterplot_sosialekonomi_hivaids.png". 
<br>
<br>
i. Peringkat faktor sosial ekonomi
<br>
    Menyusun daftar provinsi berdasarkan:
  <br>
- Provinsi dengan jumlah penduduk miskin terbanyak
- Provinsi indeks TPT tertinggi
- Provinsi dengan rata rata lama sekolah terendah
- Provinsi dengan rasio HIV & AIDS tertinggi
<br>
<br>

### **Terima kasih kepada dosen pengampu Bu Ulfa Siti Nuraini, S.Stat., M.Stat. atas bimbingannya selama perkuliahan🙏.**

### Disusun Oleh:
- #### Adisti Eka Nabila (24031554119)
- #### Cantika Latifatul Nur Ella (24031554023)
