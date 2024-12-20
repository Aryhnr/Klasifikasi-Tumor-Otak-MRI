# README - Klasifikasi Tumor Otak MRI

## Deskripsi Proyek
Proyek ini bertujuan untuk mengembangkan model klasifikasi gambar berbasis **deep learning** untuk mendeteksi tumor otak dari citra MRI. Model ini memanfaatkan teknik **preprocessing** seperti *image resizing* dan **augmentasi data** untuk meningkatkan kualitas data latih. Untuk ekstraksi fitur, digunakan kombinasi **EfficientNet50**, **ResNet50**, dan **Scratched CNN** untuk menangkap pola-pola kompleks pada citra MRI. Hasil klasifikasi ditentukan menggunakan fungsi aktivasi **Softmax** untuk memberikan probabilitas pada setiap kelas tumor.

---

## Arsitektur Proyek
1. **Preprocessing**
   - Mengubah ukuran gambar ke dimensi standar: **256x256 piksel**.
   - Melakukan augmentasi data seperti:
     - Rotasi
     - Perubahan kecerahan (*brightness*)
     - Flip horizontal/vertikal
     - Zoom
   - Normalisasi gambar dengan membagi nilai piksel dengan 255 untuk membawa rentang nilai ke [0, 1].

2. **Ekstraksi Fitur**
   - **EfficientNet50**: Model pretrained untuk menangkap fitur skala besar.
   - **ResNet50**: Model pretrained untuk mempelajari fitur lokal dan detail tekstur.
   - **Scratched CNN**: Lapisan CNN kustom untuk menyesuaikan model dengan dataset MRI tumor otak.

3. **Klasifikasi**
   - Fungsi aktivasi **Softmax** digunakan pada lapisan output untuk menghasilkan probabilitas setiap kelas.
   - Kategori tumor otak yang diklasifikasikan:
     - **Glioma Tumor**
     - **Meningioma Tumor**
     - **Pituitary Tumor**
     - **No Tumor**

---

## Dataset
Dataset yang digunakan terdiri dari citra MRI otak yang diklasifikasikan ke dalam empat kelas (Glioma, Meningioma, Pituitary, dan No Tumor). Dataset ini dilengkapi dengan label yang telah diverifikasi oleh ahli medis.

---

## Alur Kerja Proyek
1. **Persiapan Data**
   - Import dataset MRI.
   - Pembagian data menjadi **training**, **validation**, dan **testing**.
   - Preprocessing citra untuk persiapan model.

2. **Pembangunan Model**
   - Menggabungkan **EfficientNet50**, **ResNet50**, dan **Scratched CNN** sebagai fitur extractor.
   - Menambahkan lapisan fully connected dengan fungsi aktivasi **ReLU** dan Softmax.

3. **Pelatihan Model**
   - Optimizer: **Adam**
   - Loss Function: **Categorical Crossentropy**
   - Metrics: **Accuracy**

4. **Evaluasi**
   - Mengevaluasi performa model pada dataset pengujian.
   - Mengukur metrik seperti akurasi, precision, recall, dan F1-score.

5. **Implementasi**
   - Membangun antarmuka pengguna (UI) menggunakan **Gradio** untuk klasifikasi gambar MRI secara interaktif.
