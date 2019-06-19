## 1번 문제

```sql
SELECT outter.id as id, outter.type as type, outter.status as status, outter.amount as amount, (outter.amount - inner.amount_avg) as difference
FROM account outter
LEFT OUTER JOIN
(SELECT a.type, AVG(a.amount) as amount_avg
FROM account a
WHERE a.status = 'Active'
GROUP BY a.type) inner
ON outter.type = inner.type
WHERE status = 'Active';
```

![image](https://user-images.githubusercontent.com/28293389/59749393-e2029000-92b7-11e9-84dd-ce2164296b16.png)



## 2번 문제
```sql
CREATE DATABASE problem4;

CREATE EXTERNAL TABLE problem4.customer(
id INT,
fname string,
lname string,
address string,
city string,
state string,
zip string,
birthday string,
hireday string
)
ROW FORMAT delimited
FIELDS TERMINATED BY ','
STORED AS PARQUET
LOCATION '/user/training/problem2/data/employee/'
```

## 3번 문제
```sql
SELECT id, fname, lname, hphone
FROM problem3.customer
WHERE id in (SELECT id FROM problem3.account WHERE account
```

![image](https://user-images.githubusercontent.com/28293389/59750104-39edc680-92b9-11e9-80bc-81986c0cab57.png)


## 4번문제

## 5번문제
```sql
SELECT e.fname, e.lname, e.city, e.state
FROM problem5.employee e
WHERE e.city = 'Palo Alto' AND e.state = 'CA'
UNION ALL
SELECT c.fname, c.lname, c.city, c.state
FROM problem5.customer c
WHERE c.city = 'Palo Alto' AND c.state = 'CA'
```
![image](https://user-images.githubusercontent.com/28293389/59750867-7837b580-92ba-11e9-8e3a-fb1935d75072.png)

## 6번문제
```sql
CREATE TABLE problem6.newemployee
AS SELECT id, fname, lname, address, city, state, zip, substr(birthday, 0, 5) as birthday FROM problem6.employee
```
![image](https://user-images.githubusercontent.com/28293389/59751273-32c7b800-92bb-11e9-98ab-4b808342c3a3.png)


## 7번문제
```sql
SELECT CONCAT(fname, " ", lname) AS AA
FROM problem7.employee
WHERE city ='Seattle'
ORDER BY AA
```

![image](https://user-images.githubusercontent.com/28293389/59751939-622af480-92bc-11e9-8287-7f4da95385f5.png)

## 8번문제

## 9번문제

```
sqoop import --connect jdbc:mysql://localhost/problem8 --username cloudera --password cloudera --table solution --delete-target-dir --target-dir /user/training/problem8/data/customer

INFO mapreduce.Job: Counters: 30
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=143165
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=105
		HDFS: Number of bytes written=0
		HDFS: Number of read operations=4
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=2
	Job Counters 
		Launched map tasks=1
		Other local map tasks=1
		Total time spent by all maps in occupied slots (ms)=10446
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=5223
		Total vcore-seconds taken by all map tasks=5223
		Total megabyte-seconds taken by all map tasks=2674176
	Map-Reduce Framework
		Map input records=0
		Map output records=0
		Input split bytes=105
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=78
		CPU time spent (ms)=550
		Physical memory (bytes) snapshot=121901056
		Virtual memory (bytes) snapshot=2264334336
		Total committed heap usage (bytes)=62980096
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=0
19/06/19 02:09:46 INFO mapreduce.ImportJobBase: Transferred 0 bytes in 23.0352 seconds (0 bytes/sec)
19/06/19 02:09:46 INFO mapreduce.ImportJobBase: Retrieved 0 records.

```

## 10번 문제


## 11번 문제


## 12번 문제