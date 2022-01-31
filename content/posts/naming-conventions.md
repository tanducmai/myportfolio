---
draft       : false
author      : Tan Duc Mai
date        : 2021-12-29T05:36:31+10:30
title       : "Python Naming Conventions"
description : "An overview of Python's naming best practices described in PEP-8"
slug        : "python-naming-conventions"
series      : ["Introduction to Python"]
categories  : [
    "syntax",
    "clean-code",
]
tags        : [
    "python",
    "beginner",
]
---

## An Introduction to Clean Code in Python

Although you are allowed to make up your own names for variables,you must follow
these rules:

1. You cannot use one of Python's keywords as a variable name.

2. A variable name cannot contain spaces.

3. The first character must be one of the letters a..z, A..Z, or an underscore
   character ( __ ).

4. After the first character, you may use the letters a..z, A..Z, the digits
   0..0, or underscore characters.

5. Uppercase and lowercase characters are distinct. This means that the variable
   name ```ItemsOrdered``` is not akin to ```itemsordered```.

---

To make variables more human readable, we can use:

1. regular_variables

   ```python3
   names = 'Python'
   job_title = 'Software Engineer'
   populated_countries_list = []
   ```


For a comprehensive, complete documentation, please go to
[documentation](https://www.python.org/dev/peps/pep-0008/).
