# Dataset Klasifikasi: Biner, Multikelas, dan Multilabel

Repositori ini berisi 9 dataset Kaggle yang dikelompokkan menjadi 3 jenis klasifikasi (masing-masing 3 dataset), lengkap dengan identifikasi, penjelasan, dan sumber aslinya.

## Definisi Singkat

| Jenis | Arti | Contoh keputusan |
|---|---|---|
| **Biner** | Dua pilihan kelas, hanya satu yang benar | Asli / Palsu |
| **Multikelas** | Banyak pilihan kelas, tetapi hanya **satu** yang dipilih per data | Gambar ini rambu apa? (1 dari 43) |
| **Multilabel** | Satu data bisa punya **beberapa** label sekaligus | Game ini bergenre Action **dan** Indie |

## Ringkasan 9 Dataset

| No | Dataset | Jenis | Target / Label | Tipe Data | Sumber | URL |
|---|---|---|---|---|---|---|
| 1 | Banknote Authentication (UCI) | Biner | `class`: 0 = asli, 1 = palsu | Tabular | UCI ML Repository (Volker Lohweg) | https://www.kaggle.com/datasets/ritesaluja/bank-note-authentication-uci-data |
| 2 | Airline Passenger Satisfaction | Biner | `satisfaction`: satisfied / neutral or dissatisfied | Tabular | Kaggle (teejmahal20) | https://www.kaggle.com/datasets/teejmahal20/airline-passenger-satisfaction |
| 3 | Software Defects (Playground S3E23) | Biner | `defects`: cacat / tidak cacat | Tabular | Kaggle Playground Series S3E23 | https://www.kaggle.com/competitions/playground-series-s3e23 |
| 4 | Intel Image Classification | Multikelas | 6 kelas pemandangan | Gambar | Intel (via Analytics Vidhya) | https://www.kaggle.com/datasets/puneet6060/intel-image-classification |
| 5 | GTSRB German Traffic Sign | Multikelas | 43 kelas rambu lalu lintas | Gambar | INI Benchmark (IJCNN 2011) | https://www.kaggle.com/datasets/meowmeowmeowmeowmeow/gtsrb-german-traffic-sign |
| 6 | Garbage Classification | Multikelas | 6 kelas sampah | Gambar | Kaggle (asdasdasasdas) | https://www.kaggle.com/datasets/asdasdasasdas/garbage-classification |
| 7 | CelebFaces Attributes (CelebA) | Multilabel | 40 atribut biner per wajah | Gambar | CUHK MMLAB | https://www.kaggle.com/datasets/jessicali9530/celeba-dataset |
| 8 | Steam Store Games (Clean) | Multilabel | `genres` (banyak genre per game) | Tabular | Steam API + SteamSpy (Nik Davis) | https://www.kaggle.com/datasets/nikdavis/steam-store-games |
| 9 | Board Games (BoardGameGeek) | Multilabel | `Mechanics`, `Domains` | Tabular | BoardGameGeek (Feb 2021) | https://www.kaggle.com/datasets/andrewmvd/board-games |

---

## A. Klasifikasi Biner

### 1. Banknote Authentication (UCI)
- **Tujuan:** menentukan apakah uang kertas asli atau palsu.
- **Data:** 1.372 baris, 4 fitur numerik hasil wavelet transform citra uang (variance, skewness, curtosis, entropy) dan 1 kolom kelas.
- **Label:** `class` = 0 (asli, 762 data) atau 1 (palsu, 610 data).
- **Kenapa biner:** hanya ada dua kemungkinan jawaban.
- **Sumber asli:** UCI ML Repository, https://archive.ics.uci.edu/dataset/267/banknote+authentication

### 2. Airline Passenger Satisfaction
- **Tujuan:** memprediksi apakah penumpang puas dengan layanan maskapai.
- **Data:** lebih dari 100 ribu catatan survei (`train.csv` dan `test.csv`) berisi profil penumpang, tipe perjalanan, kelas kabin, jarak, dan penilaian berbagai layanan.
- **Label:** `satisfaction` = *satisfied* atau *neutral or dissatisfied*.
- **Kenapa biner:** dua kelas hasil.

### 3. Binary Classification with a Software Defects Dataset
- **Tujuan:** memprediksi apakah sebuah modul perangkat lunak mengandung cacat (bug).
- **Data:** metrik kode program (jumlah baris kode, kompleksitas siklomatik, dan metrik struktur lainnya) dalam `train.csv` dan `test.csv`.
- **Label:** `defects` = cacat (1) atau tidak cacat (0). Kelas tidak seimbang karena modul cacat lebih jarang.
- **Catatan:** dataset kompetisi, perlu login Kaggle dan klik *Join Competition* sebelum diunduh.

---

## B. Klasifikasi Multikelas

### 4. Intel Image Classification
- **Tujuan:** mengenali jenis pemandangan dari gambar.
- **Data:** sekitar 25 ribu gambar berwarna 150×150 piksel (folder train, test, dan pred).
- **Kelas (6):** buildings, forest, glacier, mountain, sea, street.
- **Kenapa multikelas:** satu gambar hanya masuk ke satu dari 6 kelas.

### 5. GTSRB (German Traffic Sign Recognition Benchmark)
- **Tujuan:** mengenali jenis rambu lalu lintas.
- **Data:** 39.209 gambar latih dan 12.630 gambar uji, dengan `Train.csv`, `Test.csv`, dan `Meta.csv`.
- **Kelas:** 43 jenis rambu (`ClassId` 0–42).
- **Kenapa multikelas:** setiap gambar rambu hanya punya satu kelas.

### 6. Garbage Classification
- **Tujuan:** memilah jenis sampah dari gambar.
- **Data:** 2.527 gambar.
- **Kelas (6):** cardboard, glass, metal, paper, plastic, trash.
- **Kenapa multikelas:** satu gambar = satu jenis sampah.

---

## C. Klasifikasi Multilabel

### 7. CelebFaces Attributes (CelebA)
- **Tujuan:** mengenali atribut pada wajah.
- **Data:** 202.599 gambar wajah dari 10.177 identitas, plus 5 titik landmark per gambar.
- **Label:** 40 atribut biner per gambar (misalnya Eyeglasses, Blond_Hair, Smiling). Satu wajah bisa punya banyak atribut sekaligus.
- **Sumber asli:** http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html (hanya untuk riset non-komersial).

### 8. Steam Store Games (Clean Dataset)
- **Tujuan:** memprediksi genre sebuah game.
- **Data:** 27.075 game, 18 kolom, ukuran file sekitar 1,67 MB.
- **Label:** `genres`. Satu game bisa punya beberapa genre, dipisah titik koma (contoh: `Action;Indie`).
- **Saran fitur:** `categories`, `platforms`, harga, jumlah rating. Jangan pakai `steamspy_tags` sebagai fitur karena isinya sangat dekat dengan genre (data leakage).
- **Sumber asli:** Steam Store API dan SteamSpy API.

### 9. Board Games (BoardGameGeek)
- **Tujuan:** memprediksi mekanik dan domain sebuah board game.
- **Data:** sekitar 20 ribu game berperingkat dari BoardGameGeek, dikumpulkan Februari 2021. Kolom: ID, Name, Year Published, Min/Max Players, Play Time, Min Age, Users Rated, Rating Average, BGG Rank, Complexity Average, Owned Users, Mechanics, Domains.
- **Label:** `Mechanics` dan `Domains`. Keduanya berisi beberapa nilai per game, dipisah koma.
- **Catatan kualitas:** banyak nilai kosong di `Domains` dan `Mechanics`, jadi perlu dibersihkan dulu.
- **Lisensi dan sitasi:** CC BY 4.0. Dilini Samarasinghe (2021), "BoardGameGeek Dataset on Board Games", IEEE Dataport, doi:10.21227/9g61-bs59.

---

## Cara Mengunduh dengan Kaggle API

```bash
pip install kaggle
# letakkan kaggle.json di ~/.kaggle/ (Kaggle > Settings > Create New Token)

kaggle datasets download -d ritesaluja/bank-note-authentication-uci-data
kaggle datasets download -d teejmahal20/airline-passenger-satisfaction
kaggle competitions download -c playground-series-s3e23
kaggle datasets download -d puneet6060/intel-image-classification
kaggle datasets download -d meowmeowmeowmeowmeow/gtsrb-german-traffic-sign
kaggle datasets download -d asdasdasasdas/garbage-classification
kaggle datasets download -d jessicali9530/celeba-dataset
kaggle datasets download -d nikdavis/steam-store-games
kaggle datasets download -d andrewmvd/board-games
```

> File dataset tidak perlu di-push ke GitHub (ukurannya besar). Cukup simpan README ini beserta tautan sumbernya.
