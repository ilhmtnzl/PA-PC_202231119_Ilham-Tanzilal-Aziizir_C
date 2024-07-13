
# Project UAS Pengolahan Citra

**1. Import Library**

Source code:

import cv2
import matplotlib.pyplot as plt

Penjelasan:
Program ini menggunakan dua library utama:

- cv2: Library OpenCV yang digunakan untuk pemrosesan gambar.
- matplotlib.pyplot: Library Matplotlib yang digunakan untuk menampilkan gambar.

**2. Memuat Gambar**

Source code:

image_path = 'Foto Diri.jpg'

image = cv2.imread(image_path)

Penjelasan:
Bagian ini memuat gambar dari file dengan nama Foto Diri.jpg menggunakan fungsi cv2.imread(). Gambar ini kemudian disimpan dalam variabel image.

**3. Konversi Gambar ke Grayscale**

Source code:

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

Penjelasan:
Gambar yang dimuat dikonversi menjadi grayscale (hitam-putih) menggunakan fungsi cv2.cvtColor(). Hasilnya disimpan dalam variabel gray.

**4. Deteksi Tepi Menggunakan Canny Edge Detection**

Source code:

edges = cv2.Canny(gray, 100, 200)

Penjelasan:
Metode Canny digunakan untuk mendeteksi tepi dalam gambar grayscale. Parameter 100 dan 200 adalah nilai threshold minimum dan maksimum untuk histeresis. Hasil deteksi tepi disimpan dalam variabel edges.

**5. Mencari Kontur**

Source code:

contours, _ = cv2.findContours(edges, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)

Penjelasan:
Fungsi cv2.findContours() digunakan untuk mencari kontur dalam gambar hasil deteksi tepi. cv2.RETR_TREE digunakan untuk mengambil semua kontur dan membangun hierarki lengkap. cv2.CHAIN_APPROX_SIMPLE menyederhanakan kontur dengan menghapus poin redundan. Kontur yang ditemukan disimpan dalam variabel contours.

**6. Menggambar Kontur pada Gambar Asli**

Source code:

contour_image = image.copy()
cv2.drawContours(contour_image, contours, -1, (0, 255, 0), 3)

Penjelasan:
Salinan dari gambar asli dibuat dan disimpan dalam variabel contour_image. Kontur yang ditemukan kemudian digambar pada salinan gambar asli menggunakan fungsi cv2.drawContours(). Warna kontur adalah hijau (0, 255, 0) dengan ketebalan garis 3.

**7. Menampilkan Hasil (Output 1)**

Source code:

plt.figure(figsize=(15, 5))

plt.subplot(1, 3, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')

Penjelasan:
Bagian ini menampilkan gambar asli dan hasil deteksi tepi menggunakan Matplotlib:

- Gambar asli ditampilkan pada subplot pertama setelah dikonversi dari format BGR ke RGB.

- Hasil deteksi tepi ditampilkan pada subplot kedua dalam skala abu-abu.

**8. Menampilkan Hasil (Output 2)**

Source code:

plt.figure(figsize=(15, 5))

plt.subplot(1, 3, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(cv2.cvtColor(contour_image, cv2.COLOR_BGR2RGB))
plt.title('Contours Detection')
plt.axis('off')

plt.tight_layout()
plt.show()

Penjelasan:
Bagian ini menampilkan tiga gambar:

- Gambar asli pada subplot pertama.
- Hasil deteksi tepi pada subplot kedua.
- Gambar dengan kontur yang digambar pada subplot ketiga.
plt.tight_layout() digunakan untuk menyesuaikan tata letak subplot agar lebih rapi, dan plt.show() digunakan untuk menampilkan semua subplot.



