#  Eigen Value dan Eigen Vektor dengan Dekomposi QR (8)

Link Gogle Colab: https://colab.research.google.com/drive/1ybIvVPNGac31UIK8Mvpz7KhHX4ugH6_D?usp=sharing

Materi ini membahas proses mencari nilai eigen menggunakan metode dekomposisi QR dengan Gram-Schmidt secara bertahap hingga 10 iterasi QR.

Diberikan matriks:

$$
A=
\begin{bmatrix}
2 & 1\\
1 & 2
\end{bmatrix}
$$

---

## Tahap 1 — Menentukan Matriks Awal

Matriks awal:

$$
A_0=
\begin{bmatrix}
2 & 1\\
1 & 2
\end{bmatrix}
$$

Kolom-kolom matriks:

$$
a_1=
\begin{bmatrix}
2\\
1
\end{bmatrix}
,\qquad
a_2=
\begin{bmatrix}
1\\
2
\end{bmatrix}
$$

Metode QR akan memfaktorkan:

$$
A = QR
$$

dengan:

- $Q$ = matriks ortogonal
- $R$ = matriks segitiga atas

---

## Tahap 2 — Membentuk Vektor $q_1$

Norma kolom pertama:

$$
\|a_1\|=\sqrt{2^2+1^2}=\sqrt5
$$

Vektor ortonormal pertama:

$$
q_1=\frac{a_1}{\|a_1\|}
$$

Hasil:

$$
q_1=
\begin{bmatrix}
\dfrac{2}{\sqrt5}\\
\dfrac{1}{\sqrt5}
\end{bmatrix}
$$

---

## Tahap 3 — Menghitung Proyeksi $a_2$

Hitung dot product:

$$
q_1\cdot a_2=
\frac{2}{\sqrt5}(1)+
\frac{1}{\sqrt5}(2)
=
\frac{4}{\sqrt5}
$$

Rumus proyeksi:

$$
\mathrm{proj}_{q_1}(a_2)
=
(q_1\cdot a_2)q_1
$$

Hasil proyeksi:

$$
(q_1\cdot a_2)q_1=
\begin{bmatrix}
\dfrac85\\
\dfrac45
\end{bmatrix}
$$

---

## Tahap 4 — Membentuk Vektor Ortogonal $u_2$

Rumus:

$$
u_2=
a_2-(q_1\cdot a_2)q_1
$$

Perhitungan:

$$
u_2=
\begin{bmatrix}
1\\
2
\end{bmatrix}
-
\begin{bmatrix}
\dfrac85\\
\dfrac45
\end{bmatrix}
=
\begin{bmatrix}
-\dfrac35\\
\dfrac65
\end{bmatrix}
$$

---

## Tahap 5 — Membentuk Vektor $q_2$

Norma:

$$
\|u_2\|=
\sqrt{
\left(-\frac35\right)^2+
\left(\frac65\right)^2
}
=
\frac{3\sqrt5}{5}
$$

Normalisasi:

$$
q_2=
\frac{u_2}{\|u_2\|}
$$

Hasil:

$$
q_2=
\begin{bmatrix}
-\dfrac{\sqrt5}{5}\\
\dfrac{2\sqrt5}{5}
\end{bmatrix}
$$

---

## Tahap 6 — Membentuk Matriks $Q$ dan $R$

Matriks $Q$:

$$
Q=
\begin{bmatrix}
\dfrac{2\sqrt5}{5} & -\dfrac{\sqrt5}{5}\\
\dfrac{\sqrt5}{5} & \dfrac{2\sqrt5}{5}
\end{bmatrix}
$$

Rumus matriks $R$:

$$
R=Q^TA
$$

Hasil:

$$
R=
\begin{bmatrix}
\sqrt5 & \dfrac{4\sqrt5}{5}\\
0 & \dfrac{3\sqrt5}{5}
\end{bmatrix}
$$

---

## Tahap 7 — Verifikasi Dekomposisi QR

Rumus verifikasi:

$$
A=QR
$$

Perkalian:

$$
QR=
\begin{bmatrix}
2 & 1\\
1 & 2
\end{bmatrix}
$$

Hasil sama dengan matriks awal sehingga dekomposisi QR benar.

---

## Tahap 8 — Membentuk Matriks Iterasi Baru

Rumus iterasi QR:

$$
A_{k+1}=R_kQ_k
$$

Iterasi pertama:

$$
A_1=
RQ=
\begin{bmatrix}
\dfrac{14}{5} & \dfrac35\\
\dfrac35 & \dfrac65
\end{bmatrix}
$$

Dalam bentuk desimal:

$$
A_1=
\begin{bmatrix}
2.8 & 0.6\\
0.6 & 1.2
\end{bmatrix}
$$

---

## Tahap 9 — Iterasi QR hingga 10 Kali

Proses QR dilakukan terus menerus:

$$
A_k=Q_kR_k
$$

kemudian:

$$
A_{k+1}=R_kQ_k
$$

Hasil iterasi:

### Iterasi 1

$$
A_1=
\begin{bmatrix}
2.8 & 0.6\\
0.6 & 1.2
\end{bmatrix}
$$

### Iterasi 2

$$
A_2=
\begin{bmatrix}
2.96 & 0.28\\
0.28 & 1.04
\end{bmatrix}
$$

### Iterasi 3

$$
A_3=
\begin{bmatrix}
2.9931 & 0.1108\\
0.1108 & 1.0069
\end{bmatrix}
$$

### Iterasi 4

$$
A_4=
\begin{bmatrix}
2.9985 & 0.0415\\
0.0415 & 1.0015
\end{bmatrix}
$$

### Iterasi 5

$$
A_5=
\begin{bmatrix}
2.9997 & 0.0154\\
0.0154 & 1.0003
\end{bmatrix}
$$

### Iterasi 6

$$
A_6=
\begin{bmatrix}
2.9999 & 0.0057\\
0.0057 & 1.0001
\end{bmatrix}
$$

### Iterasi 7

$$
A_7=
\begin{bmatrix}
3.0000 & 0.0021\\
0.0021 & 1.0000
\end{bmatrix}
$$

### Iterasi 8

$$
A_8=
\begin{bmatrix}
3.0000 & 0.0008\\
0.0008 & 1.0000
\end{bmatrix}
$$

### Iterasi 9

$$
A_9=
\begin{bmatrix}
3.0000 & 0.0003\\
0.0003 & 1.0000
\end{bmatrix}
$$

### Iterasi 10

$$
A_{10}=
\begin{bmatrix}
3.0000 & 0.0001\\
0.0001 & 1.0000
\end{bmatrix}
$$

Terlihat bahwa elemen di luar diagonal semakin mendekati nol.

---

## Tahap 10 — Kesimpulan Nilai Eigen

Setelah 10 iterasi, matriks hampir menjadi diagonal:

$$
A_{10}\approx
\begin{bmatrix}
3 & 0\\
0 & 1
\end{bmatrix}
$$

Maka nilai eigennya adalah:

$$
\lambda_1=3
$$

$$
\lambda_2=1
$$

Nilai eigen tersebut sesuai dengan penyelesaian analitik:

$$
\lambda=2\pm1
$$

Sehingga:

$$
\lambda_1=3,\qquad
\lambda_2=1
$$

Metode QR berhasil menemukan nilai eigen melalui proses iterasi yang terus membuat matriks mendekati bentuk diagonal.