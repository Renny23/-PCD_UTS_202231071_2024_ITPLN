# -PCD_UTS_202231071_2024_ITPLN

## Import Library
```python
import cv2
import numpy as np
from matplotlib import pyplot as plt
```
* cv2, atau kependekan dari OpenCV, adalah sebuah library open-source yang powerful untuk pengolahan citra (image processing) dan penglihatan komputer (computer vision) di Python.  Library ini menyediakan berbagai fungsi untuk memanipulasi dan menganalisis gambar dan video.
* numpy, yang biasa disingkat menjadi np,  adalah singkatan dari Numerical Python.  Library ini merupakan library open-source fundamental yang banyak digunakan untuk komputasi numerik di Python.  numpy menyediakan berbagai fungsi efisien untuk operasi matematis pada array, matriks, dan tensor.
* Dalam kode Python yang Anda berikan, baris from matplotlib import pyplot as plt digunakan untuk mengimpor modul pyplot dari library matplotlib.  Mari kita bahas library dan modul ini satu per satu

## Membaca Gambar
```python
image = cv2.imread("UTS.jpg")
```
* Kode Python image = cv2.imread("UTS.jpg") digunakan untuk membaca gambar bernama UTS.jpg dan menyimpannya dalam variabel image. Variabel image kemudian dapat digunakan untuk berbagai operasi pemrosesan gambar.

## Konvert BGR ke RGB
```python
rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
```
* rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB) digunakan untuk mengubah format warna gambar dari BGR ke RGB dan menyimpan hasil konversi dalam variabel rgb. Variabel rgb kemudian dapat digunakan untuk berbagai operasi pemrosesan gambar yang kompatibel dengan format RGB.

  ```python
  plt.imshow(rgb)
  ```
  * plt.imshow(rgb) digunakan untuk menampilkan gambar yang tersimpan dalam variabel rgb menggunakan modul matplotlib.pyplot. Hal ini memungkinkan kita untuk melihat secara visual gambar yang sedang kita proses.
```python
# 2. Convert to Grayscale
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# 3. Adjust Contrast and Brightness
alpha = 1.5  # kontras
beta = 30    # kecerahan
adjusted = cv2.convertScaleAbs(image, alpha=alpha, beta=beta)

# 4. Display Results
plt.figure(figsize=(10, 5))
plt.subplot(1, 2, 1)
plt.title('Original Image')
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB),)
plt.axis('off')

plt.subplot(1, 2, 2)
plt.title('Brightened Image')
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB))
plt.axis('off')

plt.show()
```
* Konversi ke Grayscale (Skala Keabuan):

Baris pertama gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY) mengubah gambar berwarna (biasanya dalam format BGR) menjadi skala keabuan. Fungsi cv2.cvtColor dari library OpenCV digunakan untuk konversi ini.

* Penyesuaian Kontras dan Kecerahan:

 *  Baris kedua dan ketiga alpha = 1.5 dan beta = 30 mendefinisikan       nilai untuk kontras dan kecerahan.
 *  Baris keempat adjusted = cv2.convertScaleAbs(image, alpha=alpha,      beta=beta) menggunakan fungsi cv2.convertScaleAbs untuk               menyesuaikan   kontras dan kecerahan gambar.
  * Parameter alpha mengontrol kontras. Nilai yang lebih besar dari 1     meningkatkan kontras, sedangkan nilai yang lebih kecil dari 1         menurunkannya.
  * Parameter beta mengontrol kecerahan. Nilai positif menambah           kecerahan, sedangkan nilai negatif menguranginya
* Menampilkan Hasil:

Baris-baris selanjutnya digunakan untuk menampilkan gambar asli dan gambar yang sudah diproses menggunakan library Matplotlib.
  * Fungsi plt.figure membuat jendela untuk menampilkan gambar.
  * Fungsi plt.subplot membagi jendela menjadi dua bagian (baris ke-      1, kolom ke-2) untuk menampilkan dua gambar secara berdampingan.
  * Baris dengan plt.title menambahkan judul untuk setiap gambar.
  * Fungsi plt.imshow menampilkan gambar pada setiap subplot.             Perhatikan pemanggilan cv2.cvtColor(image, cv2.COLOR_BGR2RGB)         sebelum   plt.imshow untuk gambar asli, karena Matplotlib             mengharapkan format RGB.
  * plt.axis('off') menyembunyikan sumbu pada setiap subplot untuk        tampilan yang lebih bersih.
Baris terakhir plt.show() menampilkan jendela yang berisi kedua gambar.

## Deteksi RGB
```python
plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB))
plt.title('Original Image')

# Display the red channel
plt.subplot(2, 2, 2)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0], cmap="gray")
plt.title('Red Channel')

# Display the green channel
plt.subplot(2, 2, 3)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1], cmap="gray")
plt.title('Green Channel')

# Display the blue channel
plt.subplot(2, 2, 4)
plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2], cmap="gray")
plt.title('Blue Channel')

plt.show()
```
* Menampilkan Gambar Asli:

  * plt.subplot(2, 2, 1): Baris ini membuat subplot di baris ke-1,   
    kolom ke-1 pada figure window.
  * plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)): Baris ini 
    seharusnya menampilkan gambar, namun labelnya salah. Seharusnya 
    ini menampilkan gambar yang sudah diproses (adjusted), bukan   
    gambar asli.
  * plt.title('Original Image'): Judul subplot ini seharusnya 
    diganti menjadi "Adjusted Image" karena memang menampilkan hasil     penyesuaian kontras dan kecerahan.

* Menampilkan Kanal Merah:

  * plt.subplot(2, 2, 2): Baris ini membuat subplot di baris ke-1, 
    kolom ke-2.
  * plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0],   
    cmap="gray"): Baris ini menampilkan kanal merah dari gambar yang 
    sudah diproses (adjusted).
      * [:,:,0] mengakses elemen pada indeks ke-0 (sesuai urutan   
        BGR) untuk mengambil kanal merah.
      * cmap="gray" menetapkan colormap menjadi grayscale untuk   
        menampilkan kanal merah sebagai gambar keabuan.
      * plt.title('Red Channel'): Judul subplot ini dengan tepat 
        menunjukkan bahwa yang ditampilkan adalah kanal merah.
        
* Menampilkan Kanal Hijau:

    * plt.subplot(2, 2, 3): Baris ini membuat subplot di baris ke-2, 
      kolom ke-1.
    * plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1], 
      cmap="gray"): Baris ini menampilkan kanal hijau dari gambar   
      yang sudah diproses.
        * [:,:,1] mengakses elemen pada indeks ke-1 (sesuai urutan 
          BGR) untuk mengambil kanal hijau.
    * plt.title('Green Channel'): Judul subplot ini dengan tepat     
      menunjukkan bahwa yang ditampilkan adalah kanal hijau.

* Menampilkan Kanal Biru:

    * plt.subplot(2, 2, 4): Baris ini membuat subplot di baris ke-2,       kolom ke-2.
    * plt.imshow(cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2], 
      cmap="gray"): Baris ini menampilkan kanal biru dari gambar 
      yang sudah diproses.
        * [:,:,2] mengakses elemen pada indeks ke-2 (sesuai urutan              BGR) untuk mengambil kanal biru.
    * plt.title('Blue Channel'): Judul subplot ini dengan tepat   
      menunjukkan bahwa yang ditampilkan adalah kanal biru.

* Menampilkan Hasil:

  * plt.show(): Baris ini menampilkan figure window yang berisi:
    * Subplot 1 (salah label) yang seharusnya menampilkan gambar           hasil penyesuaian kontras dan kecerahan.
    * Subplot 2, 3, dan 4 yang masing-masing menampilkan kanal 
      merah, hijau, dan biru dari gambar hasil penyesuaian.
```python
merah=cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0] #Merah
fig, axs = plt.subplots(1,2, figsize = (15,5))
hist = cv2.calcHist([merah],[0],None,[256],[0,256])
axs[0].imshow(merah, cmap='gray')
axs[1].plot(hist)
plt.show()
```
* Ekstraksi Kanal Merah:

* merah = cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0]: Baris 
  ini mengambil kanal merah dari gambar yang sudah diproses 
  (adjusted).
    * cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB) mengonversi gambar         dari format BGR ke RGB (karena OpenCV menggunakan BGR secara   
      default).
    * [:,:,0] mengakses elemen pada indeks ke-0 (sesuai urutan BGR)        untuk mengekstraksi kanal merah dan disimpan dalam variabel          merah

* Menampikan Kanal Merah dan Histogram:

    *  fig, axs = plt.subplots(1,2, figsize = (15,5)): Baris ini   
     membuat figure window dengan ukuran (15 unit lebar, 5 unit 
     tinggi) dan membagi figure tersebut menjadi 1 baris dan 2 kolom      untuk menampilkan plot. Variabel fig menyimpan informasi   
     keseluruhan figure, sedangkan axs adalah sebuah array yang     
     berisi objek-objek untuk masing-masing subplot (dalam hal ini   
     ada 2 subplot).
    * hist = cv2.calcHist([merah],[0],None,[256],[0,256]): Baris ini       menghitung histogram untuk kanal merah yang tersimpan di 
      variabel merah
        *cv2.calcHist adalah fungsi dari OpenCV untuk menghitung   
         histogram.
        * Parameter pertama [merah] adalah list yang berisi image 
         array (dalam hal ini hanya kanal merah).
        * Parameter kedua [0] menunjukkan bahwa histogram dihitung   
         hanya untuk kanal ke-0 (kanal merah).
        * Parameter ketiga None menunjukkan tidak ada mask yang   
         digunakan.
        * Parameter keempat [256] menetapkan jumlah bin (interval)   
         untuk histogram menjadi 256 (mencakup semua nilai     
         intensitas pixel dari 0 sampai 255).
        * Parameter kelima [0,256] menetapkan range untuk histogram 
         dari 0 sampai 256 (sesuai nilai intensitas pixel).
        * Variabel hist akan berisi array yang merepresentasikan     
         histogram, di mana setiap elemen menunjukkan jumlah pixel 
         dengan intensitas tertentu.
    * axs[0].imshow(merah, cmap='gray'): Baris ini menampilkan kanal merah (merah) pada subplot pertama (axs[0]).
cmap='gray' menetapkan colormap menjadi grayscale untuk menampilkan kanal merah sebagai gambar keabuan.
    * axs[1].plot(hist): Baris ini menampilkan histogram yang tersimpan di variabel hist pada subplot kedua (axs[1]).
plot digunakan untuk membuat plot dari data histogram.

* Menampilkan Hasil:

    * plt.show(): Baris ini menampilkan figure window yang berisi:
      Subplot pertama yang menampilkan kanal merah sebagai gambar   
      grayscale.
    * Subplot kedua yang menampilkan histogram distribusi intensitas 
      pixel pada kanal merah.

```python
hijau=cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,1] #hijau
fig, axs = plt.subplots(1,2, figsize = (15,5))
hist = cv2.calcHist([hijau],[0],None,[256],[0,256])
axs[0].imshow(hijau, cmap='gray')
axs[1].plot(hist)
plt.show()
```
* Ekstraksi Kanal hijau :

* hijau = cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0]: Baris 
  ini mengambil kanal hijau dari gambar yang sudah diproses 
  (adjusted).
    * cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB) mengonversi gambar         dari format BGR ke RGB (karena OpenCV menggunakan BGR secara   
      default).
    * [:,:,0] mengakses elemen pada indeks ke-0 (sesuai urutan BGR)        untuk mengekstraksi kanal hijau dan disimpan dalam variabel          hijau

* Menampikan Kanal hijau dan Histogram:

    *  fig, axs = plt.subplots(1,2, figsize = (15,5)): Baris ini   
     membuat figure window dengan ukuran (15 unit lebar, 5 unit 
     tinggi) dan membagi figure tersebut menjadi 1 baris dan 2 kolom      untuk menampilkan plot. Variabel fig menyimpan informasi   
     keseluruhan figure, sedangkan axs adalah sebuah array yang     
     berisi objek-objek untuk masing-masing subplot (dalam hal ini   
     ada 2 subplot).
    * hist = cv2.calcHist([hijau],[0],None,[256],[0,256]): Baris ini       menghitung histogram untuk kanal hijau yang tersimpan di 
      variabel hijau
        *cv2.calcHist adalah fungsi dari OpenCV untuk menghitung   
         histogram.
        * Parameter pertama [hijau] adalah list yang berisi image 
         array (dalam hal ini hanya kanal hijau).
        * Parameter kedua [0] menunjukkan bahwa histogram dihitung   
         hanya untuk kanal ke-0 (kanal hijau).
        * Parameter ketiga None menunjukkan tidak ada mask yang   
         digunakan.
        * Parameter keempat [256] menetapkan jumlah bin (interval)   
         untuk histogram menjadi 256 (mencakup semua nilai     
         intensitas pixel dari 0 sampai 255).
        * Parameter kelima [0,256] menetapkan range untuk histogram 
         dari 0 sampai 256 (sesuai nilai intensitas pixel).
        * Variabel hist akan berisi array yang merepresentasikan     
         histogram, di mana setiap elemen menunjukkan jumlah pixel 
         dengan intensitas tertentu.
    * axs[0].imshow(hijau, cmap='gray'): Baris ini menampilkan kanal hijau (hijau) pada subplot pertama (axs[0]).
cmap='gray' menetapkan colormap menjadi grayscale untuk menampilkan kanal hijau sebagai gambar keabuan.
    * axs[1].plot(hist): Baris ini menampilkan histogram yang tersimpan di variabel hist pada subplot kedua (axs[1]).
plot digunakan untuk membuat plot dari data histogram.

* Menampilkan Hasil:

    * plt.show(): Baris ini menampilkan figure window yang berisi:
      Subplot pertama yang menampilkan kanal hijau sebagai gambar   
      grayscale.
    * Subplot kedua yang menampilkan histogram distribusi intensitas 
      pixel pada kanal hijau.

```python
biru=cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,2] #biru
fig, axs = plt.subplots(1,2, figsize = (15,5))
hist = cv2.calcHist([biru],[0],None,[256],[0,256])
axs[0].imshow(biru, cmap='gray')
axs[1].plot(hist)
plt.show()
```
* Ekstraksi Kanal Biru :

* Biru = cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB)[:,:,0]: Baris 
  ini mengambil kanal Biru dari gambar yang sudah diproses 
  (adjusted).
    * cv2.cvtColor(adjusted, cv2.COLOR_BGR2RGB) mengonversi gambar         dari format BGR ke RGB (karena OpenCV menggunakan BGR secara   
      default).
    * [:,:,0] mengakses elemen pada indeks ke-0 (sesuai urutan BGR)        untuk mengekstraksi kanal Biru dan disimpan dalam variabel          Biru

* Menampikan Kanal Biru dan Histogram:

    *  fig, axs = plt.subplots(1,2, figsize = (15,5)): Baris ini   
     membuat figure window dengan ukuran (15 unit lebar, 5 unit 
     tinggi) dan membagi figure tersebut menjadi 1 baris dan 2 kolom      untuk menampilkan plot. Variabel fig menyimpan informasi   
     keseluruhan figure, sedangkan axs adalah sebuah array yang     
     berisi objek-objek untuk masing-masing subplot (dalam hal ini   
     ada 2 subplot).
    * hist = cv2.calcHist([Biru],[0],None,[256],[0,256]): Baris ini       menghitung histogram untuk kanal Biru yang tersimpan di 
      variabel Biru
        *cv2.calcHist adalah fungsi dari OpenCV untuk menghitung   
         histogram.
        * Parameter pertama [Biru] adalah list yang berisi image 
         array (dalam hal ini hanya kanal hijau).
        * Parameter kedua [0] menunjukkan bahwa histogram dihitung   
         hanya untuk kanal ke-0 (kanal Biru).
        * Parameter ketiga None menunjukkan tidak ada mask yang   
         digunakan.
        * Parameter keempat [256] menetapkan jumlah bin (interval)   
         untuk histogram menjadi 256 (mencakup semua nilai     
         intensitas pixel dari 0 sampai 255).
        * Parameter kelima [0,256] menetapkan range untuk histogram 
         dari 0 sampai 256 (sesuai nilai intensitas pixel).
        * Variabel hist akan berisi array yang merepresentasikan     
         histogram, di mana setiap elemen menunjukkan jumlah pixel 
         dengan intensitas tertentu.
    * axs[0].imshow(Biru, cmap='gray'): Baris ini menampilkan kanal hijau (hijau) pada subplot pertama (axs[0]).
cmap='gray' menetapkan colormap menjadi grayscale untuk menampilkan kanal Biru sebagai gambar keabuan.
    * axs[1].plot(hist): Baris ini menampilkan histogram yang tersimpan di variabel hist pada subplot kedua (axs[1]).
plot digunakan untuk membuat plot dari data histogram.

* Menampilkan Hasil:

    * plt.show(): Baris ini menampilkan figure window yang berisi:
      Subplot pertama yang menampilkan kanal hijau sebagai gambar   
      grayscale.
    * Subplot kedua yang menampilkan histogram distribusi intensitas 
      pixel pada kanal Biru.

## Ambang Batas
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

# Baca gambar
image = cv2.imread('UTS.jpg')
# Convert citra ke grayscale
gray = cv2.cvtColor(image, cv2.COLOR_RGB2GRAY)

# Inisialisasi subplot
fig, axs = plt.subplots(2, 2, figsize=(10,10))

# Ambang batas untuk mendapatkan citra biner (none)
(thresh, binary1) = cv2.threshold(gray, 0, 255, cv2.THRESH_BINARY)
axs[0,0].imshow(binary1, cmap = 'gray')
axs[0,0].set_title('NONE')

# Convert citra ke HSV
image_hsv = cv2.cvtColor(image, cv2.COLOR_BGR2HSV)

# Definisikan range warna biru dalam HSV
blue_lower = np.array([100, 50, 50])
blue_upper = np.array([140, 255, 255])

# Membuat mask untuk warna biru
mask_blue = cv2.inRange(image_hsv, blue_lower, blue_upper)
axs[0,1].imshow(mask_blue, cmap='gray')
axs[0,1].set_title('BLUE')

# Ambang batas untuk mendapatkan citra biner (red-blue)
(thresh, binary3) = cv2.threshold(gray, 43, 255, cv2.THRESH_BINARY)
axs[1,0].imshow(binary3, cmap = 'binary')
axs[1,0].set_title('RED-BLUE')

# Ambang batas untuk mendapatkan citra biner (red-green-blue)
(thresh, binary4) = cv2.threshold(gray, 80, 255, cv2.THRESH_BINARY)
axs[1,1].imshow(binary4, cmap = 'binary')
axs[1,1].set_title('RED-GREEN-BLUE')

plt.show()

* image = cv2.imread('UTS.jpg'): Membaca gambar dari file bernama "UTS.jpg" dan menyimpannya dalam variabel image. Pastikan nama file gambar sesuai dengan yang Anda miliki.
* gray = cv2.cvtColor(image, cv2.COLOR_RGB2GRAY): Mengubah gambar berwarna (image) menjadi skala keabuan (gray) menggunakan fungsi cv2.cvtColor dari OpenCV

* fig, axs = plt.subplots(2, 2, figsize=(10,10)): Membuat jendela tampilan (figure window) menggunakan plt.subplots.
Jendela ini dibagi menjadi grid 2 baris dan 2 kolom menggunakan parameter 2, 2.
* Variabel fig menyimpan informasi keseluruhan jendela, sedangkan axs adalah array yang berisi objek-objek untuk masing-masing subplot (4 subplot dalam hal ini).

*  Deteksi Tanpa Ambang Batas (NONE):

*(thresh, binary1) = cv2.threshold(gray, 0, 255, cv2.THRESH_BINARY): Menerapkan thresholding pada gambar grayscale (gray) dengan cv2.threshold.
* Nilai ambang batas bawah 0 dan atas 255 artinya semua pixel diubah menjadi hitam (0) atau putih (255) tanpa filtering berdasarkan intensitas, menghasilkan citra biner penuh.
* axs[0,0].imshow(binary1, cmap = 'gray'): Menampilkan citra biner (binary1) pada subplot baris ke-0, kolom ke-0 dengan colormap grayscale.
* axs[0,0].set_title('NONE'): Menambahkan judul "NONE" pada subplot ini karena tidak ada filtering yang diterapkan.

* Deteksi Warna Biru (BLUE)
  * image_hsv = cv2.cvtColor(image, cv2.COLOR_BGR2HSV): Mengubah gambar berwarna (image) menjadi ruang warna HSV menggunakan cv2.cvtColor. Ruang warna HSV sering lebih baik untuk mendeteksi warna tertentu
  * blue_lower = np.array([100, 50, 50]) dan blue_upper = np.array([140, 255, 255]): Mendefinisikan range warna biru yang ingin dideteksi dalam HSV. Nilai-nilai ini dapat disesuaikan untuk rentang biru yang lebih spesifik.
* mask_blue = cv2.inRange(image_hsv, blue_lower, blue_upper): Membuat mask untuk warna biru. cv2.inRange mengembalikan elemen True (putih) untuk pixel yang berada di dalam range warna yang ditentukan, dan False (hitam) untuk yang di luar range tersebut
