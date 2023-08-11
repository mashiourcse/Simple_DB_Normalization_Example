# Simple_DB_Normalization_Example
Simple Database Normalization Example

CREATE DATABASE normalization_practice;
use normalization_practice;

CREATE TABLE Authors (
    author_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    birth_year INT
);

CREATE TABLE Books (
    book_id INT PRIMARY KEY,
    title VARCHAR(100),
    publication_year INT
);

CREATE TABLE AuthorBooks (
    author_id INT,
    book_id INT,
    FOREIGN KEY (author_id) REFERENCES Authors(author_id),
    FOREIGN KEY (book_id) REFERENCES Books(book_id)
);


SELECT * FROM Authors;
SELECT * FROM Books;
SELECT * FROM AuthorBooks;

INSERT INTO Authors (author_id, first_name, last_name, birth_year)
VALUES
    (1, 'John', 'Smith', 1980),
    (2, 'Jane', 'Doe', 1992);

INSERT INTO Books (book_id, title, publication_year)
VALUES
    (101, 'The Adventure', 2005),
    (102, 'Mystery Unveiled', 2010),
    (103, 'Lost in Time', 2018),
    (104, 'Secrets Revealed', 2015);

INSERT INTO AuthorBooks (author_id, book_id)
VALUES
    (1, 101),
    (1, 102),
    (1, 104),
    (2, 103);
    
SELECT Books.book_id, Authors.first_name, Books.title FROM Books INNER JOIN Authors INNER JOIN AuthorBooks ON AuthorBooks.author_id = Authors.author_id AND AuthorBooks.book_id = Books.book_id; 
