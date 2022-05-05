+++
author = "WNO-IQ"
title = "Chapter 16: Data representation"
date = "2021-12-03"
description = "我的A2 计算机科学笔记"
tags = [
    "Notes",
    "Study"
]
keywords = ["CIE","Alevel","A2","Computer Science","Notes"]
categories = [
    "A2-CS-notes"
]

+++

# Chapter 16: Data representation

## Data types

### Built-in data types

- the `programming language` defines the range of possible values that can be assigned to a variable when its type has been chosen.
- the programming language defines the operations that are available for manipulating values assigned to the variable.

### User-defined data types

### Non-composite data types

- does not involve a reference to another data type

### Enumerated data type

- a non-composite user-defined data type for which the definition identifies all possible values
- a pseudocode example
  ![](/cs-note-img/Pastedimage20211123192324.png)

### Composite user-defined data types

- Record
  - collection of related items which may have different data types
- Array
  - (Indexed) collection of items with the same data type
- List
  - (Indexed) collection of items that can have different data types
- Set
  - stores a finite number of different values that have no order // supports mathematical operations
- Class/Structure
  - Gives the properties and methods for an object

### Pointer data type

### Set data type

- It contains a collection of data values.
- There is no organisation of the data values within the set.
- Duplicate values are not allowed.

---

## File organisation

- the content is stored using a specific binary code
- A file is either a text file or a binary file
- The organisation of a binary file is based on the concept of a record
- A file contains records and each record contains fields

### Serial files

- In a serial file each new record is simply appended to the file so that the only ordering in the file is the time order of data entry.

### Sequential(顺序的) files

- records that are ordered
- there has to be a key field for which the values are unique and sequential but not necessarily consecutive

### Direct-access files(Random-access files)

- only that the access can be to any record in the file without sequential reading of the file
- A separate index file is created which has two fields per record. The first field has the key field value and the second field has a value for the position of this key field value in the main file.

#### Hashing algorithm

- do not have any order
- different key field values can produce the same remainder and therefore the same address in the file

### File access

---

## Real number

### Floating-point

- **Floating-point representation**: a representation of real numbers that stores a value for the mantissa and a value for the exponent
- example:
  ![](cs-note-img/Pastedimage20211116135647.png)

### Fixed-point representations

- ![](cs-note-img/Pastedimage20211116134751.png)

### Precision

- the total number of bits to be used and decide on the split between those representing the mantissa and those representing the exponent
- `increasing` the number of bits for the `mantissa` would give `better precision` for a value
- leave `fewer` bits for the `exponent`, which `reduces the range` of possible values

### Normalisation

- For a positive number, the bits in the mantissa are shifted left until the most significant bits are 0 followed by 1
- For a negative number until the most significant bits are 1 followed by 0

### Conversion of representations

- Binary floating number to denary
  ![](cs-note-img/Pastedimage20211116141202.png)
  ![](cs-note-img/Pastedimage20211116141219.png)

- Denary to binary floating number
  - ![](cs-note-img/Pastedimage20211116141510.png)
  - ![](cs-note-img/Pastedimage20211116141516.png)
  - ![](cs-note-img/Pastedimage20211116141449.png)

### Problems with using floating-point numbers

- Floating-point numbers are used in extended mathematical procedures involving repeated calculations.
- Rounding errors
  - if calculations are repeated enough times
  - To avoid, you should increase the precision
- Range of numbers that can be stored
  - overflow error condition
  - underflow error condition
