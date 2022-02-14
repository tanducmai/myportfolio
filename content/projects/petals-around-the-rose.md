+++
date = "2021-10-06"
title = "Petals Around The Rose"
slug = "petals-around-the-rose"
description = "Credit Card Validator"
tags = ['python']
categories = ['python']
aliases = "/petals-around-the-rose/"
+++

#### → [GitHub](https://github.com/tanducmai/petals-around-the-rose)

#### Table of Contents

1. [Aim](#aim)
1. [Introduction](#introduction)
1. [Sample Output](https://github.com/tanducmai/petals-around-the-rose/blob/main/sample-output.pdf)

##### Aim

Write a Pytram that allows a user to play a game called Petals Around the Rose.
The program allows the user to repeatedly guess the answer to the puzzle until
the user chooses to stop guessing/playing. Once the user chooses to stop
guessing, the program will report the user’s and game play statistics to the
screen.

##### Introduction

The name of the game is Petals Around the Rose and the name of the game is
important.  The computer will roll five dice and ask the user to guess the score
for the roll. The score will always be an even number (including zero). The
user’s mission is to work out how the computer calculates the score in order to
become a Potentate of the Rose.

##### Sample Output ([- PDF Version -](https://github.com/tanducmai/petals-around-the-rose/blob/main/sample-output.pdf))

```text
File:         petals.py
Author:       Tan Duc Mai
Email:        tan.duc.work@gmail.com
Description:  Build a mathematical challenging puzzle/game -
              Petals Around the Rose.

Petals Around the Rose
----------------------
The name of the game is 'Petals Around the Rose'. The name of the
game is important. The computer will roll dice and ask you to guess
the score for the roll. The score will always be zero or an even
number. Your mission, should you choose to accept it, is to work out
out the secret and guess correctly four times in a row, you become a
Potentate of the Rose.
----------------------

Would you like to play Petals Around the Rose [y|n]? y
```

![First roll](/images/petals/1.png)

```
Please enter your guess for the roll: 8
Well done! You guessed it!
```

![Second roll](/images/petals/2.png)

```
Please enter your guess for the roll: 8
Well done! You guessed it!
```

![Third roll](/images/petals/3.png)

```
Please enter your guess for the roll: 2
Well done! You guessed it!
```

![Fourth roll](/images/petals/4.png)

```
Please enter your guess for the roll: 8
Congratulations! You have worked out the secret!
Make sure you don't tell anyone!

Do you want to keep playing [y|n]? y
```

![Fifth roll](/images/petals/5.png)

```
Please enter your guess for the roll: 3
No sorry, it's 0 not 3. The score is always even.

Hint: The name of the game is important... Petals Around the Rose. 

Do you give up [y|n]? y

Game Summary
------------
You played 5 games:
 * Correct guesses: 4
 * Incorrect guesses: 1

Maybe you will work it out next time.
Thanks for playing!
```
