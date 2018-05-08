## Smaller is usually better.
## Simple is good.
## Avoid NULL if possible: The performance improvement from changing NULL columns to NOT NULL is usually
small. If you are planing to index colums, avoid making them nullable.

## Whole Numbers:
## Real Numbers:
## String:
#### VARCHAR: variable-length. MySQL preserves trailing spaces when you store and retrieve values. Must use extra bytes for store length.
#### CHAR: fixed-length, MySQL removes any trailing spaces. Values are padded with spaces as needed for comparisons.
#### TEXT: MySQL can’t index the full length of these data types and can’t use the indexes for
    sorting. The best solution is to avoid using the BLOB and TEXT types unless you really need them.
## ENUM:
#### The biggest downside of ENUM is that the list of strings is fixed, and adding or removing strings requires the use of ALTER TABLE.
## Date and Time:
#### Date: 
#### Timestamp: 
## Bit-Packed Data Types:
## Choosing identifiers:
#### Integer is best choice.
#### UUID:
##### If you use auto increment, you must take langer memory for store ID.
##### If you use auto increment, so easy to user find out the number of record in db and find out other records. That's not safe.
##### Use for distributed database system.
