# Udemy Challenges
A collection of SQL challenge questions and answers that showcase my SQL knowledge. 

## Table of Contents
- [Tools](#tools)
- [Data Sources](#data-sources)
- [Beginner Challenges](#beginner-challenges)
- [Challenge 1: SELECT](#challenge-1-select)
- [Challenge 2: ORDER BY](#challenge-2-order-by)
- [Challenge 3: SELECT DISTINCT](#challenge-3-select-distinct)
- [Day 1 Daily Challenge](#day-1-daily-challenge)
- [Challenge 4: WHERE](#challenge-4-where)
- [Challenge 5: WHERE operators](#challenge-5-where-operators)
- [Challenge 6: WHERE with AND OR](#challenge-6-where-with-and-or)
- [Challenge 7: BETWEEN](#challenge-7-between)
- [Challenge 8: IN](#challenge-8-in)
- [Challenge 9: LIKE](#challenge-9-like)
- [Day 2 Daily Challenge](#day-2-daily-challenge)
- [Challenge 10: Aggregate functions ](#challenge-10-aggregate-functions)
- [Challenge 11: GROUP BY](#challenge-11-group-by)
- [Challenge 12: GROUP BY multiple columns](#challenge-12-group-by-multiple-columns)
- [Challenge 13: HAVING](#challenge-13-having)
- [Intermediate Challenges](#intermediate-challenges)
- [Challenge 14: LENGTH,LOWER & UPPER](#challenge-14-length-lower-upper)
- [Challenge 15: LEFT & RIGHT](#challenge-15-left-right)
- [Challenge 16: Concatenate](#challenge-16-concatenate)
- [Challenge 17: POSITION](#challenge-17-position)
- [Challenge 18: SUBSTRING](#challenge-18-substring)
- [Challenge 19: EXTRACT](#challenge-19-extract)
- [Challenge 20: TO_CHAR](#challenge-20-to-char)
- [Challenge 21: Intervals & Timestamps](#challenge-21-intervals-timestanps)
- [Challenge 22: Mathematical Functions and operators](#challenge-22-mathematical-functions-and-operators)
- [Challenge 23: CASE WHEN](#challenge-23-case-when)
- [Challenge 24: CAST & COALESCE](#challenge-24-cast-coalesce)
- [Challenge 25: INNER JOIN](#challenge-25-inner-join)
- [Challenge 26: LEFT OUTER JOIN](#challenge-26-left-outer-join)
- [Challenge 27: Joins](#challenge-27-joins)
- [Challenge 28: Joins on multiple conditions](#challenge-28-joins-on-multiple-conditions)
- [Challenge 29: Joining multiple tables](#challenge-29-joining-multiple-tables)
- [Challenge 30: More Challenges](#challenge-30-more-chalenges)
- [Advanced Challenges](#advanced-challenges)
- 
## Tools
PostgreSQL 

pgAdmin

## Data Sources 
Sales Data: The primary dataset used for these challenges 

## Beginner Challenges

### Challenge 1: SELECT
The Marketing Manager asks you for a list of all customers stating their first name, last name, and email address. 

```
SELECT first_name, last_name, email
FROM customer 
```
**Results**: [challenge1.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13371990/challenge1.csv)


### Challenge 2: ORDER BY
The Marketing Manager asks you to order the customer list by last name. They want to start from 'Z' and end with 'A.' In case of the same last name, the order should be based on the first name, also order from 'Z' to 'A.'

```
SELECT first_name, last_name
FROM customer
ORDER BY last_name DESC
```
**Results**: [challenge2.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13372009/challenge2.csv)


### Challenge 3: SELECT DISTINCT
The Marketing Manager asks you about the different prices that have been paid. To make it easier for them order the prices from high to low.

```
SELECT DISTINCT amount
FROM payment
ORDER BY amount DESC
```

**Results**: [challenge3.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13372018/challenge3.csv)


```
SELECT DISTINCT amount
FROM payment
ORDER BY amount DESC
LIMIT 5
```

**Results**: 
[challenge3Limit.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13372024/challenge3Limit.csv)

```
SELECT COUNT(DISTINCT amount)
FROM payment
```

**Results**: [challenge3CountDistinct.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13372029/challenge3CountDistinct.csv)


### Day 1 Daily Challenge

1. Create a list of all the distinct districts customers are from.
```
SELECT DISTINCT
district
FROM address
```
**Results**: [D1dailyQ1.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13386721/D1dailyQ1.csv)

2. What is the latest rental date?
```
SELECT rental_data
FROM rental
ORDER BY rental_date DESC
LIMIT 1
```
**Result**: [D1dailyQ2.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13386857/D1dailyQ2.csv)

3. How many films does the company have?
```
SELECT
COUNT(*)
FROM film
```
**Results**: [D1dailyQ3.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13386870/D1dailyQ3.csv)

4. How many distinct last names of the customers are there?
```
SELECT
COUNT(DISTINCT last_name)
FROM customer
```
**Results**: [D1dailyQ4.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13386886/D1dailyQ4.csv)


### Challenge 4: WHERE
How many payments were made by the customer with customer_id = 100? What is the last name of customers with the first name 'ERICA'?

```
SELECT COUNT (*)
FROM payment
WHERE customer_id = 100
```

**Result**: [challenge4.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13372033/challenge4.csv)

```
SELECT first_name, last_name
FROM customer
WHERE first_name = 'ERICA'
```

**Results**: [challenge4pt2.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13372036/challenge4pt2.csv)

### Challenge 5: WHERE operators
The Inventory Manager asks you how many rentals have not been returned yet (return_date is null).

The Sales Manager asks you how for a list of all the payment_ids with an amount less than or equal to $2. Include payment_id and the amount. 

```
SELECT COUNT (*)
FROM rental 
WHERE return_date is not null
```

**Results**:[challenge5.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13372152/challenge5.csv)

```
SELECT payment_id, amount
FROM payment 
WHERE amount <= 2
```

**Results**: [challenge5pt2.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13372052/challenge5pt2.csv)


### Challenge 6: WHERE with AND OR
The Support Managher asks you about a list of all the paayments of customer 322, 346, and 354 where the amount is either less than $2 or greater than $10. It should be ordered by the customer first (ascending) and then ordered by the amount in a descending order.

```
SELECT *
FROM payment
WHERE 
(customer_id = 322 OR customer_id = 346 OR customer_id = 354)
AND
(amount < 2 OR amount > 10)
ORDER BY customer_id ASC, amount DESC
```

**Results**: [challenge6.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13372054/challenge6.csv)


### Challenge 7: BETWEEN
There have been some faulty payments and you need to help to find out how many payments have been affected. How many payments were made on January 26th and 27th 2020 with an amount between 1.99 and 3.99?

```
SELECT COUNT(*)
FROM payment
WHERE amount BETWEEN 1.99 AND 3.99 
AND payment_date BETWEEN '2020-01-26' AND '2020-01-27 23:59'
```
We use 23:59 to query for all day on the 27th. If we just queried 2020-01-27 it would only query up until 12AM on the 27th, so we use the timestamp to account for the rest of the day. We could also use 2020-01-28, but 2020-01-27 23:59 is more accurate.

**Results**:[challenge7.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13372162/challenge7.csv)


### Challenge 8: IN
There have been 6 complaints of customers about their payments. 
customer_id: 12, 25, 67,93,124,234
The concerned payments are all the payments of these customers with amount 4.99, 7.99, and 9.99 in January 2020. 

```
SELECT * FROM payment 
WHERE customer_id IN (12,25,67,93,124,234)
AND amount IN (4.99,7.99,9.99)
AND payment_date BETWEEN '2020-01-01' AND '2020-02-01'
```

**Results**: [challenge8.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13372179/challenge8.csv)


### Challenge 9: LIKE
Help the Inventory Manager find the following:
How many movies are there that contain "Documentary" in the description?
How many customers are there with a first name that is 3 letters long and either an 'X' or a 'Y' as the last letter in the last name? 

```
SELECT COUNT (*)
FROM film
WHERE description LIKE '%Documentary%'
```

**Results**: [challenge9pt1.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13372136/challenge9pt1.csv)


```
SELECT COUNT(*)
FROM customer
WHERE first_name LIKE '___'
AND (last_name LIKE '%X'
OR last_name LIKE '%Y')
```

**Results**: [challenge9.csv](https://github.com/ERShaw/Erik-Shaw-UdenyChallenges/files/13372071/challenge9.csv)

### Day 2 Daily Challenge
1. How many movies are there that contain 'Saga' in the description and where the title starts either with 'A' or ends with 'R'? Use the alias 'no_of_movies'
```
SELECT
COUNT (*) AS number_of_movie
FROM film
WHERE description LIKE '%Saga%'
AND (title LIKE 'A%' OR title LIKE '%R')
```
**Result**: [D2dailyQ1.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13387146/D2dailyQ1.csv)

2. Create a list of all cistomers where the first name contains 'ER' and has an 'A' as the second letter. Order the results by the last name descendingly.
```
SELECT

```
**Result**: [D2dailyQ2.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13387175/D2dailyQ2.csv)

3. How many payments are there where the amount is either 0 or is between 3.99 and 7.99 and in the same time has happened on 2020-05-01.
```
SELECT 
COUNT (*)
FROM payment
WHERE (amount = 0 
OR amount BETWEEN 3.99 AND 7.99)
AND payment_date BETWEEN '2020-05-01' AND '2020-05-02'
```
**Result**: [D2dailyQ3.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13387276/D2dailyQ3.csv)


### Challenge 10: Aggregate functions 
Your manager wants to get a better understanding of the films. You are asked to write a query to see the minimum, maximum, average rounded to two decimal places, and the sum of the replacement cost of the films. 
```
SELECT
MIN (replacement_cost),
MAX(replacement_cost),
ROUND(AVG(replacement_cost),2) AS AVG,
SUM(replacement_cost)
FROM film
```
**Results**: [challenge10.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13387412/challenge10.csv)

### Challenge 11: GROUP BY
Your manager wants to know which of the two employees is rsponsible for more payments. Which of the two is responsible for a higher overall payment amount? How do these amounts change if we don't consider amounts equal to 0?

```
SELECT staff_id,
SUM (amount),
COUNT(*)
FROM payment
GROUP BY staff_id
```
**Results**: [challenge11pt1.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13387451/challenge11pt1.csv)

```
SELECT staff_id,
SUM (amount),
COUNT(*)
FROM payment
WHERE amount ! = 0
GROUP BY staff_id
```
**Results**: [challenge11pt2.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13387533/challenge11pt2.csv)


### Challenge 12: GROUP BY multiple columns
There are two competitions between the two employees: Which employee had the highest sales amount in a single day? Which employee had the most sales in a single day(not counting payments with amount = 0?

```
SELECT staff_id, DATE(payment_date),
SUM(amount),
COUNT(*)
FROM payment
GROUP BY staff_id, DATE(payment_date)
ORDER BY SUM(amount) DESC
```
**Results**: [challenge12pt1.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13387579/challenge12pt1.csv)

```
SELECT staff_id, DATE(payment_date),
SUM(amount),
COUNT(*)
FROM payment
WHERE amount !=0
GROUP BY staff_id, DATE(payment_date)
ORDER BY SUM(amount) DESC
```
**Results**: [challenge12pt2.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13387600/challenge12pt2.csv)


### Challenge 13: HAVING
In 2020, April 28, 29, and 30 were days with very high revenue. That's why we want to focus only on these days in this challenge. Find out what the average payment amount grouped by customer and day - consider only the days/customers with more then 1 payment (per customer and day.) Order by the average amount in a descending order.

```
SELECT
customer_id, DATE(payment_date),
ROUND(AVG(amount),2) AS avg_amount,
COUNT (*)
FROM payment
WHERE DATE(payment_date) IN ('2020-04-28', '2020-04-29', '2020-04-30')
GROUP BY customer_id, DATE(payment_date)
ORDER BY ROUND (AVG(amount),2) DESC
```
**Results**: [challenge13.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13387771/challenge13.csv)

## Intermediate Challenges

### Challenge 14: LENGTH, LOWER & UPPER
In the email system there was a problem with names where either the first name or the last name is more than 10 characters long. Find these customers and output the list of these first and last names in all lower case.

```
SELECT
LOWER(first_name),
LOWER(last_name),
LOWER(email)
FROM customer
WHERE LENGTH(first_name) > 10
OR LENGTH(last_name) > 10
```
**Results**: [challenge14.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13398878/challenge14.csv)


### Challenge 15: LEFT & RIGHT
Extract the last 5 characters of the email address (the email address always ends with '.org') How can you extract just the dot'.' from the email address?

```
SELECT email,
RIGHT(email,5)
FROM customer
```
**Results**: [challenge15pt1.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13398938/challenge15pt1.csv)

```
SELECT email,
LEFT(RIGHT(email,4),1)
FROM customer
```
**Results**: [challenge15pt2.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13398949/challenge15pt2.csv)

### Challenge 16: Concatenate
You need to create an anonymized version of the email addresses. It should be the first character followed by '***' and then the last part starting with '@'. Note the email address always ends with '@sakilacustomer.org'

```
SELECT
LEFT(email,1) || '***' || RIGHT(email,19) AS anonymized_email
FROM customer
```
**Results**: [challenge16.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13398958/challenge16.csv)


### Challenge 17: POSITION
In this challenge you have only the email address and the last name of customers. You need to extract the first name from the email address and concatenate it with the last name. It should be in the form: 'Last name, First'

```
SELECT
last_name || ', ' || LEFT(email, POSITION('.' IN email)-1),
last_name
FROM customer
```
**Results**: [challenge17.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13398984/challenge17.csv)


### Challenge 18: SUBSTRING
You need to create an anonymized form of the email addresses in the following format: 'M***S***@sakilcustomer.org'
In a second query create an anonymized form of the email addresses in the following way: '***Y.S***sakilcustomer.org'

```
SELECT
LEFT(email,1) || '***' || SUBSTRING(email from POSITION('.' IN email)for 2)
|| '***' || SUBSTRING(email from POSITION('@' IN email))
FROM customer
```
**Results**: [challenge18pt1.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401435/challenge18pt1.csv)

```
SELECT
'***'
|| SUBSTRING(email from POSITION('.' in email)-1 for 3)
|| '***'
|| SUBSTRING(email from POSITION('@' in email))
FROM customer
```
**Results**: [challenge18pt2.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401481/challenge18pt2.csv)


### Challenge 19: EXTRACT
You need to analyze the payments and find out the following:
1. What's the month with the highest total payment amount?

```
SELECT
EXTRACT(month from payment_date) AS month,
SUM(amount) AS payment_amount
FROM payment
GROUP BY month
ORDER BY payment_amount DESC
```
**Results**: [challenge19pt1.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401558/challenge19pt1.csv)

2. What's the day of week with the highest total payment amount?

```
SELECT
EXTRACT(dow from payment_date) AS day_of_week,
SUM(amount) AS payment_amount
FROM payment
GROUP By day_of_week
ORDER BY payment_amount DESC
```
**Results**: [challenge19pt2.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401567/challenge19pt2.csv)

4. What's the highest amount one customer has spent in a week?

```
SELECT
customer_id,
EXTRACT(week from payment_date) AS week,
SUM(amount) AS payment_amount
FROM payment
GROUP By week, customer_id
ORDER BY payment_amount DESC
```
**Results**: [challenge19pt3.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401575/challenge19pt3.csv)


### Challenge 20: TO_CHAR
You need to sum payments and group in the following formats:
![TOCHARchallengept1](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/assets/124463259/d1f7ad8a-bffd-418b-884c-6490cf6f9554)

```
SELECT
SUM(amount) AS total_payment,
TO_CHAR(payment_date,'Dy, DD/MM/YYYY') AS day
FROM payment
GROUP BY day
ORDER BY total_payment
```
**Results**: [challenge20pt1.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401639/challenge20pt1.csv)

![TOCHARpt2](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/assets/124463259/87b6a988-3db9-4221-adf1-c790722adcf6)

```
SELECT
SUM(amount) AS total_payment,
TO_CHAR(payment_date,'Mon, YYYY') AS mon_year
FROM payment
GROUP BY mon_year
ORDER BY total_payment ASC
```
**Results**: [challenge20pt2.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401653/challenge20pt2.csv)

![TOCHARpt3](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/assets/124463259/44d73017-53fa-4578-9d72-d2dcbc487cf5)

```
SELECT
SUM(amount) AS total_payment,
TO_CHAR(payment_date,'Dy, HH:MI') AS day_time
FROM payment
GROUP BY day_time
ORDER BY total_payment DESC
```
**Results**: [challenge20pt3.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401652/challenge20pt3.csv)

### Challenge 21: Intervals & Timestamps
You need to create a list for the support team of all rental durations of customer with customer_id 35. Also you need to find out which customer has the longest average rental duration?

```
SELECT
customer_id,
return_date-rental_date AS rental_duration
FROM rental
WHERE customer_id=35
```
**Results**: [challenge21pt1.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401687/challenge21pt1.csv)

```
SELECT
customer_id,
AVG(return_date-rental_date) AS rental_duration
FROM rental
GROUP BY customer_id
ORDER BY rental_duration DESC
```
**Results**: [challenge21pt2.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401692/challenge21pt2.csv)


### Challenge 22: Mathematical functions and operators
Your manager is thinking about increasing the prices for films that are more expensive to replace. For that reason, you should create a list of films including the relation of rental rate to replacement cost where the rental rate is less than 4% of the replacement cost. Create a list of film_ids together with the percentage rounded to 2 decimal places. Example: 3.54(=3.54%)

```
SELECT
film_id,
ROUND(rental_rate / replacement_cost*100,2) AS percentage
FROM film
WHERE ROUND(rental_rate / replacement_cost*100,2)< 4
ORDER BY percentage ASC
```
**Results**: [challenge22.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401823/challenge22.csv)


### Challenge 23: CASE WHEN
You need to find out how many tickets you have sold in the following categories:
1. Low price ticket: total_amount<20,000
2. Mid price ticket: total_amount between 20,000 and 150,000
3. High price ticket: total_amount>= 150,000
How many high price tickets has the company sold?

```
SELECT ticket_price, count(1)
FROM
(SELECT book_ref,
CASE
WHEN total_amount <20000 THEN 'low price'
WHEN total_amount < 150000 THEN 'mid price'
ELSE 'high price'
END AS ticket_price
FROM bookings)
GROUP BY ticket_price
```
**Results**: [challenge23pt1.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401883/challenge23pt1.csv)

You need to find out how many flights have departed in the following seasons:
Winter: December, January, February
Spring: March, April, May
Summer: June, July, August
Fall: September, October, November

```
SELECT COUNT(*) AS flights,
CASE
WHEN EXTRACT(month from scheduled_departure) IN (12,1,2) THEN 'Winter'
WHEN EXTRACT (month from scheduled_departure)  <= 5 THEN 'Spring'
WHEN EXTRACT (month from scheduled_departure) <= 8 THEN 'Summer'
ELSE 'Fall'
END AS season
FROM flights
GROUP BY season
```
**Results**: [challenge23pt2.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401887/challenge23pt2.csv)

You want to create a tier list in the following way:
1. Rating is 'PG' or 'PG-13' or length is more then 210 min: 'Great rating or long (Tier 1)
2. Description contains "Drama' and length is more than 90min: 'Long drama (tier 2)'
3. Description contains 'Drama' and length is not more than 90min: 'Short drama (tier 3)'
4. Rental_rate less than $1: 'Very cheap (tier 4)'
If one movie can be in multiple categories it gets the higher tier assigned.

```
SELECT
title,
CASE
WHEN rating IN ('PG','PG-13') OR length > 210 THEN 'Great rating or long (tier 1)'
WHEN description LIKE '%Drama%' AND length>90 THEN 'Long drama (tier 2)'
WHEN description LIKE '%Drama%' THEN 'Short drama (tier 3)'
WHEN rental_rate<1 THEN 'Very cheap (tier 4)'
END as tier_list
FROM film
WHERE 
CASE
WHEN rating IN ('PG','PG-13') OR length > 210 THEN 'Great rating or long (tier 1)'
WHEN description LIKE '%Drama%' AND length>90 THEN 'Long drama (tier 2)'
WHEN description LIKE '%Drama%' THEN 'Short drama (tier 3)'
WHEN rental_rate<1 THEN 'Very cheap (tier 4)'
END is not null
```
**Results**: [challenge23pt3.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401890/challenge23pt3.csv)


### Challenge 24: CAST & COALESCE
Replace null with 'not returned'

```
SELECT
rental_date,
COALESCE(CAST(return_date AS VARCHAR), 'not returned)
FROM rental
ORDER BY rental_date DESC
```
**Results**: [challenge24.csv](https://github.com/ERShaw/Erik-Shaw-UdemyChallenges/files/13401900/challenge24.csv)


### Challenge 25: INNER JOIN

### Challenge 26: LEFT OUTER JOIN

### Challenge 27: Joins

### Challenge 28: Joins on multiple conditions

### Challenge 29: Joining multiple tables

### Challenge 30: More Challenges





## Advanced Challenges









