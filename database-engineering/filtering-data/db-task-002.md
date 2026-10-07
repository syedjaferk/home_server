# DB-TASK-002

{% tabs %}
{% tab title="1. Question" %}
Get all movies (films) that have a rental rate greater than $3.
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT title, rental_rate
FROM film
WHERE rental_rate > 3;
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="2. Question" %}
Get all movies that have a rental rate greater than $3 _and_ a replacement cost less than $20.
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT title, rental_rate, replacement_cost
FROM film
WHERE rental_rate > 3 AND replacement_cost < 20;
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="3. Question" %}
Get all movies that are either rated as 'PG' or have a rental rate of $0.99.
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT title, rating, rental_rate
FROM film
WHERE rating = 'PG' OR rental_rate = 0.99;
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="4. Question" %}
Show the first 10 movies sorted by rental rate (highest first).
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT title, rental_rate
FROM film
ORDER BY rental_rate DESC
LIMIT 10;
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="5. Question" %}
Skip the first 5 movies and fetch the next 3 sorted by rental rate in ascending order.
{% endtab %}

{% tab title="Solution" %}
Using FETCH

```sql
SELECT title, rental_rate
FROM film
ORDER BY rental_rate ASC
OFFSET 5 FETCH NEXT 3 ROWS ONLY;

```

Using LIMIT

```sql
SELECT title, rental_rate
FROM film
ORDER BY rental_rate ASC
OFFSET 5 LIMIT 3;

```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="6. Question" %}
Skip the first 5 movies and fetch the next 3 sorted by rental rate in ascending order.
{% endtab %}

{% tab title="Solution" %}

{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="7. Question" %}
Get all movies with a rental duration between 3 and 7 days.
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT title, rental_duration
FROM film
WHERE rental_duration BETWEEN 3 AND 7;
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="8. Question" %}
Get all movies where the title starts with 'A' and ends with 'e'
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT title
FROM film
WHERE title LIKE 'A%e';
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="9. Question" %}
Find all customers who do not have an email address listed.
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT first_name, last_name
FROM customer
WHERE email IS NULL;
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="10. Question" %}
Find all movies released in 2006 with a rental rate of $2.99 or $3.99, and their title starts with 'S'. Display the top 5 results.SELECT title, rental\_rate, release\_year
{% endtab %}

{% tab title="Solution" %}
```sql
FROM film
WHERE release_year = 2006 
  AND rental_rate IN (2.99, 3.99) 
  AND title LIKE 'S%'
LIMIT 5;
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="11. Question" %}
Display 10 customers after skipping the first 20, sorted alphabetically by last name.
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT first_name, last_name
FROM customer
ORDER BY last_name
LIMIT 10 OFFSET 20;
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="12. Question" %}
Get the top 5 movies with the highest replacement cost, skipping the most expensive one.
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT title, replacement_cost
FROM film
ORDER BY replacement_cost DESC
OFFSET 1 FETCH NEXT 5 ROWS ONLY;
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="13. Question" %}
Find all rentals that occurred between '2005-05-01' and '2005-06-01'.
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT rental_id, rental_date, customer_id
FROM rental
WHERE rental_date BETWEEN '2005-05-01' AND '2005-06-01';
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="14. Question" %}
Get all actors whose last names contain the letters "man".
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT first_name, last_name
FROM actor
WHERE last_name LIKE '%man%';
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="15. Question" %}
Find all movies where the special features are not listed (i.e., `special_features` is `NULL`).
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT title
FROM film
WHERE special_features IS NULL;
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="16. Question" %}
Find all movies where the rental duration is more than 7 days.
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT title, rental_duration
FROM film
WHERE rental_duration > 7;
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="17. Question" %}
Find the first 10 movies with a rental rate of $2.99 or $4.99, a rating of 'R', and a title containing the word "L".
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT title, rental_rate, rating
FROM film
WHERE rental_rate IN (2.99, 4.99) 
  AND rating = 'R' 
  AND title LIKE '%L%'
LIMIT 10;
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="18. Question" %}
Find all movies where the title starts with "A" or "B" and ends with "s".
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT title
FROM film
WHERE title SIMILAR TO '(A|B)%s';
```
{% endtab %}
{% endtabs %}

{% tabs %}
{% tab title="19. Question" %}
Find all movies where the title contains "Man", "Men", or "Woman".
{% endtab %}

{% tab title="Solution" %}
```sql
SELECT title
FROM film
WHERE title SIMILAR TO '%(Man|Men|Woman)%';
```
{% endtab %}
{% endtabs %}



### Bonus Q/A

1. Find all movies where the special features are not listed (i.e., `special_features` is `NULL`).
2. Find all movies where the rental duration is more than 7 days.
3. Find all movies that have a rental rate of $4.99 _and_ a replacement cost of more than $20.
4. Find all movies that have a rental rate of $0.99 _or_ a rating of 'PG-13'.
5. Retrieve the first 5 rows of movies sorted alphabetically by title.
6. Skip the first 10 rows and fetch the next 3 movies with the highest replacement cost.
7. Find all movies where the rating is either 'G', 'PG', or 'PG-13'.
8. Find all movies with a rental rate between $2 and $4.
9. Find all movies with titles that start with 'The'.
10. Find the first 10 movies with a rental rate of $2.99 or $4.99, a rating of 'R', and a title containing the word "Love".
11. Find all movies where the title contains the `%` symbol.
12. Find all movies where the title contains an underscore (`_`).
13. Find all movies where the title starts with "A" or "B" and ends with "s".
14. Find all movies where the title contains "Man", "Men", or "Woman".
15. Find all movies with titles that contain digits (e.g., "007", "2", "300").
16. Find all movies with titles containing a backslash (`\`).
17. Find all movies where the title does contain the words "Love" or "Hate".
18. Find the first 5 movies with titles that end with "er", "or", or "ar".

