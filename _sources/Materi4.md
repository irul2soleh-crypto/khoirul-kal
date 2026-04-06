#Pengertian Matriks

Matriks adalah susunan bilangan yang disusun dalam bentuk baris (row) dan kolom (column).

Bentuk umum:

𝐴
=
[
𝑎
𝑖
𝑗
]
A=[a
ij
	​

]

Contoh:

𝐴
=
[
1
	
2
	
3


4
	
5
	
6
]
A=[
1
4
	​

2
5
	​

3
6
	​

]
Ordo matriks: 
𝑚
×
𝑛
m×n
m = jumlah baris
n = jumlah kolom

Jenis-Jenis Matriks
Matriks Persegi
𝑛
×
𝑛
n×n
Matriks Nol
Semua elemen = 0
Matriks Identitas
𝐼
=
[
1
	
0


0
	
1
]
I=[
1
0
	​

0
1
	​

]
Matriks Diagonal
Elemen selain diagonal utama = 0
Matriks Segitiga
Segitiga atas
Segitiga bawah
📘 2.1 Aritmetika Matriks
📌 1. Penjumlahan Matriks

Syarat: ukuran sama

𝐴
+
𝐵
=
[
𝑎
𝑖
𝑗
+
𝑏
𝑖
𝑗
]
A+B=[a
ij
	​

+b
ij
	​

]

Contoh:

[
1
	
2


3
	
4
]
+
[
5
	
6


7
	
8
]
=
[
6
	
8


10
	
12
]
[
1
3
	​

2
4
	​

]+[
5
7
	​

6
8
	​

]=[
6
10
	​

8
12
	​

]
📌 2. Pengurangan Matriks
𝐴
−
𝐵
=
[
𝑎
𝑖
𝑗
−
𝑏
𝑖
𝑗
]
A−B=[a
ij
	​

−b
ij
	​

]
📌 3. Perkalian Skalar
𝑘
𝐴
kA

Contoh:

2
[
1
	
2


3
	
4
]
=
[
2
	
4


6
	
8
]
2[
1
3
	​

2
4
	​

]=[
2
6
	​

4
8
	​

]
📌 4. Perkalian Matriks

Syarat:

(
𝑚
×
𝑛
)
⋅
(
𝑛
×
𝑝
)
(m×n)⋅(n×p)

Rumus:

𝑐
𝑖
𝑗
=
∑
𝑎
𝑖
𝑘
𝑏
𝑘
𝑗
c
ij
	​

=∑a
ik
	​

b
kj
	​


Contoh:

[
1
	
2


3
	
4
]
⋅
[
5
	
6


7
	
8
]
=
[
19
	
22


43
	
50
]
[
1
3
	​

2
4
	​

]⋅[
5
7
	​

6
8
	​

]=[
19
43
	​

22
50
	​

]
📌 Implementasi Python
import numpy as np

A = np.array([[1,2],[3,4]])
B = np.array([[5,6],[7,8]])

print("Penjumlahan:\n", A + B)
print("Perkalian:\n", A @ B)
📘 2.2 Aljabar Matriks
📌 Sifat-Sifat Matriks
1. Asosiatif
(
𝐴
𝐵
)
𝐶
=
𝐴
(
𝐵
𝐶
)
(AB)C=A(BC)
2. Distributif
𝐴
(
𝐵
+
𝐶
)
=
𝐴
𝐵
+
𝐴
𝐶
A(B+C)=AB+AC
3. Tidak Komutatif
𝐴
𝐵
≠
𝐵
𝐴
AB

=BA
📌 Transpose Matriks
𝐴
𝑇
A
T

Contoh:

[
1
	
2


3
	
4
]
𝑇
=
[
1
	
3


2
	
4
]
[
1
3
	​

2
4
	​

]
T
=[
1
2
	​

3
4
	​

]

Python:

print(A.T)
📌 Matriks Simetris
𝐴
=
𝐴
𝑇
A=A
T
📌 Matriks Ortogonal
𝐴
𝑇
𝐴
=
𝐼
A
T
A=I
📘 2.3 Matriks Invertibel
📌 Pengertian

Matriks invertibel adalah matriks yang memiliki invers.

𝐴
−
1
A
−1
📌 Syarat Invers
Matriks persegi
Determinan ≠ 0
📌 Rumus Invers 2x2
𝐴
−
1
=
1
𝑎
𝑑
−
𝑏
𝑐
[
𝑑
	
−
𝑏


−
𝑐
	
𝑎
]
A
−1
=
ad−bc
1
	​

[
d
−c
	​

−b
a
	​

]
📌 Contoh
𝐴
=
[
1
	
2


3
	
4
]
A=[
1
3
	​

2
4
	​

]
📌 Implementasi Python
import numpy as np

A = np.array([[1,2],[3,4]])
print(np.linalg.inv(A))
📘 2.4 Teorema Invertibilitas
📌 Pernyataan

Matriks A invertibel jika dan hanya jika:

Determinan tidak nol
Memiliki invers
Rank penuh
Tidak ada baris nol
Sistem AX = B punya solusi unik
📌 Identitas Penting
𝐴
−
1
𝐴
=
𝐼
A
−1
A=I
📌 Makna
Matriks dapat “dibalik”
Solusi sistem linear bisa ditemukan dengan:
𝑋
=
𝐴
−
1
𝐵
X=A
−1
B
📘 2.5 Determinan
📌 Pengertian

Determinan adalah nilai skalar dari matriks yang menunjukkan sifat matriks.

📌 Determinan 2x2
∣
𝑎
	
𝑏


𝑐
	
𝑑
∣
=
𝑎
𝑑
−
𝑏
𝑐
	​

a
c
	​

b
d
	​

	​

=ad−bc
📌 Determinan 3x3 (Sarrus)
∣
𝑎
	
𝑏
	
𝑐


𝑑
	
𝑒
	
𝑓


𝑔
	
ℎ
	
𝑖
∣
	​

a
d
g
	​

b
e
h
	​

c
f
i
	​

	​

📌 Sifat Determinan
det(A) = 0 → tidak invertibel
det(AB) = det(A) det(B)
det(Aᵀ) = det(A)
📌 Implementasi Python
import numpy as np

A = np.array([[1,2],[3,4]])
print(np.linalg.det(A))
📘 Contoh Kasus (Aplikasi)
📌 Sistem Persamaan
2
𝑥
+
𝑦
=
5
𝑥
−
𝑦
=
1
2x+y=5x−y=1

Bentuk matriks:

𝐴
𝑋
=
𝐵
AX=B

Solusi Python:

A = np.array([[2,1],[1,-1]])
B = np.array([5,1])

X = np.linalg.solve(A,B)
print(X)