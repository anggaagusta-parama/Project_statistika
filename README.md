# Tugas Analisis Statistik: Deskriptif, Korelasi, dan Regresi

## 1. Informasi Penyusun

- **Nama:** `[PUTU ANGGA AGUSTA PARAMA SANDI]`
- **NIM:** `[2515091115]`
- **Program Studi:** `[SISTEMINFORMASI]`
- **Mata Kuliah:** Statistika dan Probabilitas

---

## 2. Deskripsi Proyek

Pada bagian ini, jelaskan secara singkat dataset yang Anda gunakan. Apa saja variabel di dalamnya? Apa tujuan dari analisis yang Anda lakukan?

*Contoh:*
> Dataset yang digunakan adalah data `data_startup_saas.csv` yang berisi informasi tentang `File data_startup_saas.csv berisi data kinerja 650+ startup SaaS di Indonesia, dengan kolom utama: NamaStartup (seperti Startup1 hingga Startup650), KategoriLayanan (Keuangan, Proyek, SDM, Pemasaran, CRM), PendapatanTahunanMiliarIDR (1-66 miliar IDR), BiayaAkuisisiPelangganJutaIDR (2-68 juta IDR, ada "NA"), NilaiPelangganJutaIDR (5-205 juta IDR), dan TingkatChurnPersen (-50 hingga 15%).  Data ini berguna untuk analisis bisnis SaaS, menunjukkan tren pendapatan naik dan churn bervariasi.`. Variabel kunci dalam dataset ini meliputi `Pendapatan_Tahunan_Miliar_IDR`, `Biaya_Akuisisi_Pelanggan_Juta_IDR`, dan `Nilai_Pelanggan_Juta_IDR`. Tujuan dari proyek ini adalah untuk memahami karakteristik data melalui statistik deskriptif, menguji hubungan antara `Pendapatan_Tahunan_Miliar_IDR` dan `Biaya_Akuisisi_Pelanggan_Juta_IDR` melalui analisis korelasi, serta memprediksi `Nilai_Pelanggan_Juta_IDR` menggunakan `Pendapatan_Tahunan_Miliar_IDR` sebagai prediktor melalui analisis regresi.

---

## 3. Struktur Proyek

Proyek ini diorganisir ke dalam beberapa folder:
- `/data`: Berisi dataset mentah yang digunakan untuk analisis.
- `/scripts`: Berisi semua skrip R yang digunakan dalam analisis, diurutkan berdasarkan alur kerja.
- `/results`: Berisi output dari analisis, seperti plot, gambar, atau tabel ringkasan.

---

## 4. Cara Menjalankan Analisis

Untuk mereproduksi hasil analisis ini, ikuti langkah-langkah berikut:
1. Pastikan Anda memiliki R dan RStudio terinstal.
2. Buka proyek R ini di RStudio.
3. Instal paket yang diperlukan dengan menjalankan perintah berikut di konsol R:
   ```R
   # install.packages(c("tidyverse", "corrplot", "knitr"))
   ```
4. Jalankan skrip di dalam folder `/scripts` secara berurutan, mulai dari `01_data_preparation.R` hingga `05_analisis_regresi.R`.

---

## 5. Hasil dan Interpretasi

Di bagian ini, mahasiswa diharapkan untuk menyajikan dan menginterpretasikan hasil dari setiap tahap analisis.

### 5.1. Statistik Deskriptif
- **Ukuran Pemusatan (Mean, Median, Modus):**
  - *Tabel atau ringkasan...*
  - Mean = 33.5
  - Median = 33.08
  - Modus = 3.21
  - *Interpretasi:* Jelaskan apa arti dari nilai-nilai tersebut terkait dengan data Anda.
  - Data Anda memiliki nilai rata-rata (Mean) sebesar 33.5, yang menunjukkan pusat massa data secara keseluruhan. Nilai ini didukung oleh Median sebesar 33.08, yang berarti tepat separuh dari data Anda berada di bawah angka tersebut dan separuhnya lagi berada di atasnya. Mengingat nilai Mean dan Median sangat berdekatan, data Anda cenderung memiliki distribusi yang cukup stabil di sekitar angka 33. Namun, terdapat anomali pada Modus sebesar 3.21, yang merupakan nilai yang paling sering muncul. Perbedaan drastis antara Modus dengan nilai tengah lainnya mengindikasikan adanya sebaran data yang sangat menceng atau keberadaan sekelompok nilai rendah yang frekuensinya sangat dominan dibandingkan nilai lainnya dalam kumpulan data tersebut.
- **Ukuran Sebaran (Standar Deviasi, Range, Kuartil):**
  - *Tabel atau ringkasan...*
  - Standar Deviasi =20.03
  - Range = 2.56 - 68.77
  - Kuartil = Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
              2.56   15.23   33.08   33.50   50.92   68.77 
  - *Interpretasi:* Jelaskan seberapa menyebar data Anda berdasarkan nilai-nilai ini.
  - Data ini aslinya berantakan dan nggak kompak. Jarak antara angka paling kecil (2.56) sama yang paling gede (68.77) itu jauh banget, hampir nggak ada nyambung-nyambungnya. Standar deviasinya yang sampai 20.03 itu jadi bukti kalau data kamu mencar ke mana-mana, nggak ngumpul di satu titik. seperempat data masih "nyangkut" di angka kecil belasan, tapi seperempat sisanya sudah lari jauh ke angka 50-an ke atas. Intinya, isi data ini sangat beragam—ada yang kecil banget dan ada yang besar banget—jadi nggak bisa dibilang seragam atau konsisten.
- **Visualisasi (Histogram/Boxplot):**
  - *Sematkan gambar plot dari folder /results...*
  - *Interpretasi:* Jelaskan wawasan apa yang Anda dapatkan dari bentuk distribusi data.

### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - *Nilai p-value...*
  - *Interpretasi:* Apakah data Anda terdistribusi normal berdasarkan hasil uji? Apa implikasinya?
- **Plot Q-Q:**
  - *Sematkan gambar plot dari folder /results...*
  - *Interpretasi:* Apakah titik-titik data mengikuti garis lurus? Apa artinya?

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - *Nilai r...*
  - *Interpretasi:* Seberapa kuat dan apa arah hubungan antara dua variabel yang Anda uji? (misalnya, korelasi positif kuat, negatif lemah, atau tidak ada korelasi).
- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - *Interpretasi:* Apakah pola pada scatter plot mendukung hasil koefisien korelasi?

### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = b0 + b1*X*
  - *Interpretasi:* Jelaskan arti dari koefisien intercept (b0) dan slope (b1) dalam konteks data Anda.
- **Evaluasi Model (R-squared):**
  - *Nilai R-squared...*
  - *Interpretasi:* Berapa persen variasi dari variabel dependen yang dapat dijelaskan oleh model regresi Anda?
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - *Interpretasi:* Jelaskan bagaimana garis regresi merepresentasikan hubungan antara variabel.

---

## 6. Kesimpulan

Rangkum temuan utama dari analisis Anda dalam beberapa kalimat. Apa wawasan paling penting yang Anda peroleh?
