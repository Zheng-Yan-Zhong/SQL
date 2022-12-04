# SQL
Structure Query Language(結構性篩選語言)

## Download

[Download Server](https://dev.mysql.com/downloads/mysql/)
[Download Workbench](https://dev.mysql.com/downloads/workbench/)

[Sequel Ace](https://github.com/Sequel-Ace/Sequel-Ace)

## Grammar

### SELECT
現在資料庫Test中有個user的資料表，並且其中有兩筆資料

| id | name
| -------- | -------- 
| 1     | Anne    
| 2     | Dennis    

當今天要取得Test的`(.)`user中所有資料可以使用
```sql=
SELECT * FROM `Test`.`user`
```

| id | name
| -------- | -------- 
| 1     | Anne    
| 2     | Dennis    

只想取得name的資料欄位時
```sql=
SELECT name FROM `Test`.`user`
```

|  name
| -------- 
| Anne    
| Dennis   

### NOT

當想要取得不是使用者Dennis的使用者資料時
```sql=
SELECT name FROM `Test`.`user` WHERE NOT name='Dennis'
```
| id | name
| -------- | -------- 
| 1     | Anne    

### DISTINCT

當想要取得不重複的名稱時

| id | name
| -------- | -------- 
| 1     | Anne    
| 2     | Dennis    
| 3    | Anne    
| 4     | Jack    
```sql=
SELECT DISTINCT name FROM `Test`.`user` 
```
可以看到重複的Anne只會出現一次

|name
| -------- 
| Anne    
| Dennis    
| Jack    

### COUNT

計算共有幾筆時
```sql=
SELECT COUNT(DISTINCT name) FROM `Test`.`user`
```

|COUNT(DISTINCT)
| -------- 
| 3

### ORDER BY

當需要透過名字進行排序時
```sql=
SELECT * FROM `Test`.`user` ORDER BY name
```
| id | name
| -------- | -------- 
| 1     | Anne    
| 3     | ANNE    
| 2    | Dennis    
| 4     | Jack    

當然也可以透過名字做降冪的操作
```sql=
SELECT * FROM `Test`.`user` ORDER BY name DESC
```
| id | name
| -------- | -------- 
| 4     | Jack    
| 2     | Dennis    
| 1   | Anne    
| 3     | Anne    

### INSERT INTO