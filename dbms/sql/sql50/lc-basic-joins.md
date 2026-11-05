# Basic Joins

## Calculate yesterday

```sql
select today.id from
weather today
inner join
weather yesterday
on today.recordDate = yesterday.recordDate + INTERVAL '1 day' 
where today.temperature > yesterday.temperature
```

## Normalising a table

```sql
Write a solution to find the average time each machine takes to complete a process.

Input: 
Activity table:
+------------+------------+---------------+-----------+
| machine_id | process_id | activity_type | timestamp |
+------------+------------+---------------+-----------+
| 0          | 0          | start         | 0.712     |
| 0          | 0          | end           | 1.520     |
| 0          | 1          | start         | 3.140     |
| 0          | 1          | end           | 4.120     |
| 1          | 0          | start         | 0.550     |
| 1          | 0          | end           | 1.550     |
| 1          | 1          | start         | 0.430     |
| 1          | 1          | end           | 1.420     |
| 2          | 0          | start         | 4.100     |
| 2          | 0          | end           | 4.512     |
| 2          | 1          | start         | 2.500     |
| 2          | 1          | end           | 5.000     |
+------------+------------+---------------+-----------+
Output: 
+------------+-----------------+
| machine_id | processing_time |
+------------+-----------------+
| 0          | 0.894           |
| 1          | 0.995           |
| 2          | 1.456           |
+------------+-----------------+
Explanation: 
There are 3 machines running 2 processes each.
Machine 0's average time is ((1.520 - 0.712) + (4.120 - 3.140)) / 2 = 0.894
Machine 1's average time is ((1.550 - 0.550) + (1.420 - 0.430)) / 2 = 0.995
Machine 2's average time is ((4.512 - 4.100) + (5.000 - 2.500)) / 2 = 1.456

select machine_id , 
ROUND(AVG(end_time-start_time)::numeric,3) as processing_time
from(
select start_row.machine_id,
start_row.process_id,
start_row.timestamp as start_time,
end_row.timestamp as end_time
from Activity as start_row
join Activity as end_row
on start_row.machine_id = end_row.machine_id
and start_row.process_id = end_row.process_id
where start_row.activity_type = 'start'
and end_row.activity_type = 'end'
) as normalised_tbl
group by machine_id;

-- normalised_tbl : this was the major challenge
| machine_id | process_id | start_time | end_time |
| ---------- | ---------- | ---------- | -------- |
| 0          | 0          | 0.712      | 1.52     |
| 0          | 1          | 3.14       | 4.12     |
| 1          | 0          | 0.55       | 1.55     |
| 1          | 1          | 0.43       | 1.42     |
| 2          | 0          | 4.1        | 4.512    |
| 2          | 1          | 2.5        | 5        |
```

## IS null

```sql
select name, bonus from
Employee e left join Bonus b
on e.empId = b.empId
where bonus < 1000 or bonus is null;
```

## Multiple tables can be joined

```sql
select s.student_id, s.student_name, sub.subject_name,
count(e.student_id) as attended_exams from 
Students s cross join Subjects sub
left join Examinations e
on s.student_id = e.student_id
AND e.subject_name = sub.subject_name
group by s.student_id, s.student_name, sub.subject_name
order by s.student_id, sub.subject_name;
```

## Having clause

```sql
select name from Employee
where id in (
    select managerId from Employee
    where managerId is not null
    group by managerId
    having count(*) >= 5
)
```