# PCD_UTS_202231104_2024_ITPLN
# IMPORT LIBRARY
import cv2
import matplotlib.pyplot as plt
import numpy as np
* Fungsi dari cv2 yaitu untuk memproses gambar dan computer vision sedangkan fungsi dari import matplotlib.pyplot as plt adalah untuk membuat visualisasi dan yang terakhir ada import numpy as np yang berfungsi untuk komputasi numerik dalam program
# Membaca Data Gambar
img = cv2.imread("name.jpg") 
* berfungsi sebagai membaca gambar yang tersimpan dalam file "name.jpg" dan menyimpannya dalam variabel img
rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
* berfungsi untuk mengubah representasi warna gambar dari BGR (Blue-Green-Red) ke RGB (Red-Green-Blue) menggunakan fungsi cv2.cvtColor()
plt.imshow(rgb)
* berfungsi untuk untuk menampilkan gambar yang telah diubah ke ruang warna RGB. Fungsi plt.imshow()
<matplotlib.image.AxesImage at 0x1d382bbde50>

# 2. Convert to Grayscale
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
* berfungsi untuk mengubah gambar ke dalam skala keabuan (grayscale) dengan menggunakan fungsi cv2.cvtColor(). Parameter cv2.COLOR_BGR2GRAY menentukan bahwa konversi akan dilakukan dari ruang warna BGR ke skala keabuan.
# 3. Adjust Contrast and Brightness
alpha = 1.5 # kontras
beta = 30   # kecerahan
adjusted = cv2.convertScaleAbs(img, alpha=alpha, beta=beta)
* Code ini mengatur kontras dan kecerahan dari gambar menggunakan fungsi cv2.convertScaleAbs(). Dalam hal ini, parameter alpha mengatur kontras, sementara parameter beta mengatur kecerahan.
# 4. Display Results
plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.title('Original Image')
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.axis('off')

plt.subplot(1, 2, 2)
plt.title('Brightened Image')
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB))
plt.axis('off')

plt.show()
* Code diatas menggunakan matplotlib untuk menampilkan gambar asli sebelum penyesuaian kontras dan kecerahan. Dengan menggunakan plt.subplot() untuk membuat subplot di dalam figur, di mana gambar asli ditampilkan di subplot pertama.
* plt.figure(figsize=(10, 5)): Membuat figur dengan ukuran 10x5 inci.
* plt.subplot(1, 2, 1): Membuat subplot dengan grid 1 baris dan 2 kolom, dan memilih subplot pertama untuk menampilkan gambar asli.
* plt.title('Original Image'): Memberikan judul "Original Image" pada subplot.
* plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB)): Menampilkan gambar asli dengan menggunakan imshow(). Karena matplotlib menggunakan format warna RGB untuk menampilkan gambar, kita perlu mengonversi gambar BGR ke RGB menggunakan cv2.cvtColor().
* plt.axis('off'): Menghilangkan sumbu (axis) pada gambar.
* Sedangakn plt.subplot(1, 2, 2): Membuat subplot kedua di figur dengan grid 1 baris dan 2 kolom, dan memilih subplot kedua untuk menampilkan gambar yang telah disesuaikan.
* plt.title('Brightened Image'): Memberikan judul "Brightened Image" pada subplot kedua.
* plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)): Menampilkan gambar yang telah disesuaikan dengan menggunakan imshow(). Karena matplotlib menggunakan format warna RGB untuk menampilkan gambar, kita perlu mengonversi gambar BGR ke RGB menggunakan cv2.cvtColor().
# Display the Original Image
plt.subplot(2, 1, 1)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
* berfungsi untuk untuk membuat subplot pertama di dalam figur dengan grid 2 baris dan 1 kolom. Kemudian menggunakan plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)) untuk menampilkan gambar yang telah disesuaikan dalam format warna RGB.
* Dengan plt.title('Original Image'), Anda memberikan judul "Original Image" pada subplot pertama.
# Display the red channel
plt.subplot(2, 2, 2)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0], cmap="gray")
plt.title('Red')
* berfungsi untuk menampilkan saluran merah dari gambar yang telah disesuaikan. Dalam pemrosesan ini, cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0] digunakan untuk mengambil saluran merah dari gambar yang telah disesuaikan. Parameter cmap="gray" digunakan untuk menampilkan gambar dalam skala abu-abu. Judul subplot diatur menjadi "Red", yang menunjukkan bahwa gambar yang ditampilkan adalah saluran merah dari gambar yang telah disesuaikan.
# Display the green channel
plt.subplot(2, 2, 3)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1], cmap="gray")
plt.title('Green')
* berfungsi untuk menampilkan saluran hijau dari gambar yang telah disesuaikan. Dalam pemrosesan ini, cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1] digunakan untuk mengambil saluran hijau dari gambar yang telah disesuaikan. Parameter cmap="gray" digunakan untuk menampilkan gambar dalam skala abu-abu. Judul subplot diatur menjadi "Green", yang menunjukkan bahwa gambar yang ditampilkan adalah saluran hijau dari gambar yang telah disesuaikan.
# Display the blue channel
plt.subplot(2, 2, 4)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2], cmap="gray")
plt.title('Blue')
plt.show()
* berfungsi  untuk menampilkan saluran biru dari gambar yang telah disesuaikan. Dalam pemrosesan ini, cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2] digunakan untuk mengambil saluran biru dari gambar yang telah disesuaikan. Parameter cmap="gray" digunakan untuk menampilkan gambar dalam skala abu-abu. Judul subplot diatur menjadi "Blue", yang menunjukkan bahwa gambar yang ditampilkan adalah saluran biru dari gambar yang telah disesuaikan. Setelah semua subplot ditambahkan, plt.show() digunakan untuk menampilkan keseluruhan figur yang berisi keempat subplot tersebut.
  
merah=cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0] #merah
fig, axs = plt.subplots(1,2, figsize = (15,5))
hist = cv2.calcHist([merah],[0],None,[256],[0,256])
axs[0].imshow(merah, cmap='gray')
axs[1].plot(hist)
plt.show()
* menggunakan cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0] untuk mengambil saluran merah dari gambar yang telah disesuaikan.
* menghitung histogram dari saluran merah menggunakan cv2.calcHist().
* menggunakan plt.subplots() untuk membuat satu baris dengan dua subplot.
* Subplot pertama menampilkan gambar saluran merah menggunakan imshow() dengan cmap='gray'.
* Subplot kedua menampilkan histogram dari saluran merah menggunakan plot().

hijau=cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1] 
fig, axs = plt.subplots(1,2, figsize = (15,5))
hist = cv2.calcHist([hijau],[0],None,[256],[0,256])
axs[0].imshow(hijau, cmap='gray')
axs[1].plot(hist)
plt.show()
* menggunakan cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1] untuk mengambil saluran hijau dari gambar yang telah disesuaikan.
* menghitung histogram dari saluran hijau menggunakan cv2.calcHist().
* menggunakan plt.subplots() untuk membuat satu baris dengan dua subplot.
* Subplot pertama menampilkan gambar saluran hijau menggunakan imshow() dengan cmap='gray'.
* Subplot kedua menampilkan histogram dari saluran hijau menggunakan plot().

biru=cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2] 
fig, axs = plt.subplots(1,2, figsize = (15,5))
hist = cv2.calcHist([biru],[0],None,[256],[0,256])
axs[0].imshow(biru, cmap='gray')
axs[1].plot(hist)
plt.show()
* menggunakan cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2] untuk mengambil saluran biru dari gambar yang telah disesuaikan.
* menghitung histogram dari saluran biru menggunakan cv2.calcHist().
* menggunakan plt.subplots() untuk membuat satu baris dengan dua subplot.
Subplot pertama menampilkan gambar saluran biru menggunakan imshow() dengan cmap='gray'.
Subplot kedua menampilkan histogram dari saluran biru menggunakan plot().

import cv2
import numpy as np
import matplotlib.pyplot as plt
* cv2: Ini adalah pustaka OpenCV, yang merupakan pustaka populer untuk pemrosesan gambar dan komputer vision. OpenCV menyediakan berbagai fungsi untuk membaca, menulis, dan memanipulasi gambar.
* numpy as np: Ini adalah pustaka yang sering digunakan untuk komputasi numerik di Python. Numpy menyediakan array dan fungsi matematika yang kuat, yang sering digunakan dalam pemrosesan gambar untuk manipulasi dan transformasi array gambar.
* matplotlib.pyplot as plt: Ini adalah pustaka untuk membuat visualisasi dalam Python. Dengan menggunakan matplotlib.pyplot, Anda dapat membuat plot, grafik, dan visualisasi lainnya, termasuk menampilkan gambar.

# Baca gambar
img = cv2.imread('name.jpg')
* berfungsi untuk memuat gambar yang disimpan dalam file dengan nama "name.jpg" menggunakan OpenCV. Setelah dieksekusi, gambar tersebut akan disimpan dalam variabel img. 
# Convert citra ke grayscale
gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)
* berfungsi untuk mengonversi gambar img dari ruang warna RGB menjadi skala abu-abu (grayscale). Dalam skala abu-abu, setiap piksel dalam gambar hanya memiliki satu nilai intensitas yang mewakili tingkat keabuan dari 0 (hitam) hingga 255 (putih).
# Inisialisasi subplot
fig, axs = plt.subplots(2, 2, figsize=(10,10))
* berfungsi untuk membuat sebuah figur matplotlib yang terdiri dari empat subplot, dengan masing-masing subplot memiliki ukuran 2 baris dan 2 kolom. Figur ini akan memiliki ukuran keseluruhan 10x10 inci.
# Ambang batas untuk mendapatkan citra biner (none)
(thresh, binary1) = cv2.threshold(gray, 0, 255, cv2.THRESH_BINARY)
axs[0,0].imshow(binary1, cmap = 'gray')
axs[0,0].set_title('NONE')
* menggunakan fungsi cv2.threshold() untuk melakukan proses thresholding pada gambar skala abu-abu (gray). Hasil dari proses thresholding disimpan dalam variabel binary1.
# Convert citra ke HSV
image_hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
* berfungsi untuk mengonversi gambar img dari ruang warna BGR ke ruang warna HSV (Hue, Saturation, Value).
# Definisikan range warna biru dalam HSV
blue_lower = np.array([100, 50, 50])
blue_upper = np.array([140, 255, 255])
* berfungsi untuk menentukan batas bawah dan batas atas untuk deteksi warna biru dalam ruang warna HSV.
# Membuat mask untuk warna biru
mask_blue = cv2.inRange(image_hsv, blue_lower, blue_upper)
axs[0,1].imshow(mask_blue, cmap='gray')
axs[0,1].set_title('BLUE')
* berfungsi untuk membuat sebuah mask yang menunjukkan di mana warna biru berada dalam gambar dalam ruang warna HSV. Mask ini akan berisi piksel dengan nilai 255 di tempat di mana warna biru berada, dan nilai 0 di tempat lainnya.
# Ambang batas untuk mendapatkan citra biner (red-blue)
(thresh, binary3) = cv2.threshold(gray, 43, 255, cv2.THRESH_BINARY)
axs[1,0].imshow(binary3, cmap = 'binary')
axs[1,0].set_title('RED-BLUE')
* menggunakan fungsi cv2.threshold() untuk melakukan proses thresholding pada gambar skala abu-abu (gray). Nilai ambang (threshold) yang di tentukan adalah 43, yang berarti bahwa setiap piksel dengan nilai intensitas yang lebih besar dari 43 akan diubah menjadi 255 (putih), dan yang lainnya akan diubah menjadi 0 (hitam).
# Ambang batas untuk mendapatkan citra biner (red-green-blue)
(thresh, binary4) = cv2.threshold(gray, 80, 255, cv2.THRESH_BINARY)
axs[1,1].imshow(binary4, cmap = 'binary')
axs[1,1].set_title('RED-GREEN-BLUE')

plt.show()
* menggunakan fungsi cv2.threshold() untuk melakukan proses thresholding pada gambar skala abu-abu (gray). Nilai ambang (threshold) yang Anda tentukan adalah 80, yang berarti bahwa setiap piksel dengan nilai intensitas yang lebih besar dari 80 akan diubah menjadi 255 (putih), dan yang lainnya akan diubah menjadi 0 (hitam).
* menggunakan plt.show() untuk menampilkan keseluruhan figur
