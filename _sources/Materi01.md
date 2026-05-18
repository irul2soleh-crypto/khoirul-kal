# Materi 1

# Eliminasi Gaussian
Eliminasi Gaussian adalah metode untuk menyelesaikan sistem persamaan linear dengan cara mengubahnya menjadi bentuk yang lebih sederhana menggunakan operasi baris.
Tujuannya:
Mengubah sistem menjadi bentuk eselon baris
Supaya solusi lebih mudah ditemukan
# Matriks

Matriks adalah susunan bilangan berbentuk persegi panjang yang terdiri dari baris dan kolom. Matriks sering digunakan untuk merepresentasikan sistem persamaan linear dalam bentuk yang lebih ringkas. Matriks augmentasi adalah matriks yang diperoleh dengan menggabungkan matriks koefisien dan hasil dari sistem persamaan. Dengan menggunakan matriks augmentasi, proses penyelesaian SPL menjadi lebih efisien karena dapat dilakukan melalui operasi baris.

Matriks adalah susunan angka berbentuk tabel (baris & kolom).
Contoh:

​

# Matriks Augmentasi

Matriks yang menggabungkan:

Koefisien variabel
Hasil persamaan


# Bentuk Eselon Baris 
Bentuk eselon baris adalah bentuk matriks yang telah disederhanakan dengan aturan tertentu. Dalam bentuk ini, semua baris nol berada di bagian bawah, setiap baris memiliki elemen pertama yang bukan nol (disebut pivot), dan posisi pivot pada setiap baris berada lebih ke kanan dibandingkan baris di atasnya. Bentuk ini menyerupai pola tangga, sehingga sering disebut sebagai bentuk tangga.

Matriks dikatakan bentuk eselon baris jika:

Baris nol ada di bawah
Angka pertama (pivot) = 1
Pivot ke bawah semakin ke kanan (bentuk tangga)

 

 # Bentuk Eselon Baris Tereduksi (RREF)

Bentuk eselon baris tereduksi merupakan bentuk lanjutan dari eselon baris. Pada bentuk ini, setiap pivot bernilai 1 dan menjadi satu-satunya elemen yang tidak nol pada kolomnya. Artinya, semua elemen di atas dan di bawah pivot harus bernilai nol. Bentuk ini adalah bentuk paling sederhana dari suatu matriks dan memudahkan dalam membaca solusi secara langsung.

 Setiap kolom pivot hanya punya satu angka ≠ 0 (yang lain harus 0)

# Operasi Baris Elementer

Dalam eliminasi Gaussian, terdapat tiga jenis operasi baris elementer yang digunakan. Pertama adalah perkalian skalar, yaitu mengalikan suatu baris dengan bilangan tidak nol. Kedua adalah pertukaran baris, yaitu menukar posisi dua baris dalam matriks. Ketiga adalah penjumlahan baris, yaitu menambahkan kelipatan suatu baris ke baris lainnya. Ketiga operasi ini tidak mengubah solusi dari sistem persamaan.



# Penyelesaian Sistem Persamaan Linier (SPL) menggunakan Eliminasi Gaussian

## A. Sistem Persamaan Linear Tiga Variabel

$\begin{cases}
x + y + z = 6 \\
2x + 3y + z = 10 \\
x + 2y + 3z = 13
\end{cases}$

**Penyelesaian:**
### 1. Ubah ke Matriks Augmented
1. Kode:
    ```python
    A = matrix([[1, 1, 1, 6], [2, 3, 1, 10], [1, 2, 3, 13]])
    A

2. Output:

    $\left[
    \begin{array}{ccc|c}
    1 & 1 & 1 & 6 \\
    2 & 3 & 1 & 10 \\
    1 & 2 & 3 & 13
    \end{array}
    \right]$

### 2. Eliminasi Gaussian (Operasi Baris Elementer)
1. Hilangkan elemen di bawah pivot pertama

    Baris 2 → R2 − 2R1
    Baris 3 → R3 − R1

    *Artinya:* Menghilangkan angka pertama agar jadi 0 dengan menggunakan **A.add_multiple_of_row** untuk melakukan perkalian kemudian penjumlahan.
    -  A.add_multiple_of_row(1, 0, -2) *Artinya:* Tambahkan -2* (baris 0) ke baris 1
    -  A.add_multiple_of_row(2, 0, -1) *Artinya:* Tambahkan -1* (baris 0) ke baris 2

        1. Kode:
            ```python
            A.add_multiple_of_row(1, 0, -2)
            A.add_multiple_of_row(2, 0, -1)
            A

        2. Output:

            $\left[
            \begin{array}{ccc|c}
            1 & 1 & 1 & 6 \\
            0 & 1 & -1 & -2 \\
            0 & 1 & 2 & 7
            \end{array}
            \right]$

2. Hilangkan elemen di bawah pivot kedua

    Baris 3 → R3 − R2

    *Artinya:* Menghilangkan angka pertama agar jadi 0 dengan menggunakan **A.add_multiple_of_row** untuk melakukan perkalian kemudian penjumlahan.
    -  A.add_multiple_of_row(2, 1, -1) *Artinya:* Tambahkan -1* (baris 1) ke baris 2

        1. Kode:
            ```python
            A.add_multiple_of_row(2, 1, -1)
            A
        
        2. Output:

           $\left[
            \begin{array}{ccc|c}
            1 & 1 & 1 & 6 \\
            0 & 1 & -1 & -2 \\
            0 & 0 & 3 & 9
            \end{array}
            \right]$

3. Substitusi Balik

    1. Dari baris ketiga:

        $3z = 9 \Rightarrow z = 3$
    2. Baris kedua:

       $y - z = -2
        y - 3 = -2 \Rightarrow y = 1$
    3. Baris Pertama

        $x + y + z = 6
        x + 1 + 3 = 6 \Rightarrow x = 2$
       
        **ATAU:**

4. Jadikan pivot ketiga = 1
    Baris 3 → R3 ÷ 3

    1. Kode:
         ```python
        A.rescale_row(2, 1/3)
        A
    2. Output

        $\left[
            \begin{array}{ccc|c}
            1 & 1 & 1 & 6 \\
            0 & 1 & -1 & -2 \\
            0 & 0 & 1 & 3
            \end{array}
            \right]$
    3. Substitusi Balik (Manual)

        $z = 3
        y - z = -2 \Rightarrow y = 1
        x + y + z = 6 \Rightarrow x = 2$


5. Solusi (Hasil)

    $(x, y, z) = (2, 1, 3)$
   
## B. Sistem Persamaan Linear Empat Variabel

$\begin{cases}
x + y + z + w = 10 \\
2x + y + z + w = 13 \\
x + 2y + z + w = 14 \\
x + y + 2z + w = 15
\end{cases}$

**Penyelesaian:**
### 1. Ubah ke Matriks Augmented
1. Kode:
    ```python
    A = matrix([[1, 1, 1, 1, 10], [2, 1, 1, 1, 13], [1, 2, 1, 1, 14], [1, 1, 2, 1, 15]])
    A
2. Output:
    $\begin{cases}
    x + y + z + w = 10 \\
    2x + y + z + w = 13 \\
    x + 2y + z + w = 14 \\
    x + y + 2z + w = 15
    \end{cases}$

### 2. Eliminasi Gaussian (Operasi Baris Elementer)
1. Hilangkan elemen di bawah pivot pertama
    B2 → B2 − 2B1,
    B3 → B3 − B1,
    B4 → B4 − B1

    *Artinya:* Menghilangkan angka pertama agar jadi 0 dengan menggunakan **A.add_multiple_of_row** untuk melakukan perkalian kemudian penjumlahan.
    -  A.add_multiple_of_row(1, 0, -2) *Artinya:* Tambahkan -2* (baris 0) ke baris 1
    -  A.add_multiple_of_row(2, 0, -1) *Artinya:* Tambahkan -1* (baris 0) ke baris 2
    -  A.add_multiple_of_row(3, 0, -1) *Artinya:* Tambahkan -1* (baris 0) ke baris 3

        1. Kode:

            ```python
            A.add_multiple_of_row(1, 0, -2)
            A.add_multiple_of_row(2, 0, -1)
            A.add_multiple_of_row(3, 0, -1)
            A

        2. Output:

            $\left[
            \begin{array}{cccc|c}
            1 & 1 & 1 & 1 & 10 \\
            0 & -1 & -1 & -1 & -7 \\
            0 & 1 & 0 & 0 & 4 \\
            0 & 0 & 1 & 0 & 5
            \end{array}
            \right]$

2. Tukar B2 (baris 1) dan B3 (baris 2) (agar pivot positif)
    1. Kode:

        ```python
        A.swap_rows(1, 2)
        A

    - A.swap_rows(1, 2) *Artnya:* Tukar baris 1 dan 2

    2. Output:

        $\left[
        \begin{array}{cccc|c}
        1 & 1 & 1 & 1 & 10 \\
        0 & 1 & 0 & 0 & 4 \\
        0 & -1 & -1 & -1 & -7 \\
        0 & 0 & 1 & 0 & 5
        \end{array}
        \right]$

3. Hilangkan elemen di bawah pivot kedua
    B3 → B3 + B2

    1. Kode:

        ```python
        A.add_multiple_of_row(2, 1, 1)
        A

    2. Output:

        $\left[
        \begin{array}{cccc|c}
        1 & 1 & 1 & 1 & 10 \\
        0 & 1 & 0 & 0 & 4 \\
        0 & 0 & -1 & -1 & -3 \\
        0 & 0 & 1 & 0 & 5
        \end{array}
        \right]$

4. Hilangkan elemen di bawah pivot ketiga
    B4 → B4 + B3

    1. Kode:

        ```python
        A.add_multiple_of_row(3, 2, 1)
        A
    
    2. Output:

        $\left[
        \begin{array}{cccc|c}
        1 & 1 & 1 & 1 & 10 \\
        0 & 1 & 0 & 0 & 4 \\
        0 & 0 & -1 & -1 & -3 \\
        0 & 0 & 0 & -1 & 2
        \end{array}
        \right]$

5. Substitusi Balik
    1. Dari baris 4:

        $−w = \Rightarrow 2 w = −2$
    
    2. Baris 3

        $−z −w = −3
        −z + 2 = −3
        z = 5$
    
    3. Baris 2

        $y = 4$
    
    4. Baris 1

        $x + y + z + w = 10
        x + 4 + 5 − 2 = 10
        x = 3$

        **ATAU**

6. Jadikan pivot ketiga dan keempat = 1
    1. Kode:

        ```python
        A.rescale_row(2, -1)
        A.rescale_row(3, -1)
        A

    2. Output:

        $\begin{bmatrix}
        1 & 1 & 1 & 1 & 10 \\
        0 & 1 & 0 & 0 & 4 \\
        0 & 0 & -1 & -1 & -3 \\
        0 & 0 & 0 & -1 & 2
        \end{bmatrix}$

    3. Substitusi Balik (Manual)

        $w = −2
        z = 5
        y = 4
        x = 3$

7. Solusi (Hasil)

    $(x,y,z,w) = (3,4,5,−2)$ 