+++
date = "2021-10-11"
title = "Python - Naming Conventions"
slug = "python-naming-conventions"
description = "Python Naming Conventions"
aliases = "/python-naming-conventions/"
tags = [
    "python",
    "beginner",
    "syntax",
]
categories = [
    "syntax",
    "clean-code",
]
+++

### Table of Contents

1. [Rules](#rules)
1. [The Python Keywords](#the-python-keywords)
1. [Use of Underscores](#use-of-underscores)
1. [Readability Matters](#readability-matters)
1. [Style of Naming Variables](#style-of-naming-variables)
1. [Sample Variable Names](#sample-variable-names)
1. [Reference](#reference)
1. [Further Research](#further-research)

### Rules

Although you are allowed to make up your own names for variables, you must
follow these rules:

```text
1. You cannot use one of Python's keywords as a variable name

2. A variable or function name cannot contain spaces, underscore characters '_'
   can be used instead.

3. The first character must be one of the letters a..z, A..Z, or '_'.

4. After the first character, you may use the letters a..z, A..Z, the digits
   0..0, or '_'.

5. Uppercase and lowercase characters are distinct. This means that the variable
   named 'ItemsOrdered' is not akin to the one named 'itemsordered'.
```

### The Python Keywords

Keywords define the language’s syntax rules and structure, and they cannot be
used as variable names. Python has thirty-something keywords (and every now and
again improvements to Python introduce or eliminate one or two):

Some   | Common   | Python  | Keywords | Include
:---:  | :---:    | :---:   | :---:    | :---:
and    | continue | finally | is       | raise
as     | def      | for     | lambda   | return
assert | del      | from    | None     | True
async  | elif     | global  | nonlocal | try
await  | else     | if      | not      | while
break  | except   | import  | or       | with
class  | False    | in      | pass     | yield

### Use of Underscores

With regards to naming variables, names with leading underscores are intended
to have special meaning in Object-Oriented Programming (OOP).
- The use of '_' implies **protected** attributes (e.g. `_init_`).
- The use of '__' implies **private** attributes (e.g. `__init__`).

### Readability Matters

Because a variable's name should reflect the variable’s purpose, programmers
often find themselves creating names that are made of multiple words. For
example, consider the following variable names:

- coursecode
- studentfullname
- addressline1

Unfortunately, these names are not easily read by the human eye because the
words aren’t separated. Because we can’t have spaces in variable names, we need
to find another way to separate the words in a multi-word variable name and make
it more readable to the human eye.

One way to do this is to use the underscore character to represent a space. For
example, the following variable names are easier to read than those previously
shown:

- gross_pay
- pay_rate
- hot_dogs_sold_today

### Style of Naming Variables

The [rules above](#rules) are called *snake_case* style which is used to name
almost every variable in Python (including functions, lists, dictionaries,
etc.).

On the other hand, there are other styles in Python used for certain variables
namely *PascalCase* and *camelCase*.


*PascalCase* is used to name classes and is written in the following manner:

1. The first character of every word is written in uppercase.
1. There is not a space character.

For example:

- ItemInOrder
- CourseDetail


*camelCase* is used to name methods (functions belong to a class) and is written
in the following manner:

1. The variable name begins with lowercase letters.
1. The first character of the second and subsequent words is written in
  uppercase.
1. There is not a space character.

For example:

- firstName
- payRate

NOTE: This style of naming is called
*[camelCase](https://upload.wikimedia.org/wikipedia/commons/e/ef/CamelCase.svg)*
because the uppercase characters that appear in a name may suggest a camel’s
humps.

### Sample Variable Names

Variable Name | Legal or Illegal?
---           | ---
units_per_day | Legal
dayOfWeek     | Legal
3dGraph       | Illegal. Variable names cannot begin with a digit
June1997      | Legal
Mixture#3     | Illegal. Variable names may only use letters, digits, or underscores

### Reference

Gaddis, T 2021, *Starting Out With Python*, 5th edn, Pearson Education, Inc.

### Further Research

For a comprehensive, complete documentation, please see
*[PEP-8](https://www.python.org/dev/peps/pep-0008/#naming-conventions)*.
