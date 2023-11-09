# java-codingchallenge

## Build a RESTful API using Spring Boot with below endpoints:
(use database of your choice, or even in-memory data is fine)

POST `/authors`

PATCH `/authors/:author-name`

GET `/authors/:author-name`

GET `/authors (returns all authors)`

Sample response data from GET /authors/author1
```
{
	"author-name": "author1",
	"author-location": "Sydney"
}
```

POST `/authors/:author/books`

PATCH `/authors/:author/books/:book-name`

GET `/authors/:author/books/:book-name`

GET `/authors/:author/books` (returns all books of this author)

Sample response data from GET /authors/author1/books/book11
```
{
	"book-name": "book11",
	"book-price": 11
	"author-name": "author1"
}
```

## Write a Java program which reads a csv file (e.g. c:\data\authors-books.csv) with below sample data:

```
author-name|author-location|book-name|book-price
author1|Sydney|book11|12
author1|Sydney|book12|23
author2|Melbourne|book21|13
author2|Melbourne|book22|20
author3|Brisbane|book31|15
author3|Brisbane|book32|18
author3|Brisbane|book33|25
author4||book42|25
author5|Perth||20
```


Loads file data into memory and queries api for the authors and books.

- If author is found then updates the location using PATCH /author.
- If author is not found then creates a new author using POST /author
- If book is found then it updates the price using PATCH /books
- If book is not found then it creates the book using POST /books

In the end program archives the csv with datetime stamp (e.g. c:\data\authors-books-20231109-1723.csv), adding success and message fields to each row, e.g.

```
author-name|author-location|book-name|book-price|success|message
author1|Sydney|book11|12|true|
author4||book42|25|false|Author's location not defined
author5|Perth||20|false|Book's name not defined
```

## Acceptance Criteria:
1. Program is able to load csv file, do api calls and update csv with the status
2. Error handling
3. Able to rerun multiple times without any problems if the file is found
4. Logging and unit tests

## Bonus Criteria:
1. Multi-threading for efficiently processing large files, where multiple rows can be processed concurrently without impacting the data
2. File is loaded from a s3 bucket and archived into a archive folder/bucket
