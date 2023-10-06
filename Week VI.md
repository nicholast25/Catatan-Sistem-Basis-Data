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
        
