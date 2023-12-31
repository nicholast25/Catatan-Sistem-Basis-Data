## 📘 My Personal Notes

### 🗓️ Week 1: Introduction to Database (DB)

#### 📍 Definition and Purpose of Database
- Database merupakan sekumupulan data yang terstruktur (seperti buku), sedangkan database management system merupakan perangkat lunak untuk membaca, menulis, dan mengelola data. Database digunakan untuk memastikan data tersimpan secara organisir dan mudah diakses.
- Contohnya adalah database universitas yang terdiri dari kode mata kuliah, nama mata kuliah, dosen pengajar, periode ajaran, dan sebagainya. Aadapun dalam human resource universitas yang menyimpan informasi dosen, departemen, gaji, tax, dan sebagainya.
- Database Management System terdiri dari sekumpulan data yang saling berhubungan, program untuk mengakses data, serta menyediakan sistem yang nyaman dan efisien. Sistem Database juga mengatur data yang terstruktur dan tak terstruktur, serta melibatkan setiap aspek kehidupan. Adapun beberapa masalah dalam DMBS seperti _inconsistency data_, _duplicated data_, _difficulty in accessing data_, hingga masalah keamanan data.
      <br />

#### 📍 View of Data
- Data models: kerangka konseptual yang menentukan struktur, pengelolaan dan alur data dalam sistem.
  * Data: informasi yang akan disimpan ke dalam database.
  * D.Relationship: bagaimana data terhubung dengan data berbeda/ lainnya. Contohnya entity dosen akan terhubung dengan entity data mahasiswa melalui data mata kuliah.  
  * D.Semantic: maksud/arti dari data, misalnya _department_ untuk menunjukkan fakultas.
  * D.Constraints: aturan yang menentukan nilai/ _value_ dari data tersebut, seperti usia mahasiswa tidak boleh negatif.

- Dalam Data model, terdapat _relational_ yang mengelola data ke dalam tabel, seperti MySQL. Adapun _Enttiy-Relationship_ yang digunakan untuk mendesain database, bagaimana entitas berelasi satu dengan yang lain (seperti entitas "Murid" dan "Kelas", yang mana relasi "Enrollment" meninjukkan bahwa siswa terdaftar di dalam kelas). Adapun contoh lainnya berikut:

The instructor table

  |ID|name|dept_name|salary|
  |---|---|----|----|
  |2222|Einstein|Physics|95000|
  |98123|Kim|Finance|100000|
  |23231|Mat| History|84000|
  
The department table

 |dept_name|building|budget|
  |---|---|----|
  |Physics|C|100000|
  |History|B|120000|
  |Finance|A|90000|

 Relasi antara kedua entitas adalah _dept_name_
<br />
<br />
 
- Data abstraction, untuk menyembunyikan kompleksitas dari data untuk menampilkan database melalui tiga level berikut:
    * Physical level: menjelaskan cara data disimpan.
    * Logical level: menjelaskan bahwa data tersimpan dalam database serta relasi antara data.
      <br />
      
      Contoh:      <br />
      **type** instructor = **record**      <br />
             **ID** = string;      <br />
             **name**= string;      <br />
             **dept_name**= string;      <br />
             **salary**= string;      <br />

      end;
      <br />

    * View level: menjelaskan menyembunyikan tipe data secara detail untuk tujuan keamanan data.
      <br />

#### 📍 DB Languages, Design, Architecture, and Users and Administrator
- Data Definition Language: membuat sekumpulan template yang disimpan di dalam _data dictionary_. Dictionary tersebut mengandung **database schema, integrity constraints (primary key), authorization**.

  <br/>Contoh: <br/>
      **create table** instructor = **record**      <br />
             **ID** char(5);      <br />
             **name** varchar(20);      <br />
             **dept_name** varchar(20);      <br />
             **salary** numeric (8,2);      <br />
             end;
      <br />
      <br />

- Data Manipulation Language (DML) atau query language: mengakses dan perbaharui data yang dikelola oleh data model. Terdiri dari dua tipe:
   * Procedural DML (mewajibkan user menentukan data yang diperlukan dan cara mendapatkannya).
   * Declarative DML (mewajibkan user menentukan data tanpa dijelaskan cara mendapatkan datanya).
<br />

- SQL query language digunakan untuk mengatur dan memberi query atau perintah dalam pengelolaan data. Misalkan: <br/>
SELECT name FROM students WHERE grade='A';<br/>
<br/> meminta data nama yang mendapatkan nilai A.
<br/>

- Database Design:
   * Logical Design (Entity, Relationship, Attribute): Rancangan pembuatan database yang membutuhkan entitas (seperti objek Buku), yang setiap entitas memiliki atribut (seperti judul, tahun, ISBN), serta relasi entitas satu dengan yang lain (seperti relasi objek Buku dengan objek Penerbit).
   * Physical Design (Tables and indexes, Storage, Security): Bagaimana data disimpan, diakses, dan diamankan, yang mana data-data sudah diimplementasikan ke nama-nama.

- Data Architecture, Database User and Administrator: Skema dan pengguna-pengguna database dapat dilihat berikut ini: <br/><br/>
![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/cb1a750e-9be5-43df-b98e-0cb8229fce51)
 ![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/aaecc04d-1572-4374-9ff9-6ae3ac6d6df8)

<br/>

 Ada empat jenis pengguna sistem basis data yang berbeda, yaitu naive user, pemrogram, analysts, dan administrator basis data. Naive user adalah pengguna yang kurang berpengalaman dan berinteraksi dengan sistem menggunakan antarmuka pengguna yang telah ditentukan sebelumnya, seperti aplikasi web atau mobile. Peemrograma berperan dalam menulis program aplikasi. Analysts berinteraksi dengan sistem tanpa menulis program dan biasanya menggunakan bahasa kueri basis data atau perangkat lunak analisis data. Administrator database memiliki kontrol sentral terhadap data dan program yang mengakses data tersebut, dan tugasnya meliputi definisi skema, pengaturan struktur penyimpanan, modifikasi skema, pengaturan izin akses data, dan pemeliharaan rutin seperti pencadangan data dan pemantauan kinerja.



