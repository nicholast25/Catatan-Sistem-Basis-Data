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

#### 📍 Set Comparison
- Membandingkan nilai pada kumpulan _values_ dengan nilai lainnya.



#### 📍 Subqueries in The Form Clause
