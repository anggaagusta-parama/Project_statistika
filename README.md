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
  - ![alt text](https://github.com/anggaagusta-parama/Project_statistika/blob/main/results/boxplot_Biaya_Akuisisi_Pelanggan_Juta_IDR.png)
  - *Interpretasi:* Jelaskan wawasan apa yang Anda dapatkan dari bentuk distribusi data.
  - Berdasarkan boxplot Biaya_Akuisisi_Pelanggan_Juta_IDR, dapat disimpulkan bahwa distribusi data menunjukkan variasi biaya akuisisi pelanggan yang cukup besar. Nilai median berada di sekitar 30 juta IDR, yang menandakan bahwa biaya akuisisi pelanggan yang paling umum berada pada kisaran tersebut. Rentang antar kuartil yang lebar, yaitu kira-kira dari 15 juta hingga 50 juta IDR, menunjukkan bahwa biaya akuisisi tidak konsisten dan dapat berbeda jauh antar periode atau strategi yang digunakan. Selain itu, whisker bagian atas yang lebih panjang dibandingkan bagian bawah mengindikasikan distribusi yang cenderung condong ke kanan, artinya terdapat beberapa kondisi di mana biaya akuisisi pelanggan relatif lebih tinggi dari nilai rata-rata. Meskipun demikian, tidak terlihat adanya outlier ekstrem, sehingga seluruh nilai biaya akuisisi masih berada dalam batas yang wajar dan dapat dianggap representatif untuk dianalisis lebih lanjut.

### 5.2. Uji Normalitas
- **Hasil Uji Shapiro-Wilk:**
  - *Nilai p-value...*
  - P-Velue = 4.138e-15
  - *Interpretasi:* Apakah data Anda terdistribusi normal berdasarkan hasil uji? Apa implikasinya?
  - Berdasarkan hasil uji normalitas yang menghasilkan p-value = 4,138 × 10⁻¹⁵, nilai tersebut jauh lebih kecil dari tingkat signifikansi yang umum digunakan (α = 0,05). Dengan demikian, hipotesis nol yang menyatakan bahwa data terdistribusi normal ditolak, sehingga dapat disimpulkan bahwa data tidak terdistribusi normal. Implikasinya, analisis statistik yang mensyaratkan asumsi normalitas, seperti uji t atau regresi linear klasik tanpa penyesuaian, berpotensi menghasilkan kesimpulan yang kurang akurat. Oleh karena itu, disarankan untuk menggunakan metode statistik nonparametrik, melakukan transformasi data (misalnya log atau square root), atau menerapkan pendekatan yang lebih robust agar hasil analisis tetap valid dan dapat dipercaya.
- **Plot Q-Q:**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/anggaagusta-parama/Project_statistika/blob/main/results/qqplot_Biaya_Akuisisi_Pelanggan_Juta_IDR.png)
  - *Interpretasi:* Apakah titik-titik data mengikuti garis lurus? Apa artinya?
  - Berdasarkan Q–Q plot yang ditampilkan, titik-titik data tidak sepenuhnya mengikuti garis lurus yang merepresentasikan distribusi normal teoretis. Terlihat adanya pola melengkung (kurva berbentuk S), di mana pada bagian kuantil rendah dan tinggi titik-titik menyimpang cukup jauh dari garis referensi. Hal ini menunjukkan bahwa distribusi data menyimpang dari normalitas, khususnya pada bagian ekor (tails) distribusi. Artinya, data Biaya Akuisisi Pelanggan tidak berdistribusi normal dan cenderung memiliki kemencengan (skewness) serta kemungkinan ekor yang lebih tebal dibandingkan distribusi normal. Temuan ini konsisten dengan hasil uji normalitas sebelumnya yang menghasilkan p-value sangat kecil, sehingga memperkuat kesimpulan bahwa asumsi normalitas tidak terpenuhi.

### 5.3. Analisis Korelasi
- **Nilai Koefisien Korelasi:**
  - *Nilai r...*
  - Koefisien Korelasi (r) = 0.996
  - *Interpretasi:* Seberapa kuat dan apa arah hubungan antara dua variabel yang Anda uji? (misalnya, korelasi positif kuat, negatif lemah, atau tidak ada korelasi).
  - Berdasarkan nilai koefisien korelasi r = 0,996, dapat disimpulkan bahwa terdapat hubungan yang sangat kuat dan positif antara kedua variabel yang diuji. Nilai r yang mendekati +1 menunjukkan bahwa ketika nilai satu variabel meningkat, variabel lainnya juga cenderung meningkat secara konsisten dengan pola yang hampir linear. Hubungan ini hampir sempurna, sehingga perubahan pada satu variabel sangat erat kaitannya dengan perubahan pada variabel lainnya. Dengan demikian, kedua variabel memiliki keterkaitan yang sangat tinggi, meskipun perlu diingat bahwa korelasi yang kuat tidak selalu menunjukkan adanya hubungan sebab–akibat.
- **Visualisasi (Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/anggaagusta-parama/Project_statistika/blob/main/results/scatterplot_Pendapatan_Tahunan_Miliar_IDR_vs_Biaya_Akuisisi_Pelanggan_Juta_IDR.png)
  - *Interpretasi:* Apakah pola pada scatter plot mendukung hasil koefisien korelasi?
  - pola pada scatter plot sangat mendukung hasil koefisien korelasi yang tinggi (r = 0,996). Titik-titik data terlihat membentuk pola yang hampir lurus dan meningkat, di mana semakin besar pendapatan tahunan, semakin besar pula biaya akuisisi pelanggan. Garis tren linear (garis merah) juga melewati sebagian besar titik data, menunjukkan hubungan linear yang sangat kuat antara kedua variabel. Penyebaran titik yang rapat di sekitar garis tren menandakan variasi yang kecil, sehingga memperkuat kesimpulan bahwa hubungan yang terjadi bukan hanya positif, tetapi juga sangat kuat dan konsisten, sesuai dengan nilai koefisien korelasi yang mendekati 1.

### 5.4. Analisis Regresi
- **Model Regresi:**
  - *Persamaan regresi: Y = b0 + b1*X*
  - Intercept (b0) = -1.06
  - Slope (b1) = 0.98
  - Y = -1.06 + 0.98X
  - *Interpretasi:* Jelaskan arti dari koefisien intercept (b0) dan slope (b1) dalam konteks data Anda.
  - Berdasarkan persamaan regresi Y = −1,06 + 0,98X, nilai intercept (b0 = −1,06) berarti bahwa saat pendapatan tahunan bernilai nol, model memprediksi biaya akuisisi pelanggan sebesar −1,06 juta IDR. Nilai ini tidak terlalu bermakna secara nyata dan hanya berfungsi sebagai penyesuaian matematis model. Sementara itu, slope (b1 = 0,98) menunjukkan bahwa setiap kenaikan 1 miliar IDR pendapatan tahunan akan meningkatkan biaya akuisisi pelanggan sekitar 0,98 juta IDR. Ini menandakan hubungan yang kuat dan searah antara pendapatan dan biaya akuisisi pelanggan.
- **Evaluasi Model (R-squared):**
  - *Nilai R-squared...*
  - Adjusted R-squared = 0.991 atau 99.1 %
  - *Interpretasi:* Berapa persen variasi dari variabel dependen yang dapat dijelaskan oleh model regresi Anda?
  - Nilai Adjusted R-squared sebesar 0,991 (99,1%) menunjukkan bahwa 99,1% variasi pada variabel dependen dapat dijelaskan oleh model regresi yang digunakan. Artinya, perubahan pada variabel independen sangat mampu menjelaskan perubahan pada variabel dependen, sedangkan sisanya sekitar 0,9% dipengaruhi oleh faktor lain di luar model.
- **Visualisasi (Garis Regresi pada Scatter Plot):**
  - *Sematkan gambar plot dari folder /results...*
  - ![alt text](https://github.com/anggaagusta-parama/Project_statistika/blob/main/results/plot_regresi_Biaya_Akuisisi_Pelanggan_Juta_IDR_vs_Pendapatan_Tahunan_Miliar_IDR.png)
  - *Interpretasi:* Jelaskan bagaimana garis regresi merepresentasikan hubungan antara variabel.
  - Garis regresi pada grafik menunjukkan hubungan linear dan positif antara biaya akuisisi pelanggan dan pendapatan tahunan. Garis yang menanjak menandakan bahwa semakin besar biaya akuisisi pelanggan, semakin tinggi pendapatan tahunan yang diperoleh. Titik-titik data yang berada sangat dekat dengan garis regresi menunjukkan bahwa hubungan kedua variabel ini sangat kuat, sehingga perubahan biaya akuisisi dapat dijelaskan dengan baik oleh perubahan pendapatan. Hal ini juga diperkuat oleh nilai Adjusted R-squared sebesar 0,991, yang menandakan bahwa garis regresi mampu merepresentasikan pola hubungan data secara sangat akurat.

---

## 6. Kesimpulan

Rangkum temuan utama dari analisis Anda dalam beberapa kalimat. Apa wawasan paling penting yang Anda peroleh?
