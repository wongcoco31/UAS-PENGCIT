# UAS-PENGCIT
Proyek yang dibuat adalah contoh implementasi pemrosesan citra untuk menghasilkan citra tersegmentasi dengan menggunakan teknik thresholding dan contouring. 
1. Berikut adalah teori yang mendukung langkah-langkah dalam proyek ini:

Membaca Gambar: Gunakan fungsi cv2.imread() untuk membaca gambar dari file yang ditentukan dan menyimpannya dalam variabel img. Citra tersebut akan dibaca dalam mode BGR (Blue-Green-Red).

Konversi ke Grayscale: Mengubah citra BGR menjadi citra grayscale menggunakan fungsi cv2.cvtColor() dengan parameter cv2.COLOR_BGR2GRAY. Hasilnya disimpan dalam variabel gray. Citra grayscale hanya memiliki satu saluran warna (intensitas), yang mempermudah dalam melakukan operasi pemrosesan lanjutan.

Gaussian Blur: Pada tahap ini, diterapkan Gaussian blur pada citra grayscale untuk mengurangi noise dan menghaluskan gambar. Fungsi cv2.GaussianBlur() digunakan dengan kernel size (ukuran kernel) (5, 5) dan disimpan dalam variabel blur. Filter Gaussian membantu menghaluskan citra dengan mengurangi perbedaan intensitas antara piksel-piksel tetangganya.

Thresholding: Menggunakan fungsi cv2.threshold() untuk mengubah citra menjadi citra biner (hitam-putih) berdasarkan nilai ambang yang ditentukan. Nilai ambang 127 digunakan dalam contoh ini. Semua piksel dengan intensitas di bawah ambang akan diubah menjadi hitam (0), sedangkan piksel-piksel dengan intensitas di atas ambang akan diubah menjadi putih (255). Hasilnya disimpan dalam variabel thresh.

Deteksi Contour: Menggunakan fungsi cv2.findContours() untuk menemukan kontur dalam citra biner yang dihasilkan dari tahap sebelumnya. Fungsi ini mengembalikan daftar kontur dan hirarki kontur. Daftar kontur berisi titik-titik yang membentuk kontur dalam citra, sedangkan hirarki kontur memberikan informasi tentang hubungan spasial antara kontur-kontur tersebut.

Kontur Terbesar: Menggunakan fungsi max() dengan parameter cv2.contourArea untuk mencari kontur terbesar dalam citra. Fungsi cv2.contourArea() menghitung luas kontur. Kontur terbesar dipilih berdasarkan luasnya dan disimpan dalam variabel cnt.

Membuat Mask: Membuat maska (selubung) berdasarkan kontur terbesar yang telah ditemukan sebelumnya. Membuat array kosong dengan ukuran yang sama dengan citra asli menggunakan np.zeros_like(). Menggunakan fungsi cv2.drawContours() untuk menggambar kontur terbesar pada maska dengan warna putih (255) dan ketebalan yang ditentukan. Hasilnya disimpan dalam variabel mask.

Konversi ke Grayscale: Mengubah maska ke citra grayscale menggunakan fungsi cv2.cvtColor() dengan parameter cv2.COLOR_BGR2GRAY. Hasilnya disimpan dalam variabel mask_gray. Maska grayscale hanya memiliki satu saluran warna (intensitas) yang digunakan untuk menggabungkan maska dengan citra asli pada tahap selanjutnya.

Menggabungkan Maska dengan Citra Asli: Menggunakan operasi bitwise AND (cv2.bitwise_and()) untuk menerapkan maska ke citra asli. Hasilnya adalah citra asli yang hanya mempertahankan piksel yang terdapat dalam maska. Hasil ini disimpan dalam variabel masked.

Menampilkan Citra: Menggunakan matplotlib.pyplot untuk menampilkan citra asli dan citra tersegmentasi (citra dengan maska yang diterapkan). plt.subplot() digunakan untuk membuat subplot untuk menampilkan kedua citra secara berdampingan. plt.imshow() digunakan untuk menampilkan citra dalam subplot, dan plt.title() digunakan untuk memberikan judul pada setiap subplot.

Dengan mengikuti langkah-langkah ini, Anda dapat memuat gambar, mengubahnya menjadi citra grayscale, menerapkan Gaussian blur, melakukan thresholding, mencari kontur, memilih kontur terbesar, membuat maska, menerapkan maska ke citra asli, dan menampilkan citra asli dan tersegmentasi secara berdampingan.

2. Berikut adalah tahapan-tahapan rinci untuk menyelesaikan proyek deteksi kontur dan segmentasi citra dengan OpenCV:

Impor Libraries: Impor library yang diperlukan, yaitu cv2, numpy, dan matplotlib.pyplot.

Memuat Gambar: Gunakan fungsi cv2.imread() untuk membaca gambar dari file yang ditentukan dan simpan hasilnya dalam variabel img.

Konversi ke Grayscale: Gunakan fungsi cv2.cvtColor() dengan parameter cv2.COLOR_BGR2GRAY untuk mengubah citra BGR menjadi citra grayscale. Simpan hasilnya dalam variabel gray.

Gaussian Blur: Terapkan Gaussian blur pada citra grayscale untuk mengurangi noise dan menghaluskan gambar. Gunakan fungsi cv2.GaussianBlur() dengan kernel size (ukuran kernel) (5, 5) dan simpan hasilnya dalam variabel blur.

Thresholding: Terapkan thresholding pada citra yang telah di-blur untuk menghasilkan citra biner (hitam-putih). Gunakan fungsi cv2.threshold() dengan parameter-parameter yang sesuai (dalam contoh ini threshold value 127, maksimal value 255, dan metode thresholding cv2.THRESH_BINARY). Simpan hasilnya dalam variabel thresh.

Deteksi Kontur: Gunakan fungsi cv2.findContours() untuk menemukan kontur dalam citra biner yang dihasilkan dari tahap sebelumnya. Fungsi ini mengembalikan dua nilai, yaitu daftar kontur dan hirarki kontur. Simpan daftar kontur dalam variabel contours dan hirarki kontur dalam variabel hierarchy.

Kontur Terbesar: Temukan kontur terbesar dalam citra. Gunakan fungsi max() dengan parameter cv2.contourArea untuk mencari kontur dengan luas terbesar dalam daftar kontur. Simpan kontur terbesar dalam variabel cnt.

Membuat Mask: Buat maska (selubung) berdasarkan kontur terbesar yang telah ditemukan. Gunakan np.zeros_like() untuk membuat array kosong dengan ukuran yang sama dengan citra asli. Gunakan fungsi cv2.drawContours() untuk menggambar kontur terbesar pada maska dengan warna putih (255) dan ketebalan kontur yang ditentukan. Simpan hasilnya dalam variabel mask.

Konversi ke Grayscale: Konversi maska ke citra grayscale menggunakan fungsi cv2.cvtColor() dengan parameter cv2.COLOR_BGR2GRAY. Simpan hasilnya dalam variabel mask_gray.

Menerapkan Maska ke Citra Asli: Terapkan maska ke citra asli menggunakan operasi bitwise AND (cv2.bitwise_and()). Simpan hasilnya dalam variabel masked.

Menampilkan Citra: Gunakan plt.subplot() untuk membuat subplot dan plt.imshow() untuk menampilkan citra dalam subplot. Tampilkan citra asli dan citra tersegmentasi (citra dengan maska yang diterapkan) secara berdampingan. Berikan judul pada setiap subplot menggunakan plt.title(). Terakhir, panggil plt.tight_layout() dan plt.show() untuk menampilkan gambar.

Menyimpan Hasil: Gunakan cv2.imwrite() untuk menyimpan citra hasil segmentasi dengan nama "hasil_removal_bg.png". Fungsi ini akan menyimpan citra masked yang telah diproses dengan menghapus latar belakang ke dalam file dengan format PNG.

Dengan mengikuti langkah-langkah di atas, Anda akan dapat memuat gambar, mengubahnya menjadi citra grayscale, menerapkan Gaussian blur, melakukan thresholding, mencari kontur, memilih kontur terbesar, membuat maska, menerapkan maska ke citra asli, menampilkan citra, dan menyimpan hasil segmentasi dalam sebuah file.
