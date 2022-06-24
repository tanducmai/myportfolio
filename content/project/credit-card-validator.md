+++
date = "2021-12-17"
title = "Credit Card Validator"
slug = "credit-card-validator"
thumbnail = "images/python/portfolio/credit-card-valid.png"
description = "Credit Card Validator"
aliases = "/credit-card-validator/"
+++

### → [GitHub](https://github.com/tanducmai/credit-card-validator)

### Introduction

Chances are you have a credit card in your wallet or purse. Credit card numbers
have a 'checksum' built into them, a mathematical relationship between at least
one number and the others. The checksum enables a computer to detect typos, if
not fraudulent numbers, without having to query a database (which can be slow).
Most cards use an algorithm invented by Hans Peter Luhn, a scientist who worked
for IBM. According to Luhn's algorithm, this program will validate if a credit
card number is valid.

### Sample Output and Pseudocode

{{% portfolio image="/images/python/portfolio/credit-card-validator.png"
alt="Project Demo" %}}

According to Luhn’s algorithm, it can be determined if a credit card number is
(syntactically) valid:

```text
prompt for a credit card number (string type)
reverse the number
FOR each digit in number
    double every second digit starting from left
    IF product > 9
        THEN sum each digit of product
    add doubled digits with the undoubled digits
IF the total modulo (%) 10 equates to 0
  THEN output 'valid'
ELSE
  THEN output 'invalid'
```

{{% /portfolio %}}
