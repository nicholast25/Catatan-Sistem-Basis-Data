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
   
        