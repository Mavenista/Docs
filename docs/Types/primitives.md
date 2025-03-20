---
title: Primitive Data Types
summary: Every programming language has some built-in data types that can be used
date : 2025-10-22
---
# What is a Primitive Data Type?
A primitive data type is a type of data corresponding to the most basic parts of data, that would be inconvenient to break down further. For example, if there were three blocks on top of each other, remove the first two leaving the last block. The last block can be split in half, but it would no longer be a block then. Similarly primitive data types are types of data that is inconvenient to break down.

# Integer Primitive Data Types
Any programming language needs to deal with numbers in some way or another, unlike high level languages like Python there are multiple integer data types. 

### Signed and Unsigned
Each Integer Data Type will have the number of bits it can store as well if it is **signed** or **unsigned**. Signed represents whether the number can be negative and/or positive, for example if there is an **8 bit integer** that is **signed**:

| Bits representing an 8 bit **signed** integer|
| :-----------: |
|**<span style="font-size:100px"><span style="color:blue">- </span>- - - - - - - </span>**|

The bit highlighted in blue will be used to identify if the number is negative or not. However this leaves the **signed 8 bit integer** with only 7 bits that can be used to store numbers. This makes it such that the maximum of a **signed 8 bit integer** is 127 and the minimum will be 128. (Note: 0 counts as a 'positive' number)

The concept behind **unsigned** numbers are such that the number is assumed to never be negative which affords it the entire 8 bits of space.If there is an **unsigned 8 bit integer** the representation would look like:

| Bits representing an 8 bit **unsigned** integer|
| :-----------: |
|**<span style="font-size:100px">- - - - - - - - </span>**|

As there is no need for negatives, all 8 bits are used to represent a positive number ranging from 0 to 255.

### All Integer Data Types

| Bits | Representation         | Signed (**-** is signed) | Minimum                       | Maximum                       |
|------|------------------------|--------------------------|-------------------------------|-------------------------------|
| 1    | Bool                    |                           | 0                             | 1                             |
| 8    | i8                     | **-**                    | -128                          | 127                           |
| 8    | u8                     |                           | 0                             | 255                           |
| 16   | i16                    | **-**                    | -32,768                       | 32,767                        |
| 16   | u16                    |                           | 0                             | 65,535                        |
| 32   | i32                    | **-**                    | -2,147,483,648                | 2,147,483,647                 |
| 32   | u32                    |                           | 0                             | 4,294,967,295                 |
| 64   | i64                    | **-**                    | -9,223,372,036,854,775,808    | 9,223,372,036,854,775,807     |
| 64   | u64                    |                           | 0                             | 18,446,744,073,709,551,615    |
| 32   | f32                  | **-**                    | ~ -3.4 × 10³⁸                 | ~ 3.4 × 10³⁸                  |
| 64   | f64                 | **-**                    | ~ -1.7 × 10³⁰⁸               | ~ 1.7 × 10³⁰⁸                |

(Note: Representation is the data type in Maven, **i** is signed and **u** is unsigned, lastly **f** is float)

### Floats
Floats represent decimals, the default decimal data type in Maven is **f**64, as there is a higher degree of precision versus **f**32


### Which Integer Data Type Should I Use?
If you find yourself in this position, stick with the default integer type (**i**32), unless the following conditions are met:
- The numbers you are working with are bigger than **i**32's maximum (in which case **u**32 or higher will be required [**i**64 if negatives are involved as well])
- The number is smaller than **i**32 and you need to be conservative about how much memory you use
- A function takes a specific argument that is a different Integer Data Type
(note: This is only a general guideline)

### Usage Of Integer Data Types
```
a = 1 // as a is implicitly the default integer, a is an i32
// you can declare integers of a different type using the integer shorthand:
b = 7u64 // b is now a u64 of value 7
c = 3.14 // c is by default an f64
d = 3.14f32

// Other bases for integers (other than 10) are also possible
hexadecimal = 0xf00d
octal = 0o777
binary = 0b1001

// Casting: Scenarios where you need to convert an integer data type into another integer data type
fn foreveri8(number: i8){
    println("I am an i8")
}

// If the function above, seems unfamiliar, it will be covered later
// The function takes a number of type i8

my_num = 168u64

// we can use the 'as' keyword to cast the u64 into an i8:
my_num2 = my_num as i8 // ERROR: 168 is above the maximum of an i8

// Let's try that again
my_num3 = 127u64
my_num4 = my_num3 as i8 // While you may also do: foreveri8(my_num3 as i8), it is considered better practice to keep it in a variable
foreveri8(my_num4) // I am an i8
```


# String/Character Primitive Data Types

### Character Data Type
A Character is any single ascii that will be regarded as a character for example:
```
MyChar = 65Character // 65 in ASCII is 'A'

MyASCII_CODE = MyChar as i32 // MyASCII_CODE now contains the literal ASCII code of 65

printf("The character is: %c\n",MyChar)
//output : The character is A
```
It is not limited to letters and numbers as well, it can also represent various types of ASCII codes for example:

The ASCII code 64 is `@`

As seen in the code example, this type's identifier is `Character`

What if we want a string?

### RawString Data Type

A raw string is essentially a **fixed** size array of `Characters` corresponding to `&i8` in pointer form (this will be covered in more detail later).

You actually already have created a string, when writing `"Hello World"`, this is a string.

Let's try it out in a proper example:
```
x: RawString = "!@(#$($))" // syntax does not apply in strings
y = "I am a star \u{2B50}" // unicode is also supported with `\u{<code>}`
z = "Multi
    line or using \n, did I mention \r is supported too?
    "
```

The Identifier for this type is `RawString`, Currently there is no `String` in the builtins which is planned for later