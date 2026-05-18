# tugas kal
A. Hitunglah determinan matrik berikut dengan menggunakan rumus expansi baris

\sum_{k=1}^n (-1)^{i+k} a_{ik} M_{ik}

 dengan M_{ij} adalah minior dari matrik A dan

M_{ij} = \det A_{ij}.


 A_{ij} adalah submatrik dengan menghapus baris i dan kolom kolom j dari matrix A_{mxn} dengan 1 \le i, j \le n


#1. 
A = \begin{bmatrix} -7 & -5 \\ 1 & 4 \end{bmatrix}

#2.
A = \begin{bmatrix} 0 & 2 & -3 \\ 1 & -2 & -1 \\ 0 & 0 & 1 \end{bmatrix}

#3.
A = \begin{bmatrix} 1 & -3 & 1 & 1 \\ -3 & 1 & 1 & 1 \\ 1 & 1 & -3 & 1 \\ 1 & 1 & 1 & -3 \end{bmatrix}.


#B. Gunakan rumus matriks adjoin untuk menghitung invers dari matriks berikut dengan rumus

(\operatorname{adj} A)_{ij} = (-1)^{i+j} M_{ji}

#dan 

A^{-1} = \frac{1}{\det A} \operatorname{adj} A.

#4.
A = \begin{bmatrix} -7 & -5 \\ 1 & 4 \end{bmatrix}

#5.
A = \begin{bmatrix} 0 & 2 & -3 \\ 1 & -2 & -1 \\ 0 & 0 & 1 \end{bmatrix}

#6.
A = \begin{bmatrix} 1 & -3 & 1 & 1 \\ -3 & 1 & 1 & 1 \\ 1 & 1 & -3 & 1 \\ 1 & 1 & 1 & -3 \end{bmatrix}.


# Evaluasi Determinan dan Invers Matriks

Penjelasan berikut berisi langkah-langkah sistematis untuk menyelesaikan operasi determinan menggunakan ekspansi baris dan pencarian invers menggunakan matriks adjoin.

---

## A. Menghitung Determinan dengan Rumus Ekspansi Baris

Rumus umum ekspansi baris (menggunakan baris pertama, $i = 1$):
$$\det(A) = \sum_{k=1}^{n} (-1)^{1+k} a_{1k} M_{1k}$$

### 1. Matriks 2x2
$$A = \begin{bmatrix} -7 & -5 \\ 1 & 4 \end{bmatrix}$$

**Proses:**
Kita lakukan ekspansi pada baris pertama ($i=1$):
* $a_{11} = -7$, minor $M_{11}$ diperoleh dengan menutup baris 1 & kolom 1 $\implies M_{11} = \det([4]) = 4$
* $a_{12} = -5$, minor $M_{12}$ diperoleh dengan menutup baris 1 & kolom 2 $\implies M_{12} = \det([1]) = 1$

**Perhitungan:**
$$\begin{aligned} \det(A) &= (-1)^{1+1} a_{11} M_{11} + (-1)^{1+2} a_{12} M_{12} \\ &= (1)(-7)(4) + (-1)(-5)(1) \\ &= -28 + 5 \\ &= \mathbf{-23} \end{aligned}$$

---

### 2. Matriks 3x3
$$A = \begin{bmatrix} 0 & 2 & -3 \\ 1 & -2 & -1 \\ 0 & 0 & 1 \end{bmatrix}$$

**Proses:**
Melakukan ekspansi pada baris pertama ($i=1$):
* $a_{11} = 0 \implies$ Karena koefisien 0, kita tidak perlu menghitung minor $M_{11}$.
* $a_{12} = 2$, minor $M_{12}$ (tutup baris 1, kolom 2):
    $$M_{12} = \det \begin{bmatrix} 1 & -1 \\ 0 & 1 \end{bmatrix} = (1)(1) - (-1)(0) = 1$$
* $a_{13} = -3$, minor $M_{13}$ (tutup baris 1, kolom 3):
    $$M_{13} = \det \begin{bmatrix} 1 & -2 \\ 0 & 0 \end{bmatrix} = (1)(0) - (-2)(0) = 0$$

**Perhitungan:**
$$\begin{aligned} \det(A) &= (1)(0) - (1)(2)(M_{12}) + (1)(-3)(M_{13}) \\ &= 0 - 2(1) - 3(0) \\ &= \mathbf{-2} \end{aligned}$$

---

### 3. Matriks 4x4
$$A = \begin{bmatrix} 1 & -3 & 1 & 1 \\ -3 & 1 & 1 & 1 \\ 1 & 1 & -3 & 1 \\ 1 & 1 & 1 & -3 \end{bmatrix}$$

**Proses (Ekspansi Baris 1):**
Untuk matriks ordo 4x4, mengekstrak minor $M_{1k}$ berarti kita harus menghitung determinan dari submatriks 3x3.

* **Hitung $M_{11}$:** Tutup baris 1, kolom 1.
    $$M_{11} = \det \begin{bmatrix} 1 & 1 & 1 \\ 1 & -3 & 1 \\ 1 & 1 & -3 \end{bmatrix} = 1(9-1) - 1(-3-1) + 1(1-(-3)) = 8 + 4 + 4 = 16$$

* **Hitung $M_{12}$:** Tutup baris 1, kolom 2.
    $$M_{12} = \det \begin{bmatrix} -3 & 1 & 1 \\ 1 & -3 & 1 \\ 1 & 1 & -3 \end{bmatrix} = -3(9-1) - 1(-3-1) + 1(1-(-3)) = -24 + 4 + 4 = -16$$

* **Hitung $M_{13}$:** Tutup baris 1, kolom 3.
    $$M_{13} = \det \begin{bmatrix} -3 & 1 & 1 \\ 1 & 1 & 1 \\ 1 & 1 & -3 \end{bmatrix} = -3(-3-1) - 1(-3-1) + 1(1-1) = 12 + 4 + 0 = 16$$

* **Hitung $M_{14}$:** Tutup baris 1, kolom 4.
    $$M_{14} = \det \begin{bmatrix} -3 & 1 & 1 \\ 1 & 1 & -3 \\ 1 & 1 & 1 \end{bmatrix} = -3(1+3) - 1(1+3) + 1(1-1) = -12 - 4 + 0 = -16$$

**Perhitungan Total $\det(A)$:**
$$\begin{aligned} \det(A) &= (1)a_{11}M_{11} - (1)a_{12}M_{12} + (1)a_{13}M_{13} - (1)a_{14}M_{14} \\ &= (1)(1)(16) - (-3)(-16) + (1)(1)(16) - (1)(-16) \\ &= 16 - 48 + 16 + 16 \\ &= \mathbf{0} \end{aligned}$$

*(Catatan: Total penjumlahan setiap baris pada matriks ini bernilai 0, yang membuktikan secara langsung bahwa matriks ini singular atau nilai determinannya pasti 0).*

---

## B. Menghitung Invers dengan Rumus Matriks Adjoin

Rumus:
$$(\text{adj } A)_{ij} = (-1)^{i+j} M_{ji}$$
$$A^{-1} = \frac{1}{\det A} \text{adj } A$$

### 4. Invers Matriks 2x2 (Dari soal No. 1)
$$A = \begin{bmatrix} -7 & -5 \\ 1 & 4 \end{bmatrix}, \quad \det(A) = -23$$

**Kofaktor dan Adjoin:**
* $C_{11} = M_{11} = 4$
* $C_{12} = -M_{12} = -1$
* $C_{21} = -M_{21} = -(-5) = 5$
* $C_{22} = M_{22} = -7$

Matriks Kofaktor $C = \begin{bmatrix} 4 & -1 \\ 5 & -7 \end{bmatrix}$. Matriks Adjoin adalah transpose dari Kofaktor ($C^T$):
$$\text{adj } A = \begin{bmatrix} 4 & 5 \\ -1 & -7 \end{bmatrix}$$

**Invers:**
$$A^{-1} = -\frac{1}{23} \begin{bmatrix} 4 & 5 \\ -1 & -7 \end{bmatrix} = \mathbf{\begin{bmatrix} -4/23 & -5/23 \\ 1/23 & 7/23 \end{bmatrix}}$$

---

### 5. Invers Matriks 3x3 (Dari soal No. 2)
$$A = \begin{bmatrix} 0 & 2 & -3 \\ 1 & -2 & -1 \\ 0 & 0 & 1 \end{bmatrix}, \quad \det(A) = -2$$

**Mencari Matriks Kofaktor ($C_{ij} = (-1)^{i+j} M_{ij}$):**
* $C_{11} = +(-2 - 0) = -2$
* $C_{12} = -(1 - 0) = -1$
* $C_{13} = +(0 - 0) = 0$
* $C_{21} = -(2 - 0) = -2$
* $C_{22} = +(0 - 0) = 0$
* $C_{23} = -(0 - 0) = 0$
* $C_{31} = +(-2 - 6) = -8$
* $C_{32} = -(0 - (-3)) = -3$
* $C_{33} = +(0 - 2) = -2$

Matriks Kofaktor $C = \begin{bmatrix} -2 & -1 & 0 \\ -2 & 0 & 0 \\ -8 & -3 & -2 \end{bmatrix}$. 

**Adjoin ($C^T$):**
$$\text{adj } A = \begin{bmatrix} -2 & -2 & -8 \\ -1 & 0 & -3 \\ 0 & 0 & -2 \end{bmatrix}$$

**Invers:**
$$A^{-1} = \frac{1}{-2} \begin{bmatrix} -2 & -2 & -8 \\ -1 & 0 & -3 \\ 0 & 0 & -2 \end{bmatrix} = \mathbf{\begin{bmatrix} 1 & 1 & 4 \\ 1/2 & 0 & 3/2 \\ 0 & 0 & 1 \end{bmatrix}}$$

---

### 6. Invers Matriks 4x4 (Dari soal No. 3)
$$A = \begin{bmatrix} 1 & -3 & 1 & 1 \\ -3 & 1 & 1 & 1 \\ 1 & 1 & -3 & 1 \\ 1 & 1 & 1 & -3 \end{bmatrix}$$

Berdasarkan perhitungan pada bagian A.3, kita telah membuktikan bahwa:
$$\det(A) = 0$$

**Kesimpulan:**
Syarat utama sebuah matriks memiliki invers adalah determinannya tidak boleh bernilai nol ($\det(A) \neq 0$). Karena determinan matriks ini adalah 0 (matriks singular), maka rumus $A^{-1} = \frac{1}{0} \text{adj } A$ tidak dapat didefinisikan secara matematis.

Maka, **Matriks ini tidak memiliki invers.**