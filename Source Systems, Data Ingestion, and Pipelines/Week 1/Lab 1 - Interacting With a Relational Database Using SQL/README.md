### SQL Queries 
#### Overview
In this lab, you'll interact with a transactional database for a fictitious DVD rental company called Rentio. 
You'll use SQL queries to explore data about stores, staff, customers, DVDs, and rental transactions.

#### Database Schema
- **Normalized Structure**: Data about addresses, films, and rental transactions is stored in separate 
        tables to reduce redundancy.
- **Key Tables**:
  - **film**: Contains film titles, lengths, etc.
  - **category**: Lists film categories.
  - **film_category**: Maps film IDs to category IDs.

#### Basic SQL Queries
1. **Selecting Data**:
   - Retrieve specific columns:
     ```sql
     SELECT title, release_year FROM film;
     ```
   - Limit results:
     ```sql
     SELECT title, release_year FROM film LIMIT 10;
     ```
   - Select all columns:
     ```sql
     SELECT * FROM film;
     ```

2. **Filtering Results**:
   - Use the WHERE clause:
     ```sql
     SELECT * FROM film WHERE length < 60;
     ```

3. **Ordering Results**:
   - Order by length:
     ```sql
     SELECT * FROM film WHERE length < 60 ORDER BY length ASC;
     ```
   - For descending order:
     ```sql
     SELECT * FROM film WHERE length < 60 ORDER BY length DESC;
     ```

#### Joining Tables
- **Combining Data**:
  - Join film and film_category tables:
    ```sql
    SELECT film.title, film_category.category_id
    FROM film
    JOIN film_category ON film.film_id = film_category.film_id
    WHERE length < 60;
    ```
  - Join with the category table for category names:
    ```sql
    SELECT film.title, category.name
    FROM film
    JOIN film_category ON film.film_id = film_category.film_id
    JOIN category ON film_category.category_id = category.category_id
    WHERE length < 60;
    ```

#### Aggregate Functions
- **Counting Records**:
  - Group by category:
    ```sql
    SELECT category.name, COUNT(*) AS film_count
    FROM film
    JOIN film_category ON film.film_id = film_category.film_id
    JOIN category ON film_category.category_id = category.category_id
    WHERE length < 60
    GROUP BY category.name
    ORDER BY film_count DESC;
    ```

#### Data Manipulation
- **Basic Commands**:
  - Create a new table:
    ```sql
    CREATE TABLE example (...);
    ```
  - Insert new data:
    ```sql
    INSERT INTO example (column1, column2) VALUES (value1, value2);
    ```
  - Update existing records:
    ```sql
    UPDATE example SET column1 = value1 WHERE condition;
    ```
  - Delete records:
    ```sql
    DELETE FROM example WHERE condition;
    ``` 
