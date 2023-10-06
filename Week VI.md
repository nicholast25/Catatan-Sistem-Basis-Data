## 📘 My Personal Notes

### 🗓️ Week 6: Intermediate to SQL- Part II

#### 📍 Integrity Constraints
- Melindungi kerusakan database secara tidak disengaja dengan memastikan pengguna akses pengganti database tidak menyebabkan kehilangan konsistensi data, seperti gaji harus minimal diatas UMR, umur harus positif, dan sebagainya.
- Constraints on single relations:
  * Not NULL
      - Contoh: mengatur _name_ dan _budget_ supaya tidak kosong.
        ```sql
        name varchar(20) not null
        budget numeric(12,2) not null
        ```
        <br/>
  * UNIQUE (A1,A2...,An)
      - A1,A2,...,An membentuk candidate key yang boleh NULL (sebaliknya dengan primary key).

  * PRIMARY KEY
  * CHECK (P), _P is predicate_
      - P harus memenuhi oleh setiap tuple dalam relasi, seperti memastikan setiap semester itu diantara Fall, Spring, atau Winter.

#### 📍 Referential Integrity
- Memastikan bahwa nilai yang muncul di satu relasi untuk sekumpulan atribut tertentu juga muncul untuk sekumpulan atribut di relasi lain. Misalnya, Jika "Udin" adalah penulis yang ada di tuple pada relasi _buku_, maka terdapat tuple dalam relasi _author_ untuk "Udin".
- Foreign key dapat ditentukan sebagai bagian dari pembuatan tabel dari SQL:
    ```sql
    foreign key(Author_ID) references author
    ```
- SQL memungkinkan daftar atribut dari relasi yang direferensikan ditentukan secara eksplisit
    ```sql
    foreign key(Author_ID) references author (Author_ID)
    ```
- Ketika _referential-integrity constraint_ dilanggar, prosedur umumnya adalah menolak tindakan penyebab pelanggaran itu.
- **ON DELETE CASCADE** atau **ON DELETE SET NULL**, ketika baris dari tabel "induk" dihapus, maka semua baris yang relevan (yang memiliki foreign key yang merujuk pada baris tersebut) juga terhapus. Contoh: Jika kita menghapus "Udin" dari tabel _author_ dan foreign key dalam tabel _buku_ memiliki ON DELETE CASCADE.

#### 📍 Check Conditions
-  ```sql
   CREATE TABLE Books (
   Book_ID INT,
   Book_Title VARCHAR(255)
     CHECK (LENGTH(Book_Title)>=3),
   Author_ID INT
   );
   ```
- Jika ingin memasukkan judul buku kurang dari 3 karakter, maka data itu tidak bisa dimasukkan.

#### 📍 Assertion
   ```sql
   CREATE TABLE Authorss (
   CHECK (
SELECT AVG(Salary)
FROM Authors
WHERE Salary IS NOT NULL
   )<70000;
   );
   ```

Jika update data seperti berikut ini:
   ```sql
UPDATE Authors
SET Salary = 75000
WHERE Author_Name='Udin';
   ```

Maka, data tidak akan terupdate.

#### 📍 Create Index
- CREATE INDEX <index_name> ON <relation_name> (attribute_name);
- Misal:
   ```sql
  CREATE INDEX studentID_index ON student(ID);
  SELECT * FROM student WHERE ID = '12345';
   ```
Output: <br/>
![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/25b491db-e9d4-4b76-81c6-3f8c39bd4b67)


#### 📍 Authorization
- Authorization merupakan hak/akses yang bisa dimiliki user tertentu untuk melakukan beberapa hal pada database, seperti read (membaca), insert (menambahkan data baru), update (modif data tanpa didelete), serta delete. Adapun hak untuk modifikasi skema database, yaitu index (membuat dan menghapus indeks), resource (membuat relasi baru), alertation (menambah dan menghapus attribut dalam relasi), serta drop (menghapus relasi)
- Grant statment digunakan untuk memberi authorization atau akses
   ```sql
   Grant <privilege list> on <relation or view> to <user list>
   ```
<user list> bisa berupa user-id, public, atau role (untuk membedakan dari user” lain
- Revoke statment digunakan untuk mencabut authorization atau akses
  ```sql
  Revoke <privilege list> on <relation or view> from <user list>
   ```




  
