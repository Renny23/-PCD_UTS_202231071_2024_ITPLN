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
