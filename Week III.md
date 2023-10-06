## 📘 My Personal Notes

### 🗓️ Week 3: 

#### 📍 CREATE TABLE
- Contoh: <br/>
```sql
CREATE TABLE department(
dept_name varchar (20) primary key, 
building varchar (15),
budget numeric(12,2) check (budget>0)
);

CREATE TABLE instructor(
ID CHAR (5) primary key,
name VARCHAR(20) NOT NULL,
dept_name VARCHAR(20),
salary NUMERIC (8,2),
FOREIGN KEY(dept_name) REFERENCES department(dept_name)
);
```
#### 📍 Memeriksa Entities
- Contoh: <br/>
```sql
use university;
describe course;
```
Output:<br/>
![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/88e3b4f9-7a5a-4e04-b7b9-1e26b4de5d11)

<br/>

#### 📍 SELECT, FROM, WHERE
- Contoh 1:  untuk mencari semua nama pengajar dan course_id, pilih atribut nama dan course_id dari tabel instructor dan teaches, yang mana relasinya berdasarkan kesamaan ID antara tabel instructor dan teaches.

```sql
SELECT name, course_id FROM instructor, teaches
WHERE instructur.ID=teaches.ID;
```
Output: <br/>
![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/6df9cb09-2d45-4b38-a24f-22864f920357)

<br/>

- Contoh 2: untuk mencari semua pengajar Comp. Sci.  dan course id, pilih atribut nama dan course_id dari tabel instructor dan teaches, yang mana relasinya berdasarkan kesamaan ID dan juga atribut dept_name dari entity instructor adalah Computer Science.

```sql
SELECT name, course_id FROM instructor, teaches
WHERE instructur.ID=teaches.ID and instructor.dept_name="Comp. Sci.";
```
Output: <br/>

![image](https://github.com/nicholast25/Catatan-Sistem-Basis-Data/assets/147079216/d917e4a5-fe93-4f0e-ad7b-da4027b53dae)


