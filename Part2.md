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