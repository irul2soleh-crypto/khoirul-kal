# Invers Matriks

## Pengertian Invers Matriks

Invers matriks adalah kebalikan dari suatu matriks persegi yang jika dikalikan dengan matriks asalnya akan menghasilkan matriks identitas.

Untuk suatu matriks persegi \(A\), inversnya dinotasikan dengan \(A^{-1}\) dan memenuhi:

$$
AA^{-1}=A^{-1}A=I
$$

dengan \(I\) adalah matriks identitas.

Sebagai contoh, untuk matriks identitas orde \(n\):

$$
I=
\begin{bmatrix}
1 & 0 & \cdots & 0\\
0 & 1 & \cdots & 0\\
\vdots & \vdots & \ddots & \vdots\\
0 & 0 & \cdots & 1
\end{bmatrix}
$$

Tidak semua matriks memiliki invers. Sebuah matriks hanya memiliki invers apabila:

$$
\det(A)\neq 0
$$

Jika

$$
\det(A)=0
$$

maka matriks tersebut disebut **matriks singular** dan tidak memiliki invers.

---

## Sifat-Sifat Invers Matriks

Jika \(A\) dan \(B\) adalah matriks yang memiliki invers, maka berlaku:

### 1. Invers dari invers

$$
(A^{-1})^{-1}=A
$$

### 2. Invers hasil perkalian matriks

$$
(AB)^{-1}=B^{-1}A^{-1}
$$

### 3. Invers matriks identitas

$$
I^{-1}=I
$$

### 4. Invers transpose

$$
(A^T)^{-1}=(A^{-1})^T
$$

### 5. Determinan invers

$$
\det(A^{-1})=\frac{1}{\det(A)}
$$

---

## Metode Mencari Invers Matriks

Terdapat beberapa metode untuk mencari invers matriks, antara lain:

1. Metode Adjoin (Adjugate)
2. Metode Eliminasi Gauss-Jordan
3. Dekomposisi LU

Pada materi ini digunakan konsep invers matriks untuk menyelesaikan sistem persamaan linear.

Rumus umum invers matriks adalah:

$$
A^{-1}=\frac{1}{\det(A)}\operatorname{adj}(A)
$$

dengan:

- \(\det(A)\) = determinan matriks \(A\)
- \(\operatorname{adj}(A)\) = matriks adjoin dari \(A\)

---

# Invers Matriks dan Penyelesaian Sistem Persamaan Linear

## Diketahui

$$
A=
\begin{bmatrix}
1 & 1 & 1 & 1\\
2 & -1 & 1 & -1\\
1 & 2 & -1 & 1\\
3 & -1 & 2 & 1
\end{bmatrix}
$$

$$
B=
\begin{bmatrix}
10\\
-1\\
6\\
11
\end{bmatrix}
$$

Tujuan:

1. Mencari invers matriks \(A\)
2. Menentukan solusi sistem persamaan linear

$$
AX=B
$$

dengan rumus

$$
X=A^{-1}B
$$

---

# Langkah 1: Rumus Invers

Jika

$$
\det(A)\neq 0
$$

maka invers matriks dapat dicari dengan:

$$
A^{-1}=\frac{1}{\det(A)}\operatorname{adj}(A)
$$

Namun untuk matriks orde 4, perhitungan adjoin sangat panjang. Oleh karena itu biasanya digunakan eliminasi Gauss-Jordan.

---

# Langkah 2: Menghitung Determinan

Lakukan operasi baris pada matriks \(A\):

$$
A=
\begin{bmatrix}
1&1&1&1\\
2&-1&1&-1\\
1&2&-1&1\\
3&-1&2&1
\end{bmatrix}
$$

Eliminasi:

$$
R_2 \leftarrow R_2-2R_1
$$

$$
R_3 \leftarrow R_3-R_1
$$

$$
R_4 \leftarrow R_4-3R_1
$$

Diperoleh:

$$
\begin{bmatrix}
1&1&1&1\\
0&-3&-1&-3\\
0&1&-2&0\\
0&-4&-1&-2
\end{bmatrix}
$$

Ekspansi pada kolom pertama:

$$
\det(A)
=
\det
\begin{bmatrix}
-3&-1&-3\\
1&-2&0\\
-4&-1&-2
\end{bmatrix}
$$

Hitung determinan \(3\times3\):

$$
=(-3)
\begin{vmatrix}
-2&0\\
-1&-2
\end{vmatrix}
-
(-1)
\begin{vmatrix}
1&0\\
-4&-2
\end{vmatrix}
+
(-3)
\begin{vmatrix}
1&-2\\
-4&-1
\end{vmatrix}
$$

$$
=(-3)(4)+(-2)+(-3)(-9)
$$

$$
=-12-2+27
$$

$$
=13
$$

Jadi

$$
\boxed{\det(A)=13}
$$

Karena determinan tidak nol, maka matriks \(A\) memiliki invers.

---

# Langkah 3: Mencari Invers Matriks A

Dengan metode Gauss-Jordan diperoleh:

$$
A^{-1}
=
\begin{bmatrix}
-\frac{2}{13} & \frac{1}{13} & \frac{3}{13} & \frac{1}{13}\\
\frac{8}{13} & -\frac{3}{13} & -\frac{4}{13} & -\frac{1}{13}\\
\frac{10}{13} & -\frac{2}{13} & -\frac{8}{13} & \frac{1}{13}\\
-\frac{17}{13} & \frac{4}{13} & \frac{10}{13} & \frac{1}{13}
\end{bmatrix}
$$

atau

$$
A^{-1}
=
\frac1{13}
\begin{bmatrix}
-2&1&3&1\\
8&-3&-4&-1\\
10&-2&-8&1\\
-17&4&10&1
\end{bmatrix}
$$

---

# Langkah 4: Menentukan Solusi Sistem

Gunakan

$$
X=A^{-1}B
$$

$$
X=
\frac1{13}
\begin{bmatrix}
-2&1&3&1\\
8&-3&-4&-1\\
10&-2&-8&1\\
-17&4&10&1
\end{bmatrix}
\begin{bmatrix}
10\\
-1\\
6\\
11
\end{bmatrix}
$$

Perkalian baris-kolom:

### Baris 1

$$
-2(10)+1(-1)+3(6)+1(11)
=8
$$

### Baris 2

$$
8(10)-3(-1)-4(6)-1(11)
=48
$$

### Baris 3

$$
10(10)-2(-1)-8(6)+1(11)
=65
$$

### Baris 4

$$
-17(10)+4(-1)+10(6)+1(11)
=-103
$$

Sehingga

$$
X
=
\frac1{13}
\begin{bmatrix}
8\\
48\\
65\\
-103
\end{bmatrix}
$$

$$
X=
\begin{bmatrix}
\frac{8}{13}\\
\frac{48}{13}\\
5\\
-\frac{103}{13}
\end{bmatrix}
$$

---

# Kesimpulan

Determinan matriks:

$$
\boxed{\det(A)=13}
$$

Invers matriks:

$$
\boxed{
A^{-1}
=
\frac1{13}
\begin{bmatrix}
-2&1&3&1\\
8&-3&-4&-1\\
10&-2&-8&1\\
-17&4&10&1
\end{bmatrix}
}
$$

Solusi sistem persamaan linear:

$$
\boxed{
X=
\begin{bmatrix}
\dfrac{8}{13}\\
\dfrac{48}{13}\\
5\\
-\dfrac{103}{13}
\end{bmatrix}
}
$$

dengan

$$
x_1=\frac{8}{13},\quad
x_2=\frac{48}{13},\quad
x_3=5,\quad
x_4=-\frac{103}{13}
$$