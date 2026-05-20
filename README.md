**Deskripsi**

Proyek ini berisi notebook untuk melatih model klasifikasi gambar sederhana (CNN) pada dataset Rock-Paper-Scissors. Model dibuat dan dilatih pada file [main.ipynb](main.ipynb) menggunakan dataset gambar yang tersimpan dalam folder [rockpaperscissors](rockpaperscissors).

**Ringkasan kode**

- **Persiapan data**: `ImageDataGenerator` dari Keras digunakan dengan `rescale=1./255` dan `validation_split=0.2`, lalu `flow_from_directory(dataset_path, target_size=(150,150), batch_size=32, class_mode='categorical', subset=...)` untuk membagi data training/validasi.
- **Arsitektur model**: Model `Sequential` berisi beberapa lapisan `Conv2D` + `MaxPooling2D`, diakhiri dengan `Flatten()` dan dua `Dense` (output 3 unit dengan `softmax`).
- **Kompilasi & pelatihan**: Kompilasi menggunakan `loss='categorical_crossentropy'`, optimizer `adam`, metric `accuracy`. Pelatihan dilakukan dengan `model.fit(..., epochs=10)`.
- **Evaluasi & prediksi**: `model.evaluate(validation_generator)` dan `model.predict(validation_generator)` untuk memperoleh metrik dan probabilitas prediksi.

**Struktur proyek**

- [main.ipynb](main.ipynb) — notebook utama berisi semua sel kode (persiapan data, definisi model, pelatihan, evaluasi, prediksi).
- [rockpaperscissors](rockpaperscissors) — folder dataset yang berisi tiga subfolder: `rock`, `paper`, `scissors` (gambar untuk tiap kelas).

**Dependensi**

Minimal:

```
Python 3.8+
tensorflow
numpy
pandas
matplotlib (opsional, untuk visualisasi)
jupyter (atau jupyterlab / notebook)
```

Contoh instalasi pip:

```
python -m pip install --upgrade pip
python -m pip install tensorflow numpy pandas matplotlib jupyter
```

Jika Anda menggunakan lingkungan virtual (direkomendasikan):

```
python -m venv .venv
# PowerShell
.venv\Scripts\Activate.ps1
# CMD
.venv\Scripts\activate
pip install tensorflow numpy pandas matplotlib jupyter
```

**Cara menjalankan**

1. Jalankan di Jupyter Notebook (direkomendasikan):

```
jupyter notebook main.ipynb
```

   - Buka `main.ipynb` lalu jalankan sel-selnya berurutan. Pastikan `dataset_path = "rockpaperscissors"` sesuai lokasi dataset.

2. Menjalankan sebagai skrip (alternatif):

```
jupyter nbconvert --to script main.ipynb
python main.py
```

   - Perhatikan: skrip yang dihasilkan mungkin memerlukan penyesuaian (mis. penanganan direktori kerja, pemanggilan `if __name__ == "__main__":`, atau pengaturan logging).

**Catatan / Tips**

- Jika Anda memiliki GPU dan ingin memanfaatkan TensorFlow GPU, instal paket `tensorflow` versi yang kompatibel dengan driver/CUDA di sistem Anda.
- Jika training memakan waktu lama, kurangi `epochs` atau gunakan `batch_size` yang lebih kecil/lebih besar sesuai memori.
- Untuk melihat grafik loss/accuracy, tambahkan visualisasi dari `history` (mis. `matplotlib` plot dari `history.history['loss']` dan `history.history['val_loss']`).

Jika Anda ingin, saya bisa membuat `requirements.txt` otomatis dari dependensi di README atau menambahkan script `run.py` yang menjalankan training secara non-interaktif. Beri tahu saya pilihan Anda.
