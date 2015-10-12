# SQL Column Data Types

## Objectives

1. Learn why specifying column data types in a database matters. 
2. Learn the different types of data you can store in a SQLite database. 

## Why Do Data Types Matter?

We've learned that when we create a table, we include a name for it, and that we also have to define at least one column at that time. We define columns in a CREATE statement by including a name, and a datatype to let SQLite know the kind of data it we will be storing there. The practice of explicitly declaring a type is known as "typing." On the surface, which is really as deep as we need to go right now, types are pretty simple to understand. TEXT stores plain old text, and INTEGER stores numbers. If that was all you knew about types you could get by decently with the rest of the material we are going to cover. For the sake of learning though, let's explore what typing is really about.

We can derive a better understanding of what typing is by answering the question: why is it important that we use typing in our database? Simply put, typing allows us to exercise some level of control over our data. Typing doesn't merely inform our database of the kind of data we plan to store in a column, it restricts it. Say for instance, our age column in our cats table. What do we mean by age? What if we had this:

| name  |  breed  |  age  |
|-------|---------|-------|
| Maru  |  Scottish Fold |   3   |
| Hannah |  Tabby  |  two  |
| Lil' Bub |  American Shorthair  |  5.5  |

Did we intend age to be represented as a whole-number, a word, or a decimal? If I asked you to add up the ages of all the dogs you could simply convert the 'two' to 2 in your head, but your database can't do that. It doesn't have that ability because the logic involved in converting a word into a number would be dense and inefficient. What about different languages? What about different spellings? Capitalization, mis-pellings, what if some people hyphenate forty-two and others write forty two? These are just some top-of-the-head reasons this might start to get crazy. Because databases are designed to store large amounts of data, they are very concerned with storing, accessing, and acting upon that data as efficiently, and normally, as possible.

Typing gives us the ability to perform all kinds of operations, with predictable results. For instance, the ability to perform Math operations like SUM doesn't just depend on everything being an integer of some sort, it expects it. If you tried to SUM (we'll be learning more about SUM, MAX, MIN and other functions later) all of the dogs in the above table, SQLite would actually attempt to convert, or cast, their type to something it can SUM, converting anything it can to an INTEGER and ignoring alpha characters. This can lead to real problems. Without typing, our data might get complicated and messy, and it would be difficult to ask the database questions about large sets of data, maybe impossible.

We're going to adhere strictly to only storing data that fits with the datatype we have given to a particular column.

## Data Types

In SQLite there are five different types we will be dealing with, they are:

```bash
TEXT
NUMERIC
INTEGER
REAL
NONE
```

Different database systems also have different datatypes available, which are important and useful to know whenever you are dealing with those systems. If you're interested in learning more about SQLite's specific implementation of datatypes and affinities, you can learn more about it here. Our goal is to learn about SQL, not every detail of how SQLite itself works internally, so for now I'm going to limit us to just three types. Later on we'll learn about a couple other useful types not listed here. Our types:

### TEXT

Any alphanumeric characters which we want to represent as plain text. The body of this paragraph is text, your name is text, your email address is a piece of text, your height, weight, and age are probably not.

### INTEGER

Anything we want to represent as a whole number. If it's a number, and contains no letter or special characters or decimal points, then we should store it as an integer. If we might use it to perform math, or create a comparison between two different rows in our database, then we definitely want to store it as an integer. If it's just numbers, in general it's not a bad idea to store it as an integer. You might never add two house numbers together, but you might want to sort them numerically. You might want to get the biggest number, not the longest piece of text.

### REAL

Anything that's a plain old decimal like 1.3, or 2.25. SQLite will store decimals up to 15 characters long. So, you could have 1.2345678912345 or 1234.5678912345, but 1.23456789123456789 would only store 1.2345678912345. In other database systems this is called 'double precision.'

With these three types in hand, we are going to be able to work our way through the next several topics, and this whole typing thing is going to quickly be second nature for you.
