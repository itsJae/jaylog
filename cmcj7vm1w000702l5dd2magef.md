---
title: "[SQL] Writing Efficient SQL Queries"
seoTitle: "[SQL] Writing Efficient SQL Queries"
seoDescription: "Think of yourself building a program. It can be any types, such as website, app, etc. These applications may require database to show the data that the user"
datePublished: Mon Jun 30 2025 14:51:27 GMT+0000 (Coordinated Universal Time)
cuid: cmcj7vm1w000702l5dd2magef
slug: sql-writing-efficient-sql-queries
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1751292603168/b0b43c7d-8e08-47b2-a64c-b600e3511831.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1751294227338/cb971580-b38a-4d8c-a2f6-b383b8da77f0.jpeg
tags: optimization, databases, sql, efficiency, rdbms

---

---

Think of yourself building a program. It can be any types, such as website, app, etc. These applications may require database to show the data that the user requested.

For example, you can think of a table that stores GPS-related data. The longitude and latitude are stored in the database every second. One row increases every second. And… let’s say you have 10,000 users that use your application. Then your DB receive 10,000 rows a second.

How are you going to deal with such circumstance? In this article, I will be introducing three key strategies/skills we can use to make our SQL queries more efficient.

---

## 1\. Only Select Columns You Want

It is tempting to start your query with `SELECT * FROM`. However, what if your table has a column that stores large scale of texts?

For example, the table `reviews` has a column called `description`. Even though your application has set a limit of characters for restaurant review, selecting `description` column when you do not need is very inefficient.

Example code:

```python
star_query = "SELECT * FROM `bigquery-public-data.github_repos.contents`"
show_amount_of_data_scanned(star_query)

basic_query = "SELECT size, binary FROM `bigquery-public-data.github_repos.contents`"
show_amount_of_data_scanned(basic_query)
```

```sql
Data processed: 2682.118 GB
Data processed: 2.531 GB
```

---

## 2\. Read Less Data

Reading less data, in other words, we want to scan less data. It’s not very different from the first strategy. For example, you are selecting `a.name` where `a.id = b.id`. In this case, you are scanning three columns to retreive just a single column. Actually, you can get the same result with less columns scanned.

More efficient code:

```python
more_data_query = """
                  SELECT MIN(start_station_name) AS start_station_name,
                      MIN(end_station_name) AS end_station_name,
                      AVG(duration_sec) AS avg_duration_sec
                  FROM `bigquery-public-data.san_francisco.bikeshare_trips`
                  WHERE start_station_id != end_station_id 
                  GROUP BY start_station_id, end_station_id
                  LIMIT 10
                  """
show_amount_of_data_scanned(more_data_query)

less_data_query = """
                  SELECT start_station_name,
                      end_station_name,
                      AVG(duration_sec) AS avg_duration_sec                  
                  FROM `bigquery-public-data.san_francisco.bikeshare_trips`
                  WHERE start_station_name != end_station_name
                  GROUP BY start_station_name, end_station_name
                  LIMIT 10
                  """
show_amount_of_data_scanned(less_data_query)
```

In `more_data_query` example, you are scanning FIVE columns.

1. start\_station\_name
    
2. end\_station\_name
    
3. duration\_sec
    
4. start\_station\_id
    
5. end\_station\_id
    

In `less_data_query`, you are scanning THREE columns.

1. start\_station\_name
    
2. end\_station\_name
    
3. duration\_sec
    

```python
Data processed: 0.076 GB
Data processed: 0.06 GB
```

---

## 3\. Avoid N:N JOINs

First, let’s have a look at different types of x-to-x JOINs

### 1:1 JOIN

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1751293851420/f02bb39a-d351-4f1b-9a93-2598ddfdc8ed.png align="center")

Most of the JOINs that you have executed in this course have been **1:1 JOINs**. In this case, each row in each table has at most one match in the other table.

---

### N:1 JOIN

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1751293873765/7d6c404d-18d9-4717-ac47-051e203f1b92.png align="center")

Another type of JOIN is an **N:1 JOIN**. Here, each row in one table matches potentially many rows in the other table.

---

### N:N JOIN

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1751293886723/76ae2170-c1e4-4d68-ae2e-afee9f240383.png align="center")

Finally, an **N:N JOIN** is one where a group of rows in one table can match a group of rows in the other table. Note that in general, all other things equal, this type of JOIN produces a table with many more rows than either of the two (original) tables that are being JOINed.

Now, let’s dive into actual examples.

Inefficient way:

```python
big_join_query = """
                 SELECT repo,
                     COUNT(DISTINCT c.committer.name) as num_committers,
                     COUNT(DISTINCT f.id) AS num_files
                 FROM `bigquery-public-data.github_repos.commits` AS c,
                     UNNEST(c.repo_name) AS repo
                 INNER JOIN `bigquery-public-data.github_repos.files` AS f
                     ON f.repo_name = repo
                 WHERE f.repo_name IN ( 'tensorflow/tensorflow', 'facebook/react', 'twbs/bootstrap', 'apple/swift', 'Microsoft/vscode', 'torvalds/linux')
                 GROUP BY repo
                 ORDER BY repo
                 """
show_time_to_run(big_join_query)
```

```python
Time to run: 13.028 seconds
```

```python
small_join_query = """
                   WITH commits AS
                   (
                   SELECT COUNT(DISTINCT committer.name) AS num_committers, repo
                   FROM `bigquery-public-data.github_repos.commits`,
                       UNNEST(repo_name) as repo
                   WHERE repo IN ( 'tensorflow/tensorflow', 'facebook/react', 'twbs/bootstrap', 'apple/swift', 'Microsoft/vscode', 'torvalds/linux')
                   GROUP BY repo
                   ),
                   files AS 
                   (
                   SELECT COUNT(DISTINCT id) AS num_files, repo_name as repo
                   FROM `bigquery-public-data.github_repos.files`
                   WHERE repo_name IN ( 'tensorflow/tensorflow', 'facebook/react', 'twbs/bootstrap', 'apple/swift', 'Microsoft/vscode', 'torvalds/linux')
                   GROUP BY repo
                   )
                   SELECT commits.repo, commits.num_committers, files.num_files
                   FROM commits 
                   INNER JOIN files
                       ON commits.repo = files.repo
                   ORDER BY repo
                   """

show_time_to_run(small_join_query)
```

```python
Time to run: 4.413 seconds
```

There is a huge gap in efficiency. It’s 8.6 sec difference!

The first approach JOIN first, then filters out.

The efficient one(second approach) filters out first, then JOIN, which means it allows you to join the two tables that are already quite minimized. On the other hand, if you join first, you have two tables with a bunch of data, and your query scans tons of rows to find matching keys.