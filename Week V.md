## 📘 My Personal Notes

### 🗓️ Week 5: Intermediate to SQL- Part 1

#### 📍 Join Expression: 
- Mengambil 2 relasi dan mengembalikan sebagai hasil dari relasi lain. Terdiri dari 3 jenis:
  * **Natural Join**: menggabungkan kedua tabel berdasarkan kesamaan nama atribut dan tipe 
data, sehingga menghasilkan atau menampilkan semua atribut dari kedua tabel, tapi 
kolom yang sama hanya ditampilkan sekali. Hasilnya menampikan baris-baris data 
berdasarkan kesamaan kolom. Contohnya:<br/>

Tabel _Genre_
|Buku|Genre| 
|---|---|
|Harry Potter|Fiction|
|Si Juki|Comic|
|Chicken Soup|Novel|
<br/>

Tabel _Data_KodeBuku_
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
<br/>

 * **Inner join**: mengabungkan kedua tabel yang secara eksplist ditentukan oleh
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

* **Outer Join**: Melibatkan baris yang tidak sesuai dari satu atau kedua tabel yang digabungkan untuk meminalisir kehilangan informasi. Outer join terdiri dari:
  
    * Left Join: ketika ingin mendapatkan semua baris dari tabel kiri dan mencocokan dengan tabel di sebelah kanan, apabila tidak ada kecocokan, maka muncul value NULL di kolom dari atribut tabel kanan. Contoh:

_employee_<br/>
      ![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/97129f82-0ab9-40a8-8318-e876c7f19eb8)
<br/>

_department_<br/>
![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/201d648a-f214-458b-871f-932dc0dd0d82)
<br/>

Query Left Join:
```sql
Select empid, ename, deptid, deptname 
from employee 
left outer join department 
on employee.empdept = department.deptname; 
```

Output: <br/>
![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/6752c843-75bc-4086-bbc1-87dc526fa593)
<br/>

          
* Right Join: digunakan ketika kita ingin mendapatkan semua baris dari tabel kanan dan mencocokan tabel tersebut dengan tabel di sebelah kiri, apabila tidak ada kecocokan, maka muncuk value NULL dari atribut tabel kiri. Contoh: <br/>


```sql
Select empid, ename, deptid, deptname 
from employee 
right outer join department 
on employee.empdept = department.deptname; 
```

Output:<br/>
![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/5379e90d-062a-4670-bd99-ccf6fa785091)
<br/>
          
           
 * Full Join: digunakan ketika kita ingin mendapatkan semua baris ketika ada kecocokan atau kesamaan antara baris kiri atau baris kanan, serta mengembalikan NULL setiap kolom dari kedua tabel yang tidak ada kecocokan. Contoh: 

```sql
Select empid, ename, deptid, deptname 
from employee 
full outer join department 
on employee.empdept = department.deptname;
```

Output:<br/>
![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/d3e5963e-5d2b-403c-a1bc-9af6909bf4c7)
<br/>
<br/>

#### 📍 Views: 
- View digunakan untuk membuat atau mensimplify query expression menjadi suatu nama view. Ketika view ini sudah dibuat, kita bisa gunakan untuk query lain untuk menjalankan programya. Contoh pengunaanya:
```sql
CREATE VIEW [Brazil Customers] AS
SELECT CustomerName, ContactName
FROM Customers
WHERE Country = 'Brazil';

SELECT * FROM [Brazil Customers];
```

 Output: <br/>
 ![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/caafe665-7670-4082-8b85-83af449835ff)
<br/>
 - Adapun pengunaan view dapat diexpand atau dikembangkan menjadi contoh berikut :
```sql
create view physics_fall_2017_watson as
 select course_id, room_number
 from (select course.course_id, building, room_number
 	from course, section
 where course.course_id = section.course_id
 	and course.dept_name = 'Physics'
 	and section.semester = 'Fall'
 	and section.year = '2017')
 where building= 'Watson’
```

- Artinya membuat nama view physics_fall_2017_watson berisi query atau perintah untuk memilih atribut course_id, room_number dari tabel yang diolah dari dalam bracket from, yang mana nama gedungnya Watson. Bracket from tersebut menampilkan atribut course.course_id, building, room_number (berdasarkan tabel course dan section) dari kelas Physics ketika Fall 2017.

- View tersebut dapat diupdate atau diperbaharui dengan memasukkan tuple baru ke dalam tabel yang dibuat pada suatu view. Contoh:  insert into faculty values ('30765', 'Green', 'Music');

<br/>

  
#### 📍 Benefits of Using Views: 
- Menggunakan views memampukan pemogram untuk memperpendek syntax tanpa mengetik queries berulang kali, dan juga membantu pemogram lain untuk membaca atau memahami kode tersebut. Dari segi security, views mampu seleksi data yang ingin ditampilkan dari beberapa users sehingga tidak semua users dapat melihat kolom dan baris tertentu. Dari segi Mantainability, view memampukan pemogram untuk update database di satu tempat.

#### 📍 Limitation of Using Views: 
- Kelemahan dari pemggunaan views adalah ketika terdapat dataset yang besar dan kalkulasi yang kompleks, maka views memperlambat SQL queries dan menghambat performa. Selain itu, views membuat queries SQL, tertutama dataset yang kompleks, semakin sulit dipahami. Adapun keterbatasan dalam mengupdate views pada scenario tertentu. View juga membutuhkan storage yang lebih (disk space) untuk menyimpan data materialized.

