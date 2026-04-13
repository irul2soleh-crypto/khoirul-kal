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


|1 | 3|
|2 | 4|

	​

# Matriks Augmentasi

Matriks yang menggabungkan:

Koefisien variabel
Hasil persamaan

Contoh:

{x+y=3
{2x+y=5​

Menjadi:

 |1| 1 | 3|
 |2| 1 | 5|

# Bentuk Eselon Baris 
Bentuk eselon baris adalah bentuk matriks yang telah disederhanakan dengan aturan tertentu. Dalam bentuk ini, semua baris nol berada di bagian bawah, setiap baris memiliki elemen pertama yang bukan nol (disebut pivot), dan posisi pivot pada setiap baris berada lebih ke kanan dibandingkan baris di atasnya. Bentuk ini menyerupai pola tangga, sehingga sering disebut sebagai bentuk tangga.

Matriks dikatakan bentuk eselon baris jika:

Baris nol ada di bawah
Angka pertama (pivot) = 1
Pivot ke bawah semakin ke kanan (bentuk tangga)

Contoh:

| 1| 2 |3 |
| 0| 1 | 4|
| 0|0  | 1|
 

 # Bentuk Eselon Baris Tereduksi (RREF)

Bentuk eselon baris tereduksi merupakan bentuk lanjutan dari eselon baris. Pada bentuk ini, setiap pivot bernilai 1 dan menjadi satu-satunya elemen yang tidak nol pada kolomnya. Artinya, semua elemen di atas dan di bawah pivot harus bernilai nol. Bentuk ini adalah bentuk paling sederhana dari suatu matriks dan memudahkan dalam membaca solusi secara langsung.

 Setiap kolom pivot hanya punya satu angka ≠ 0 (yang lain harus 0)
 Contoh:

 
| 1| 0 |0 |
| 0| 1 | 0|
| 0|0  | 1|

# Operasi Baris Elementer

Dalam eliminasi Gaussian, terdapat tiga jenis operasi baris elementer yang digunakan. Pertama adalah perkalian skalar, yaitu mengalikan suatu baris dengan bilangan tidak nol. Kedua adalah pertukaran baris, yaitu menukar posisi dua baris dalam matriks. Ketiga adalah penjumlahan baris, yaitu menambahkan kelipatan suatu baris ke baris lainnya. Ketiga operasi ini tidak mengubah solusi dari sistem persamaan.

R1​→2R1​
| 1 |3 |
​| 2 | 4​|

|2 |3 |
|4 |4 |
