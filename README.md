# Udemy Challenges
A collection of SQL challenge questions and answers that showcase my SQL knowledge. 

## Table of Contents
- [Tools](#tools)
- [Data Sources](#data-sources)
- [Challenge 1: SELECT](#challenge-1-select)
- [Challenge 2: ORDER BY](#challenge-2-order-by)
- [Challenge 3: SELECT DISTINCT](#challenge-3-select-distinct)
- [Challenge 4: WHERE](#challenge-4-where)
- [Challenge 5: WHERE operators](#challenge-5-where-operators)
- [Challenge 6: WHERE with AND OR](#challenge-6-where-with-and-or)
- [Challenge 7: BETWEEN](#challenge-7-between)
- [Challenge 8: IN](#challenge-8-in)
- [Challenge 9: LIKE](#challenge-9-like)
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


### Challenge 10: Aggregate function





















