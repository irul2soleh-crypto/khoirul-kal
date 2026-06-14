# Implementasi Singular Value Decomposition (SVD) pada Kompresi Citra (9)

## Link Colab:
https://colab.research.google.com/drive/1u99d2P9le_8ek_06VurWkYCNBUruZ92i?usp=sharing

## Hasil Output Program

Pada program:

```python
U, S, Vt = np.linalg.svd(gambar_asli, full_matrices=False)
```

diperoleh output:

```text
Ukuran Matriks U  : (168, 168)
Ukuran Vektor S   : (168,)
Ukuran Matriks Vt : (168, 300)
```

Artinya sistem berhasil memecah gambar menjadi tiga komponen utama menggunakan metode Singular Value Decomposition (SVD).

Tujuan utama SVD pada citra adalah:

- memisahkan pola penting gambar,
- mengurangi ukuran data,
- mempertahankan kualitas visual gambar.

---

## 1. Menentukan Matriks Awal Gambar A

Saat gambar dibaca:

```python
gambar = Image.open(nama_file)
```

gambar masih berupa citra RGB.

Kemudian gambar diubah ukurannya menjadi:

```python
gambar = gambar.resize((300, 168))
```

Artinya:

```text
Lebar  = 300 piksel
Tinggi = 168 piksel
```

Setelah itu dilakukan konversi grayscale:

```python
gambar_gray = np.mean(gambar[:, :, :3], axis=2)
```

### Penjelasan

Proses grayscale dilakukan agar:

- gambar hanya memiliki 1 kanal warna,
- perhitungan matematika menjadi lebih sederhana,
- proses SVD menjadi lebih cepat.

Pada grayscale:

```text
0   = hitam
255 = putih
```

Setelah proses ini, gambar berubah menjadi matriks numerik.

Karena hasil ukuran gambar:

```text
168 × 300
```

maka matriks gambar:

```math
A_{168 \times 300}
```

Artinya:

- 168 baris piksel
- 300 kolom piksel

Jumlah total piksel:

```math
168 \times 300 = 50400
```

Jadi gambar direpresentasikan sebagai:

```text
50.400 nilai intensitas piksel grayscale
```

Contoh sederhana matriks gambar:

```text
A =
[120 130 140]
[100 110 125]
[ 90 100 105]
```

Setiap angka menunjukkan tingkat terang suatu piksel.

---

## 2. Tujuan Dilakukan SVD

Metode SVD memecah matriks gambar:

```math
A = U\Sigma V^T
```

menjadi tiga bagian utama.

### Penjelasan Komponen

| Matriks | Fungsi |
|---|---|
| U | menyimpan pola vertikal gambar |
| Σ | menyimpan energi/informasi penting |
| Vᵀ | menyimpan pola horizontal gambar |

Secara sederhana:

- U = arah fitur gambar
- Σ = tingkat kepentingan fitur
- Vᵀ = kombinasi pola pembentuk gambar

Dengan memecah gambar menjadi bagian-bagian ini, sistem dapat mengetahui:

- fitur penting,
- fitur kurang penting,
- bagian yang bisa dibuang saat kompresi.

---

## 3. Mencari Matriks AAᵀ

Langkah pertama dalam proses SVD adalah menghitung:

```math
AA^T
```

Pada program:

```python
AAT = gambar_asli @ gambar_asli.T
```

### Penjelasan

Transpose `(T)` berarti:

- baris menjadi kolom,
- kolom menjadi baris.

Karena ukuran gambar:

```text
A = (168 × 300)
```

maka:

```math
(168 \times 300)(300 \times 168) = 168 \times 168
```

hasil:

```text
AAᵀ = (168 × 168)
```

### Mengapa Harus Menghitung AAᵀ?

Karena:

- eigenvector dari AAᵀ digunakan membentuk matriks U,
- eigenvalue dari AAᵀ digunakan mencari singular value.

AAᵀ dipakai untuk mengetahui:

- pola dominan,
- arah variasi terbesar,
- struktur utama gambar.

---

## 4. Mencari Eigenvalue dan Eigenvector

Setelah mendapatkan AAᵀ, langkah berikutnya adalah mencari:

- eigenvalue
- eigenvector

Secara matematis:

```math
(AA^T)x = \lambda x
```

dengan:

- λ = eigenvalue
- x = eigenvector

Untuk mencari eigenvalue digunakan persamaan karakteristik:

```math
\det(AA^T - \lambda I)=0
```

Pada Python:

```python
eigenvalue, eigenvector = np.linalg.eig(AAT)
```

### Penjelasan Eigenvalue

Eigenvalue menunjukkan:

- seberapa besar pengaruh suatu fitur pada gambar.

Nilai besar:

- fitur sangat penting.

Nilai kecil:

- fitur kurang penting atau noise.

### Penjelasan Eigenvector

Eigenvector menunjukkan:

- arah pola utama pada gambar.

Misalnya:

- pola wajah,
- pencahayaan,
- kontur objek,
- bentuk struktur gambar.

---

## 5. Mendapatkan Singular Value

Singular value diperoleh dari akar eigenvalue:

```math
\sigma_i = \sqrt{\lambda_i}
```

Pada program sebenarnya proses ini dihitung otomatis oleh:

```python
np.linalg.svd()
```

Makanya muncul:

```text
Ukuran Vektor S : (168,)
```

Artinya:

```text
Terdapat 168 singular value
```

### Penjelasan Singular Value

Singular value adalah:

- ukuran kekuatan informasi suatu komponen gambar.

Nilai singular terbesar:

- menyimpan struktur utama gambar.

Nilai singular kecil:

- biasanya hanya detail kecil atau noise.

Karena itu:

- beberapa singular value pertama saja sudah cukup membentuk gambar.

---

## 6. Membentuk Matriks U

Eigenvector dari:

```math
AA^T
```

dikumpulkan menjadi:

```math
U = [u_1 \ u_2 \ u_3 \ ... \ u_{168}]
```

Ukurannya:

```text
U = (168 × 168)
```

### Penjelasan Matriks U

Matriks U berisi:

- pola vertikal utama gambar.

Setiap kolom U:

- mewakili satu arah fitur penting.

Karena jumlah piksel vertikal = 168,
maka jumlah vektor pada U juga 168.

---

## 7. Mencari Matriks AᵀA

Langkah berikutnya:

```python
ATA = gambar_asli.T @ gambar_asli
```

Secara matematis:

```math
A^TA
```

### Penjelasan

AᵀA digunakan untuk:

- mencari pola horizontal gambar.

Karena:

```text
Aᵀ = (300 × 168)
A  = (168 × 300)
```

maka:

```math
(300 \times 168)(168 \times 300) = 300 \times 300
```

hasil:

```text
AᵀA = (300 × 300)
```

---

## 8. Membentuk Matriks Vᵀ

Eigenvector dari:

```math
A^TA
```

membentuk matriks:

```text
V
```

kemudian ditranspose menjadi:

```math
V^T
```

Pada full SVD sebenarnya ukuran:

```text
Vᵀ = (300 × 300)
```

Namun karena program menggunakan:

```python
full_matrices=False
```

maka NumPy menggunakan thin SVD sehingga hanya singular vector penting yang disimpan.

Karena:

```math
\min(168,300)=168
```

maka ukuran akhirnya menjadi:

```text
Vᵀ = (168 × 300)
```

### Penjelasan Matriks Vᵀ

Vᵀ menyimpan:

- pola horizontal gambar.

Jika U membaca pola vertikal,
maka Vᵀ membaca:

- pola mendatar,
- struktur horizontal,
- kombinasi fitur antar kolom piksel.

Tujuan thin SVD:

- komputasi lebih cepat,
- memori lebih hemat,
- hanya komponen penting yang disimpan.

---

## 9. Membentuk Matriks Sigma Σ

Vector singular:

```text
S = [σ₁, σ₂, σ₃, ..., σ₁₆₈]
```

diubah menjadi matriks diagonal:

```python
Sigma = np.diag(S)
```

Menjadi:

```math
\Sigma =
\begin{bmatrix}
\sigma_1 & 0 & 0 \\
0 & \sigma_2 & 0 \\
0 & 0 & \sigma_3
\end{bmatrix}
```

*(contoh sederhana matriks diagonal)*

Ukuran sebenarnya:

```text
Σ = (168 × 168)
```

### Penjelasan Sigma

Sigma menunjukkan:

- tingkat kepentingan tiap fitur gambar.

Semakin besar nilai sigma:

- semakin penting fitur tersebut.

Karena hanya diagonal yang berisi angka:

- tiap fitur berdiri sendiri,
- tidak saling bercampur.

---

## 10. Rekonstruksi Gambar

Pada dekomposisi penuh:

```math
A = U\Sigma V^T
```

Sedangkan pada proses kompresi digunakan:

```math
A_k = U_k\Sigma_kV_k^T
```

Pada program:

```python
gambar_rekonstruksi = U_k @ S_k @ Vt_k
```

### Penjelasan

Rekonstruksi berarti:

- membangun kembali gambar dari hasil SVD.

Tetapi:

- tidak semua komponen dipakai,
- hanya komponen paling penting saja.

Karena itu:

- ukuran data menjadi lebih kecil,
- gambar masih terlihat mirip dengan gambar asli.

---

## 11. Penjelasan Nilai k

Pada program:

```python
pilihan_k = [2, 10, 30, 60, 90]
```

### Penjelasan

k menunjukkan:

- jumlah singular value yang dipakai.

| k | Makna |
|---|---|
| 2 | hanya fitur utama |
| 10 | detail mulai muncul |
| 30 | gambar mulai jelas |
| 60 | hampir menyerupai asli |
| 90 | kualitas semakin mendekati gambar asli |

Semakin besar k:

- kualitas semakin baik,
- ukuran penyimpanan semakin besar.

---

## 12. Mengapa Gambar Tetap Mirip Setelah Dikompresi?

Karena singular value terbesar menyimpan sebagian besar informasi gambar.

Pada grafik:

```python
plt.plot(S)
```

biasanya:

- nilai awal sangat besar,
- lalu turun drastis.

Artinya:

- sebagian besar informasi penting hanya berada pada beberapa komponen awal.

Komponen akhir:

- hanya detail kecil,
- bahkan sering berupa noise.

---

## 13. Alur Lengkap Proses SVD pada Program

### STEP 1
Baca gambar grayscale:

```text
A (168 × 300)
```

↓

### STEP 2
Hitung:

```math
AA^T
```

untuk mencari pola vertikal.

↓

### STEP 3
Cari:

- eigenvalue
- eigenvector

↓

### STEP 4
Bentuk:

```text
U (168 × 168)
```

↓

### STEP 5
Hitung:

```math
A^TA
```

untuk mencari pola horizontal.

↓

### STEP 6
Cari eigenvector.

↓

### STEP 7
Bentuk:

```text
Vᵀ (168 × 300)
```

↓

### STEP 8
Hitung singular value:

```math
\sigma_i = \sqrt{\lambda_i}
```

↓

### STEP 9
Bentuk:

```text
Σ (168 × 168)
```

↓

### STEP 10
Rekonstruksi:

```math
A_k = U_k\Sigma_kV_k^T
```

untuk menghasilkan kembali gambar hasil kompresi.

---

## Kesimpulan

Metode Singular Value Decomposition (SVD) dapat digunakan untuk melakukan kompresi citra dengan cara memecah gambar menjadi tiga komponen utama:

- matriks U,
- matriks Σ,
- matriks Vᵀ.

Melalui proses ini, sistem dapat menyimpan hanya komponen paling penting dari gambar sehingga ukuran data menjadi lebih kecil tanpa menghilangkan bentuk utama citra secara signifikan.

Semakin besar nilai \(k\) yang digunakan:

- kualitas gambar semakin baik,
- tetapi ukuran penyimpanan juga semakin besar.

Sebaliknya, semakin kecil nilai \(k\):

- kompresi semakin tinggi,
- namun detail gambar semakin berkurang.

Dengan demikian, SVD menjadi salah satu metode efektif dalam pengolahan citra digital untuk:

- kompresi gambar,
- reduksi dimensi,
- dan ekstraksi fitur penting dari citra.