**Deskripsi**

Proyek ini berisi notebook untuk melatih model klasifikasi gambar sederhana (CNN) pada dataset Rock-Paper-Scissors. Model dibuat dan dilatih pada file [main.ipynb](main.ipynb) menggunakan dataset gambar yang tersimpan dalam folder [rockpaperscissors](rockpaperscissors).

**Ringkasan kode**

- **Persiapan data**: `ImageDataGenerator` dari Keras digunakan dengan `rescale=1./255` dan `validation_split=0.2`, lalu `flow_from_directory(dataset_path, target_size=(150,150), batch_size=32, class_mode='categorical', subset=...)` untuk membagi data training/validasi.
- **Arsitektur model**: Model `Sequential` berisi beberapa lapisan `Conv2D` + `MaxPooling2D`, diakhiri dengan `Flatten()` dan dua `Dense` (output 3 unit dengan `softmax`).
- **Kompilasi & pelatihan**: Kompilasi menggunakan `loss='categorical_crossentropy'`, optimizer `adam`, metric `accuracy`. Pelatihan dilakukan dengan `model.fit(..., epochs=10)`.
- **Evaluasi & prediksi**: `model.evaluate(validation_generator)` dan `model.predict(validation_generator)` untuk memperoleh metrik dan probabilitas prediksi.

**Struktur proyek**

- [main.ipynb](main.ipynb) — notebook utama berisi semua sel kode (persiapan data, definisi model, pelatihan, evaluasi, prediksi).
- [rockpaperscissors](rockpaperscissors) — folder dataset yang berisi tiga subfolder: `rock`, `paper`, `scissors` (gambar tiap kelas).

**Dependensi**

Minimal:

```
Python 3.8+
tensorflow
numpy
pandas
jupyter (atau jupyterlab / notebook)
```

Instalasi pip:

```
python -m pip install --upgrade pip
python -m pip install tensorflow numpy pandas matplotlib jupyter
```

**Cara menjalankan**

```
jupyter notebook main.ipynb
```
