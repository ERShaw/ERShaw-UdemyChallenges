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









