+++
date = "2021-12-29"
title = "Python Naming Conventions"
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

- [Rules](#rules)
- [The Python Keywords](#the-python-keywords)
- [Use of Underscores](#use-of-underscores)
- [Readability Matters](#readability-matters)
- [Style of Naming Variables](#style-of-naming-variables)
- [Sample Variable Names](#sample-variable-names)
- [Reference](#reference)
- [Further Research](#further-research)

##### Rules

Although you are allowed to make up your own names for variables, you must
follow these rules:

```text
1. You cannot use one of Python's keywords as a variable name

2. A variable or function name cannot contain spaces.

3. The first character must be one of the letters a..z, A..Z, or an underscore
   character '_'.

4. After the first character, you may use the letters a..z, A..Z, the digits
   0..0, or underscore characters.

5. Uppercase and lowercase characters are distinct. This means that the variable
   named 'ItemsOrdered' is not akin to the one named 'itemsordered'.
```

##### The Python Keywords

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

##### Use of Underscores

With regards to naming conventions, names with leading underscores are intended
to be private to a class, and names starting with double underscores may have
special meaning, such as `__init__` or `__add__`.

Therefore, avoid using names that start with double underscores.

##### Readability Matters

Because a variable's name should reflect the variable’s purpose, programmers
often find themselves creating names that are made of multiple words. For
example, consider the following variable names:

- grosspay
- payrate
- hotdogssoldtoday

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

##### Style of Naming Variables

In terms of the above section, using underscore characters to separate words in
a variable name is a popular style among Python programmers. Nonetheless, there
are other popular styles, such as the camelCase naming convention (which is
quite popular among Java programmers). camelCase names are written in the
following manner:

1. The variable name begins with lowercase letters.
1. The first character of the second and subsequent words is written in
  uppercase.

For example, the following variable names are written in camelCase:

- grossPay
- payRate
- hotDogsSoldToday

*NOTE*: This style of naming is called
*[camelCase](https://upload.wikimedia.org/wikipedia/commons/e/ef/CamelCase.svg)*
because the uppercase characters that appear in a name may suggest a camel’s
humps.

##### Sample Variable Names

Variable Name | Legal or Illegal?
--- | ---
units_per_day | Legal
dayOfWeek | Legal
3dGraph | Illegal. Variable names cannot begin with a digit
June1997 | Legal
Mixture#3 | Illegal. Variable names may only use letters, digits, or underscores

##### Reference

Gaddis, T 2021, *Starting Out With Python*, 5th edn, Pearson Education, Inc.

##### Further Research

For a comprehensive, complete documentation, please see
*[PEP-8](https://www.python.org/dev/peps/pep-0008/#naming-conventions)*.
