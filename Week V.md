## 📘 My Personal Notes

### 🗓️ Week 5: Inttermediate to SQL- Part 1

#### 📍 Join Expression: 
- Mengambil 2 relasi dan mengembalikan sebagai hasil dair relasi lain.
- Terdiri dari 3 jenis:
     * Natural Join: menggabungkan kedua tabel berdasarkan kesamaan nama atribut dan tipe 
data, sehingga menghasilkan atau menampilkan semua atribut dari kedua tabel, tapi 
kolom yang sama hanya ditampilkan sekali. Hasilnya menampikan baris-baris data 
berdasarkan kesamaan kolom. Contohnya:

Tabel Genre
|Buku|Genre| 
|---|---|
|Harry Potter|Fiction|
|Si Juki|Comic|
|Chicken Soup|Novel|
<br/>

Tabel Data_KodeBuku
|Buku|Kode Buku| 
|---|---|
|Harry Potter|F-101|
|Si Juki|C-234|
|Chicken Soup|N-222|
<br/>

```sql
SELECT *
FROM Genre NATURAL JOIN Data_KodeBuku;
```
Output:
|Buku|Genre|Kode Buku| 
|---|---|---|
|Harry Potter|Fiction|F-101|
|Si Juki|Comic|C-234|
|Chicken Soup|Novel|N-222|
<br/>

* Inner join: mengabungkan kedua tabel yang secara eksplist ditentukan oleh
hubungan ON (dalam arti kita yang menentukan hubungan atribut dari kedua tabel). Hasil 
tabelnya akan menampilkan semua atribut dari kedua tabel, termasuk kolom yang sama. 
Contohnya:


```sql
SELECT *
FROM Genre INNER JOIN Data_KodeBuku ON Genre.Buku= Data_KodeBuku.Buku;
```
Output:
|Buku|Genre|Buku|Kode Buku| 
|---|---|---|---|
|Harry Potter|Fiction|Harry Potter|F-101|
|Si Juki|Comic|Si Juki|C-234|
|Chicken Soup|Novel|Chicken Soup|N-222|
<br/>


