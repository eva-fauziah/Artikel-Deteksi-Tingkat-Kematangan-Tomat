# Artikel-Deteksi-Tingkat-Kematangan-Tomat
Membuat artikel tentang hasil projek deteksi dan klasifikasi tingkat kematangan tomat
# Revolusi Agrikultur: Deteksi Otomatis Kematangan Tomat dengan Deep Learning YOLOv8 🍅

**Oleh:**  
Eva Fauziah  
Abdul Azis  
Komay Alamsyah  
Muhammad Fikri Firmansyah  

**Proyek Akhir Semester – Computer Vision**

---

## Abstrak
Di industri pangan skala besar, kualitas tomat sangat ditentukan oleh ketepatan waktu panen. Namun, proses penentuan tingkat kematangan tomat secara manual masih bergantung pada inspeksi visual manusia yang bersifat subjektif, tidak konsisten, dan memakan waktu. Kesalahan penilaian ini dapat menyebabkan kerugian ekonomi akibat panen yang terlalu dini atau terlambat.

Melalui proyek akhir semester ini, kami mengembangkan solusi **Smart Farming berbasis Computer Vision** dengan memanfaatkan algoritma **YOLOv8** untuk mendeteksi dan mengklasifikasikan kematangan tomat secara otomatis dan real-time. Sistem ini dirancang sebagai prototipe yang mampu meningkatkan efisiensi, konsistensi, dan objektivitas dalam proses penyortiran hasil pertanian.

---

## 1. Pemilihan Model: Mengapa YOLOv8m?
Pada penelitian ini, kami memilih arsitektur **YOLOv8m (Medium)** sebagai model utama. Dengan sekitar **25,8 juta parameter**, YOLOv8m menawarkan keseimbangan optimal antara akurasi deteksi yang tinggi dan kecepatan inferensi yang cukup ringan untuk implementasi di lingkungan industri.

YOLOv8 dikenal sebagai model deteksi objek yang efisien karena mampu melakukan proses deteksi dalam satu tahap (*single-stage detector*), sehingga sangat cocok untuk kebutuhan **real-time system** seperti mesin penyortir otomatis atau robot pemanen.

---

## 2. Analisis Data: Lebih dari Sekadar Gambar
Sebelum proses pelatihan model, kami melakukan analisis mendalam terhadap **177 citra digital**, dengan total **354 file** termasuk anotasi. Tahapan analisis ini bertujuan untuk memahami karakteristik visual tomat serta meningkatkan kualitas dataset.

### 2.1 Analisis Warna (RGB)
Hasil analisis menunjukkan bahwa:
- **Tomat matang** memiliki dominansi kanal **Merah (Red)** yang kuat.
*![Histogram RGB Tomat Matang](images/gambar warna garis tomat matang.jpg)*
- **Tomat mentah** lebih didominasi kanal **Hijau (Green)**.
  *![Histogram RGB Tomat Mentah](images/gambar warna garis tomat mentah.jpg)*
Perbedaan distribusi warna ini mencerminkan proses fisiologis dan biokimia selama pematangan tomat. Informasi warna tersebut menjadi fitur penting yang dimanfaatkan oleh model untuk membedakan tingkat kematangan.

### 2.2 Deteksi Tepi (Edge Detection)
![Deteksi Tepi Canny & Sobel](images/canny_sobel.png)
Kami menguji metode deteksi tepi seperti **Canny** dan **Sobel** untuk memahami kontur dan bentuk tomat. Analisis ini membantu memastikan bahwa model mampu mengenali batas objek dengan lebih baik, terutama pada kondisi lingkungan yang kompleks atau latar belakang yang bervariasi.

### 2.3 Dataset Seimbang
Dataset yang digunakan terdiri dari:
- **440 objek tomat mentah**
- **429 objek tomat matang**

Distribusi yang seimbang ini penting untuk menghindari bias model terhadap salah satu kelas dan meningkatkan kemampuan generalisasi sistem.

---

## 3. Proses Pelatihan dan Evaluasi Model
Model dilatih selama **150 epoch** dengan dukungan GPU. Evaluasi performa dilakukan menggunakan metrik **Intersection over Union (IoU)**, yang mengukur tingkat tumpang tindih antara bounding box prediksi dan ground truth:

\[
IoU = \frac{Area\ of\ Overlap}{Area\ of\ Union}
\]

### 3.1 Hasil Performa Model
Pengujian pada data yang benar-benar baru menunjukkan hasil yang sangat memuaskan:
- **Precision: 89,9%**  
  Hampir 90% prediksi yang dihasilkan model adalah benar.
- **Recall: 81%**  
  Model berhasil mendeteksi sebagian besar objek tomat yang ada.
- **mAP@0.5: 91,8%**  
  Menunjukkan akurasi deteksi yang sangat tinggi dan sebanding dengan model deteksi kematangan kelas *state-of-the-art*.

---

## 4. Keunggulan Sistem Real-Time
Salah satu keunggulan utama sistem ini adalah **kecepatan inferensi**. Model hanya membutuhkan **24,3 ms** untuk satu kali proses deteksi, yang berarti mampu memproses sekitar **40 frame per detik (FPS)**.

Kecepatan ini menjadikan sistem sangat ideal untuk:
- Mesin penyortir otomatis
- Robot pemanen
- Sistem monitoring pertanian berbasis kamera

---

## 5. Kesimpulan dan Insight
Berdasarkan hasil evaluasi menggunakan **Confusion Matrix**, model menunjukkan kemampuan klasifikasi yang sangat kuat. Tidak ditemukan kasus tomat matang yang salah diklasifikasikan sebagai tomat mentah. Meskipun terdapat tantangan pada kondisi oklusi (objek terhalang daun atau batang), sistem secara keseluruhan telah menunjukkan performa yang sangat layak untuk menggantikan inspeksi manual.

---

## Penutup
Inovasi ini membuktikan bahwa penerapan **Computer Vision dan Deep Learning** mampu meningkatkan efisiensi serta objektivitas dalam industri pertanian, khususnya di Indonesia. Kami berharap pengembangan sistem ini dapat menjadi langkah awal menuju otomatisasi proses pangan yang lebih cerdas, modern, dan berkelanjutan.

---

