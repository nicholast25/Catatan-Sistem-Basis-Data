## 📘 My Personal Notes

### 🗓️ Week 1: Introduction to Database (DB)

#### 📍 Relation Schema and Instance
- A1,A2,...,An adalah atribut
- R = (A1, A2,...,An) adalah skema relasi, misalnya: _instructor_ = (_ID,name, dept_name, salary_)
- _Relation instance_ adalah sekumpulan tuples atau baris spesifik untuk relasi skema tertentu pada titik waktu tertentu.
Dinotasikan sebagai r(R), r adalah _specific instance_ dan R adalah _relation schema_. Nilai-nilai dari relasi ditentukan oleh tabel.
Contoh: <br/><br/><br/>
  |ID|name|dept_name|salary|
  |---|---|----|----|
  |2222|Einstein|Physics|95000|
  |98123|Kim|Finance|100000|
  |23231|Mat| History|84000|
<br/>

Baris pertama merupakan atribut (nama-nama yang ada di kolom), sedangkan isi baris berupa data-data merupakan tuples.
Setiap atribut dalam relasi memiliki **domain** untuk menentukan **validasi** data. Nilai atribut harus tidak terpisahkan (_atomic_).
Tuples dapat disimpan tanpa urutan.

<br/>

#### 📍 Database Schema
-DB Schema adalah struktur logika dari database.
-DB instance adalah cuplikan dari data dalam database pada waktu yang diberikan.
-Contoh:
  * Schema: _instructor (ID,name,dept_name,salary)_
  * Instance: berupa tabel data yang ditampilkan.

#### 📍 Keys
- Superkey (SK): sekumpulan satu atau lebih atribut untuk mengidentifikasi (membedakan) tuples dalam relasi. Contohnya (_ID_) dan (_ID,name_) bisa mengidentifikasi pengajar.
- Candidate Key (CK): minimal superkey, dalam arti atribut yang wajib dibutuhkan untuk identifikasi. Contohnya ID.
- Primary Key (PK): dari Candidate Key, salah satunya dijadikan PK.
- Foreign Key (FK): sekumpulan atribur yang digunakan untuk menghubungkan data dari dua tabel. Misalnya _dept_name_ pada tabel diatas (contoh paling awal) adalah FK yang menghubungkan relasi departemen.
- Contoh Tabel:
<br/><br/>
  |ID_Class|name|dept_name|salary|
  |---|---|----|----|
  |22222|Einstein|Physics|95000|
  |98123|Kim|Finance|100000|
  |23231|Mat|History|84000|
  |23121|Luke|History|84000|
  |98231|Mat|Finance|84000|
<br/>
-schema  : instructor(ID_Class, name, dept_name, salary)<br/>
-PK      : ID, karena departemen, dan gaji bisa saja sama, serta bisa ada satu pengajar dalam dua departemen.
<br/><br/>


#### 📍 The Relational Algebra
- Terdapat Operasi Select, Project, C.Prod, Union, Set Diff, Rename. Untuk detailnya dapat dilihat pada gambar berikut: 
![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/29c7e156-7877-4dab-9cf5-f61b5b575c31)
<br/><br/>

- Contoh **Select** And **Project**:
![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/988e58ad-6812-44c5-99e8-d293e214045c)

Query Select : σ dept name =“Physics” (instructor)
Query Project: Π ID, name, salary (instructor)



