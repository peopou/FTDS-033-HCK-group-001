# Judul Project
```
"TRASHSIFY" SEBAGAI MEDIA PEMBELAJARAN SISWA UNTUK MENGENALI JENIS-JENIS SAMPAH
```
## Repository Outline
```
Deployment                = Berisi beberapa folder yang berisi file yang digunakan untuk deployment (hugging face)
Group-001_ETL.ipynb       = Berupa file yang berisi syntax proses ETL
Group-001_EDA.ipynb       = Berupa file yang berisi syntax untuk visualisasi
Group-001_Training.ipynb  = Berupa file yang berisi syntax untuk training dan modeling dataset
Group-001_Inference.ipynb = Berupa file yang berisi syntax untuk melakakukan uji prediksi model 
```

## Problem Background
```
Permasalahan sampah menjadi tantangan global yang semakin kritis, terutama di wilayah perkotaan dengan volume limbah yang tinggi. Salah satu hambatan utama dalam pengelolaan sampah yang efektif adalah rendahnya tingkat pemilahan berdasarkan jenisnya—yaitu organik, anorganik, dan B3. Pemilahan yang tidak tepat dapat menghambat proses daur ulang, meningkatkan biaya pengolahan, dan memperparah dampak lingkungan.

Banyak masyarakat masih belum memiliki kesadaran untuk membuang sampah ketempat yang sesuai dengan jenis nya seperti sampaha anorganik, organik, dan limbah B3.

Projek ini dibuat sebagagai fasilitas guna membanatu siswa mempelajari klasifikasi sampah dengan teknologi terkini. Diharapkan projek ini mampu memprediksi jenis sampah ketika diberikan sampel gambar nya.
```

## Project Output
``` 
Berupa mobile-app atau website yang mampu memprediksi jenis sampah dengan memasukkan foto sampah yang ingin dipredik jenis nya ke dalam apps lalu apps akan menebak jenis sampah tersebut.
```

## Data
```
https://www.kaggle.com/datasets/deayulianisabrina/klasifikasi-sampah

Dataset berisi kumpulan gambar sampah yang telah dilabeli ke dalam tiga kategori utama:

- Organik: sampah yang dapat terurai secara alami (misalnya sisa makanan, daun, kulit buah)
- Anorganik: sampah yang tidak mudah terurai (misalnya plastik, kertas, logam, kaca)
- B3 (Bahan Berbahaya dan Beracun): limbah yang berpotensi membahayakan kesehatan atau lingkungan (misalnya baterai, lampu TL, kaleng cat, limbah elektronik)
```

## Method
```
Secara garis besar projek ini dibagi dalam 4 tahap
1. ETL (Extract, Transform, Load)
    - Dataset mentah di-exstrak dari folder yang sebelumnya didownload dari kaggle
    - Data yang telah di-ekstrak selanjutnya dlakukan transformasi dengan augmentasi karna dataset berupa gambar
    - Dataset yang telah clean disimpan kedalam folder baru untuk proses modeling dan untuk path gambar disimpan ke database (postgreSQL)

2. Analisis
    - Menampilkan contoh data (gambar) dari setiap class
    - Menampilkan distrubis gambar keseluruhan dan tiap kelas
    - Melihat atribut (size, format, color channel) data apakah sudah sama atau belum, karena pada proses ETL data telah di transformasi

3. Modeling
    - Modeling
        - karna pada proses ETL data telah dibagi menjadi data train, test dan validation kemudian di simpan ke path local, maka data di load
        - Data di-training dengan model transfer learning EfficienteNetBO
    - Training
        - Model di training dengan 15 epochs dengan early stop 6 patience
        - Model trained dilakukan evaluasi lalu disimpan
    
    - Inference
        - Model yang telah disimpan sebelumnya di-load
        - Atur konfiguras gambar yang akan dipredict sesuai data yang di training

4. Deployment 
    Data yang telah siap selanjutnya dilakukan deployment dengan detail file/folder
    - src             = folder yang berisi page yang akan ditampilkan (eda dan predict)
    - model           = Model yang telah ditraining dan akan digunakan saat inference
    - image           = Berisi 2 folder gambar (dataset mentah dan dataset clean)
    - Dockerfile      = Berisi konfigurasi docker
    - requirments.txt = Berisi libraries yang digunakan
```

## Stacks
```
Bahasa Pemrogaman = Python
Libraries         = numpy, pandas, seaborn, matplotlib, os, PIL, tensorflow, sklearn, psycopg2
Deployment        = Huggingface
```

## Reference
```
HuggingFace link = https://huggingface.co/spaces/tomatijo/FP
slides link      = https://www.canva.com/design/DAG6caEAlyQ/yrJzsoZjCLpOhwv5Rq-VjA/edit?ui=eyJEIjp7IlAiOnsiQiI6ZmFsc2V9fX0
```


