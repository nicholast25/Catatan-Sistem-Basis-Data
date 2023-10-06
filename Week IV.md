## 📘 My Personal Notes

### 🗓️ Week 1: Introduction to SQL- Part II

#### 📍 Aggregate Function
- Untuk menghitung pada sekumpulan baris yang memberikan suatu hasil, umumnya untuk menyimpulkan dan menganalisa data.
- Fungsi terdiri dari: avg, min, max, sum, count.
- Contoh average (avg):<br/>
Mencari rata-rata gaji dari pengajar departemen Computer Science

  ```sql
  select avg(salary)
  from instructor
  where dept_name = 'Comp Sci'
  ```
- Contoh count:<br/>
Mencari jumlah pengajar yang mengajar pada waktu Spring 2018

  ```sql
  select count(distinct ID)
  from teaches
  where semester ='Spring' and year=2018;
  ```
- Menampilkan jumlah tuples dari course
  ```sql
  select count(*)
  from course;
  ```
- Mengganti nama kolom/ attribut

  ```sql
  select count(distinct ID) as spring18_instructor
  from teaches
  where semester ='Spring' and year=2018;
  ```
 <br/>

- **Group By**: Untuk mengelompokkan tuple-tuple yang memiliki value tertentu yang sama.
     * Contoh: Mencari rata-rata gaji dari setiap departemen (kesamaan departemen)
    ```sql
    select dept_name, avg (salary) as avg_salary
    from instructor
    group by dept_name;
  ```
  <br/>

- **Having**: Digunakan setelah ada klausa **group by** untuk memberikan syarat.
     * Contoh: Menampilkan data  rata-rata gaji berdasarkan departemen, yang lebih besar dari 42000
    ```sql
  select dept name, avg (salary) as avg_salary
  from instructor
  group by dept name
  having avg (salary) > 42000;
  ```
  <br/>  <br/>

 
#### 📍 Set Membership
- **in** : menghubungkan dengan himpunan keanggotaan.

   * Contoh: Memilih kelas yang diajarkan pada Fall 2017 dan juga ada di Spring 2018
```sql
select distinct course_id
from section
where semester = 'Fall' and year= 2017 and
course id in (select course_id
from section
where semester = 'Spring' and year= 2018);
```
<br/>

- **not in**: tidak ada ikatan dengan himpunan keanggotaan.

     * Contoh: Memilih kelas yang diajarkan pada Fall 2017, tetapi tidak pada Spring 2018
```sql
  select distinct course_id
  from section
  where semester = 'Fall' and year= 2017 and
  course id not in (select course_id
  from section
  where semester = 'Spring' and year= 2018);
```
<br/>

#### 📍 Set Comparison
- Membandingkan nilai pada kumpulan _values_ dengan nilai lainnya.
- Contoh: Mencari nama pengajar yang memiliki gaji leih besar daripada setidaknya satu dari departemen Biologi.
  ```sql
  select distinct T.name
  from instructor as T, instructor as S
  where T.salary > S.salary and S.dept name = 'Biology';
  ```

#### 📍 Exists Clause 
- **Exist**
     * Mengembalikan nilai _true_ jika argumen pada subquerynya tidak kosong.
     * Contoh: Menampilkan semua departemen yang memiliki minimal satu pengajar yang berhubunan dengan yang lain.
   ```sql
   SELECT dept_name
   FROM department as d
   WHERE EXISTS (SELECT * FROM instructor as i WHERE i.dept_name=d.dept_name);
  ```
- **Not Exists**: pengecualian terhadap subquery dalam argumen setelah _not exists_

    * Contoh: Menampilkan semua ID kelas pada tabel course yang tidak ada di tabel instructor.
   ```sql
   SELECT course_id
   FROM course as c
   WHERE NOT EXISTS (SELECT * FROM teachers t as i WHERE t.course_id=c.course_id);
  ```
<br/>
#### 📍 Subqueries in The Form Clause
- Contoh: Menampilkan data  rata-rata gaji berdasarkan departemen, yang lebih besar dari 42000

   ```sql
   select dept name, avg salary
  from (select dept name, avg (salary) as avg salary
  from instructor
  group by dept name)
  where avg salary > 42000;
  ```
