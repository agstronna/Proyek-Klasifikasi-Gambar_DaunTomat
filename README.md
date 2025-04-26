# 🌱 **Klasifikasi Daun Tomat Menggunakan CNN**

Proyek ini bertujuan membangun model deep learning berbasis CNN (Convolutional Neural Network) untuk mengklasifikasikan kondisi daun tomat ke dalam empat kategori berdasarkan citra gambar. Model ini diharapkan dapat membantu deteksi dini penyakit tanaman dan mendukung praktik pertanian cerdas berbasis teknologi.

## 📝 **Deskripsi Proyek**

Model klasifikasi dikembangkan menggunakan TensorFlow dan Keras untuk mengenali empat kategori daun tomat:

- **Late_blight**
- **Septoria_leaf_spot**
- **Tomato_Yellow_Leaf_Curl_Virus**
- **Healthy**

Dataset yang digunakan adalah subset dari PlantVillage, difokuskan hanya pada gambar daun tomat.

## 📚 **Informasi Dataset**
- **Sumber**: [PlantVillage Dataset di Kaggle](https://www.kaggle.com/datasets/abdallahalidev/plantvillage-dataset)
- **Jumlah Total Gambar**: 54.305
- **Jumlah Gambar Daun Tomat**: 18.160

---

# 🛠️ **Arsitektur Model**

Model dikembangkan menggunakan:
- Pretrained **MobileNetV2** (tanpa top layer)
- Layer tambahan:
  - **Conv2D**
  - **MaxPooling2D**
  - **Flatten**
  - **Dense**
  - **Dropout**

Penyusunan model:
- **Loss Function**: `categorical_crossentropy`
- **Optimizer**: `Adam`
- **Callback**: ModelCheckpoint dan EarlyStopping

---

# 🚀 **Fitur Utama**

- Preprocessing gambar (resize dan normalisasi)
- Augmentasi data untuk generalisasi yang lebih baik
- Pembagian dataset menjadi training, validation, dan testing
- Menyertakan visualisasi akurasi dan loss selama training
- Evaluasi hasil model menggunakan confusion matrix dan classification report
- Konversi model ke:
  - **TensorFlow Lite** (.tflite)
  - **TensorFlow.js** untuk deployment web
- Menyediakan antarmuka interaktif untuk inference gambar secara real-time

---

# 📈 **Visualisasi Akurasi dan Loss**

Training dan validation accuracy serta loss divisualisasikan menggunakan Matplotlib untuk memantau performa model selama proses pelatihan.

Contoh plot:
- Grafik Akurasi Training vs Testing

  ![image](https://github.com/user-attachments/assets/b559274d-af1a-45be-9b6f-2a2ce00712ca)

- Grafik Loss Training vs Testing
  
  ![image](https://github.com/user-attachments/assets/42a3317f-e089-458a-ae3c-43a6b7cb3c9d)


---

# 📊 **Hasil Evaluasi Model**

Model dievaluasi pada dataset testing menggunakan:
- Akurasi akhir

| Keterangan                  | Nilai Akurasi |
|------------------------------|---------------|
| Akurasi Akhir Training       | 98.43%        |
| Akurasi Akhir Validasi       | 96.96%        |
| Akurasi Pengujian (Testing)  | 97.91%        |

- Confusion Matrix

  ![image](https://github.com/user-attachments/assets/b7a6d72b-414e-4733-afa5-01b0aa272280)

---

# 🖼️ **Contoh Gambar Inference**

Pengguna dapat mengupload gambar daun tomat dan sistem akan:
- Menampilkan gambar input
- Memberikan prediksi kelas beserta confidence score

  ![image](https://github.com/user-attachments/assets/3068a5e0-2534-47e1-88d3-7f40589c555a)


---

# ⚙️ **Cara Penggunaan di Google Colab**

1. **Upload notebook dan file model** ke Google Drive.
2. **Mount Google Drive** di Colab:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```
3. **Jalankan notebook** langkah demi langkah sesuai instruksi.
4. **Upload gambar** untuk melakukan prediksi menggunakan antarmuka yang disediakan.

---

# 🐍 **Cara Instalasi dan Penggunaan Virtual Environment (myvenv)**

Untuk menjalankan proyek ini di lokal:

1. Buat virtual environment:
   ```bash
   python -m venv myvenv
   ```

2. Aktivasi virtual environment:
   - Windows:
     ```bash
     myvenv\Scripts\activate
     ```
   - Mac/Linux:
     ```bash
     source myvenv/bin/activate
     ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Jalankan script Python atau Jupyter Notebook.

---

# ☁️ **Menjalankan di Google Colab**

Jika tidak ingin instalasi lokal:
- Buka Google Colab
- Upload notebook
- Pastikan mengatur runtime ke **GPU** (`Runtime > Change Runtime Type > GPU`)
- Jalankan sel satu per satu

---

# 📦 **Output Model**

- `saved_model/`
- `model.h5`
- `tflite_model/converted_model.tflite`
- `tfjs_model/`

---

# 🏷️ **Label Kelas**

| Label Kelas                    | Deskripsi                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------|
| **Late_blight**                  | Penyakit daun tomat yang disebabkan oleh *Phytophthora infestans*.                   |
| **Septoria_leaf_spot**           | Penyakit jamur akibat *Septoria lycopersici*.                                         |
| **Tomato_Yellow_Leaf_Curl_Virus** | Infeksi virus yang menyebabkan daun tomat menguning dan melengkung.                  |
| **Healthy**                      | Daun dalam kondisi sehat tanpa tanda-tanda penyakit.                                 |
