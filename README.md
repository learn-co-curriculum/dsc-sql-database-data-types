# SQL Column Data Types

## Overview 
In this lesson, we'll cover why specifying data types in a database matters as well as the different types of data you can store in a SQL database.

## Objectives

1. Explain how specifying column data types in a database restricts the data entered and allows for operations to be performed with predicatable results
2. List five different types of data you can store in a SQLite database. 
3. Define three specific SQLite database types: Text, Integer, and Real.

## Why Do Data Types Matter?

We've learned that when we create a table, we need to include a name for it as well as define at least one column. We define columns in a CREATE statement by including a name, and a datatype to let SQLite know the kind of data it we will be storing there. The practice of explicitly declaring a type is known as "typing." 

Why is it important that we use typing in our database? Simply put, typing allows us to exercise some level of control over our data. Typing not only informs our database of the kind of data we plan to store in a column but it also restricts it. For instance, look at the age column below in our cats table. What do we mean by age? What if we had this:

| name  |  breed  |  age  |
|-------|---------|-------|
| Maru  |  Scottish Fold |   3   |
| Hannah |  Tabby  |  two  |
| Lil' Bub |  American Shorthair  |  5.5  |

Did we intend age to be represented as a whole-number, a word, or a decimal? If we asked you to add up the ages of all the dogs you could simply convert the 'two' to 2 in your head, but your database can't do that. It doesn't have that ability because the logic involved in converting a word into a number would be dense and inefficient. What about different languages? What about different spellings? Capitalization, typos, or different hypenation conventions? These are just some reasons this might start to get crazy. In other words, because databases are designed to store large amounts of data, they are very concerned with storing, accessing, and acting upon that data as efficiently, and normally, as possible.

Typing gives us the ability to perform all kinds of operations with predictable results. For instance, the ability to perform Math operations like SUM - i.e. summing integers - doesn't just depend on everything being an integer of some sort but would also expect it. If you tried, for example,  to SUM all of the dogs in the above table, SQLite would actually attempt to convert, or cast, their type to something it can SUM. It would try to convert anything it can to an INTEGER and ignore alpha characters. This can lead to real problems. Without typing, our data might get complicated and messy, and it would be difficult to ask the database questions about large sets of data.

We're going to adhere strictly to only storing data that fits with the datatype we have given to a particular column.

## Data Types

Different database systems also have different datatypes available, which are important and useful to know whenever you are dealing with those systems. In SQLite there are five different types we will be dealing with, they are:

```bash
TEXT
NUMERIC
INTEGER
REAL
BLOB
```

For now we'll cover just three types, and later on we'll also learn about a couple other useful types not listed here. Our types:

### TEXT

Any alphanumeric characters which we want to represent as plain text. The body of this paragraph is text. Your name is text. Your email address is a piece of text. Your height, weight, and age, however, are probably not.

### INTEGER

Anything we want to represent as a whole number. If it's a number and contains no letter or special characters or decimal points then we should store it as an integer. If we use it to perform math or create a comparison between two different rows in our database, then we definitely want to store it as an integer. If it's just numbers, it's generally not a bad idea to store it as an integer. You might never add two house address numbers together, but you might want to sort them numerically. For example in the preceding case, you might want to get the biggest number and not the longest piece of text.

### REAL

Anything that's a plain old decimal like 1.3 or 2.25. SQLite will store decimals up to 15 characters long. You can store 1.2345678912345 or 1234.5678912345, but 1.23456789123456789 would only store 1.2345678912345. In other database systems this is called 'double precision.'

With these three types in hand, we are going to be able to work our way through the next several topics, and this whole typing concept is going to quickly be second nature for you.
