# Mini Project PCD - Signature Detection on Diplomas

Proyek Pengolahan Citra Digital (PCD) untuk mendeteksi dan memverifikasi keberadaan tanda tangan (*Signature Present* vs *Signature Absent*) pada dokumen ijazah secara otomatis menggunakan OpenCV.
Metodologi & Alur Kerja Program
Auto-Detection Image Files: Mengambil seluruh file gambar berformat .jpg di direktori kerja secara otomatis.
ROI Extraction (Region of Interest):
Pemotongan area spesifik lokasi tanda tangan (misal: area kanan atas untuk Dekan atau kanan bawah untuk Kepala Sekolah).
Pengujian tingkat lanjut menggunakan fitur Multi-ROI Candidate Selection.
Grayscale Conversion: Mengubah citra ROI warna (RGB) menjadi derajat keabuan (grayscale).
Binarization & Thresholding Comparison:
Membandingkan metode Global Thresholding, Adaptive Thresholding, dan Otsu's Thresholding.
Metode Otsu Thresholding dipilih sebagai teknik pemisahan foreground (tinta tanda tangan) dan background (kertas) yang paling optimal.
Morphological Operations:
Opening: Menghilangkan derau (noise / bintik-bintik kecil).
Closing: Menyambungkan garis tinta tanda tangan yang terputus.
Quantification & Decision Rule:
Menghitung jumlah piksel putih (foreground) menggunakan fungsi cv2.countNonZero().
Aturan Keputusan:Jumlah piksel $> 2.000$ (atau $> 2.500$ pada pengujian absent) $\rightarrow$ SIGNATURE PRESENTJumlah piksel 2.000$ $\rightarrow$ SIGNATURE ABSENT
Cara Menjalankan Program (How to Run)
Buka file notebook T6_DIANMAHARANI_PCD.ipynb yang ada di repositori ini.
Klik tombol Open in Colab di bagian atas file.
Unggah seluruh sampel citra ijazah (format .jpg) ke direktori penyimpanan Colab (panel sebelah kiri).
Jalankan setiap sel kode secara berurutan:
Sel 1: Import library dan deteksi otomatis seluruh file .jpg.
Sel 2: Visualisasi citra asli ijazah.
Sel 3: Ekstraksi ROI area tanda tangan & konversi ke grayscale.
Sel 4: Komparasi 3 metode Thresholding (Global, Otsu, Adaptive).
Sel 5: Operasi morfologi (Opening & Closing).
Sel 6: Penghitungan piksel foreground dan cetak tabel log keputusan.
Sel 7: Visualisasi komparatif hasil akhir (ROI vs Citra Biner Tersegmentasi).
Sel Tambahan:
Pengujian khusus sampel citra tanpa tanda tangan (absent1.jpg).
Fungsi Advanced Detection (detect_signature_advanced) dengan fitur penggambaran bounding box (kotak kontur hijau).
Pustaka / Dependensi (Requirements)
opencv-python (cv2)
numpy
matplotlib
os
Output System
Tabel Ringkasan: Menampilkan nomor, nama file ijazah, jumlah piksel foreground, dan status deteksi (SIGNATURE PRESENT / SIGNATURE ABSENT).
Visualisasi Hasil: Menampilkan perbandingan ROI asli dengan kotak kontur hijau di sekeliling goresan tanda tangan beserta citra biner hasil pembersihan morfologi.
