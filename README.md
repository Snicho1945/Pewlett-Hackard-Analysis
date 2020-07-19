# Pewlett-Hackard-Analysis
Data analytics using SQL 

# Challenge Summary
The intial problem that arose to require this analysis was a so called "silver tsunami", a large number of employees reaching retirement. The purpose of this analysis was to identify employees reaching retirement age along with the title they held, and what their title in the company was.

Using PostgreSQL and the data provided I was able to pull data and build up tables such as:
 `` -- mentor eligibility
    SELECT e.emp_no, e.first_name, e.last_name, rt.title, rt.from_date, ti.to_date
    INTO mentor_elig
    FROM employees as e
    INNER JOIN recenttitle AS rt
    ON (e.emp_no = rt.emp_no)
    INNER JOIN title AS ti
    ON (rt.emp_no = ti.emp_no)
    WHERE (e.birth_date BETWEEN '1965-01-01' AND '1965-12-31')
    AND (ti.to_date = '9999-01-01');``
This particular piece of code gathers data from three different tables, two provided and one of own creation(with guidance), to create a new table showing which employees are eligible for the mentorship program, which in turn will help allevate the loss of many employees to retirement.

The results of this analysis yeilded results such as break down of the total retirees by title:
- 13,011 Engineers
- 13,651 Senior Engineers
- 5	Managers
- 1,623 Assistant Engineers
- 11,949 Staff
- 12,873 Senior Staff
- 1,610 Technique Leaders
- Total of 54,722

The number of total retiring employees is 33118
The number of total employees eligible for the mentor program is 1549

Due to the large deficit of eligible mentors vs the number of retiring employees I think there should be more analysis into creating a larger mentor program to combat the large exodus of employees.

Finally do to my own shortfalls I was unable to provide an updated ERD to show how all the tables interact with each other, honestly I still have no idea how primary keys and foreign keys work.
