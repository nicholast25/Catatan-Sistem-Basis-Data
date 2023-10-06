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
- Foreign Key (FK): sekumpulan atribur yang digunakan untuk menghubungkan data dari dua tabel.
... (dan seterusnya untuk sub-topik lainnya di Minggu 1)

---

(_Template di atas dapat diulangi untuk minggu-minggu berikutnya dengan topik dan sub-topik yang relevan._)

---
