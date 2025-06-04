# Sistem Pengenalan Visual untuk Mendeteksi Keberadaan Helm dan Rompi Keselamatan

## Deskripsi
Sistem ini merupakan implementasi pengenalan visual (computer vision) yang dirancang untuk mendeteksi keberadaan helm dan rompi keselamatan pada pekerja. Sistem ini menggunakan teknik deep learning untuk melakukan deteksi objek secara real-time.

## Metode yang Digunakan
Sistem ini menggunakan YOLOv8 (You Only Look Once versi 8) sebagai model deteksi objek utama.

### Alasan Pemilihan YOLOv8:
- Real-time inference dengan kecepatan tinggi
- Akurasi tinggi untuk deteksi objek kecil seperti helm dan rompi
- Arsitektur modern dan ringan, cocok untuk implementasi edge (CCTV)
- Format dataset sudah tersedia (dataset snehilsanyal/construction-site-safety-image-dataset-roboflow menggunakan YOLO format)

## Strategi Pengumpulan dan Anotasi Data

Data latih untuk sistem ini menggunakan dataset publik dari Kaggle berjudul "Construction Site Safety Image Dataset Roboflow" (oleh snehilsanyal). Dataset ini dipilih karena relevan dengan domain proyek dan sudah tersedia dalam format yang cocok untuk YOLO.

**Detail Dataset:**
- Jumlah Kelas: 10
- Nama Kelas: ["Hardhat","Mask","NO-Hardhat","NO-Mask","NO-Safety Vest","Person","Safety Cone","Safety Vest","machinery","vehicle"]
- Format Anotasi: YOLO format (.txt)
- Metadata: Dilengkapi dengan `metadata.csv` dan `count.csv` yang menyediakan informasi dataset dan rincian jumlah data pada setiap split.

**Pembagian Dataset:**
Dataset ini sudah dibagi menjadi set pelatihan, validasi, dan pengujian dengan rincian sebagai berikut:
- **Pelatihan (Train):** 2605 gambar dan 2605 file label
- **Validasi (Valid):** 114 gambar dan 114 file label
- **Pengujian (Test):** 82 gambar dan 82 file label

**Ringkasan Dataset (dalam Bahasa Indonesia dari sumber):**
Dataset ini ramah untuk pemula, cocok untuk tugas klasifikasi multi-kelas, deteksi objek, dan pelacakan. Anotasi tersedia dalam format YoloV8. Pembagian data (train-val-test) sudah diberikan langsung di dalam folder dataset, sehingga dapat langsung digunakan untuk menjalankan model.

## Hasil Evaluasi Model
Hasil evaluasi model pada set pengujian (test set) menunjukkan performa sebagai berikut:

| Class          | Images | Instances | Box(P) | R     | mAP50 | mAP50-95 |
|----------------|--------|-----------|--------|-------|-------|----------|
| all            | 114    | 697       | 0.66   | 0.442 | 0.48  | 0.231    |
| Hardhat        | 42     | 79        | 0.759  | 0.544 | 0.586 | 0.332    |
| Mask           | 19     | 21        | 0.777  | 0.81  | 0.786 | 0.391    |
| NO-Hardhat     | 37     | 69        | 0.791  | 0.329 | 0.416 | 0.159    |
| NO-Mask        | 44     | 74        | 0.508  | 0.223 | 0.255 | 0.0929   |
| NO-Safety Vest | 56     | 106       | 0.602  | 0.302 | 0.361 | 0.17     |
| Person         | 84     | 166       | 0.658  | 0.429 | 0.493 | 0.217    |
| Safety Cone    | 13     | 44        | 0.723  | 0.591 | 0.618 | 0.308    |
| Safety Vest    | 28     | 41        | 0.757  | 0.561 | 0.599 | 0.324    |
| machinery      | 26     | 55        | 0.445  | 0.491 | 0.499 | 0.228    |
| vehicle        | 16     | 42        | 0.578  | 0.143 | 0.185 | 0.0933   |

## Saran Pengembangan Lanjutan atau Perbaikan Sistem
Untuk pengembangan sistem di masa mendatang atau perbaikan lebih lanjut, beberapa area yang dapat dieksplorasi meliputi:

-   Meningkatkan akurasi deteksi, terutama untuk objek yang sulit dikenali atau dalam kondisi lingkungan yang bervariasi.
-   Mengoptimalkan performa real-time untuk implementasi pada perangkat dengan sumber daya terbatas (edge devices).
-   Menambah kemampuan pelacakan objek (object tracking) untuk memantau individu dari waktu ke waktu.
-   Mengintegrasikan sistem dengan platform pemantauan atau sistem peringatan otomatis.
-   Memperluas jenis alat pelindung diri (APD) lain yang dideteksi, seperti sepatu keselamatan atau sarung tangan.
-   Melakukan pengujian dan validasi ekstensif dalam skenario dunia nyata yang beragam.
