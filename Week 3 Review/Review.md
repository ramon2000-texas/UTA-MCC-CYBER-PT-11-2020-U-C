# Day 3 Cheat Sheet - Unit-Terminal

## Grep 

### Problem 1

From grep/problem1.txt, use grep to display all those lines which contain any of the following words in them:
 ```bash 
   the
   that
   then
   those
```

The search should not be sensitive to case. Display only those lines of an input file, which contain the required words.

### Problem 2

Form grep/problem2.txt, use grep to display all those lines that contain the word **the** in them.
The search should NOT be sensitive to case. Display only those lines of the input file that contain the word 'the'.

### Problem 3
From grep/problem3.txt, use grep to **remove** all those lines that contain the word 'that'. The search should NOT be sensitive to case.

### Problem 4

Given the file grep/problem4.txt, with N credit card numbers, each in a new line, your task is to grep out and output only those credit card numbers which have two or more consecutive occurences of the same digit (which may be separated by a space, if they are in different segments). Assume that the credit card numbers will have 4 space separated segments with 4 digits each.

If the credit card number is 1434 5678 9101 1234, there are two consecutive instances of 1 (though) as highlighted in box brackets: 1434 5678 910**1** **1**234

Here are some credit card numbers where consecutively repeated digits have been highlighted in box brackets. The last case does not have any repeated digits:

* 1234 5678 910**1** **1**234
* 2**999** 5178 9101 **22**34
* **9999** 5628 920**1** **1**232
* 8482 3678 9102 1232

Sample Input
```
1234 5678 9101 1234  
2999 5178 9101 2234  
9999 5628 9201 1232  
8482 3678 9102 1232
```

Sample Output
```
1234 5678 9101 1234  
2999 5178 9101 2234  
9999 5628 9201 1232
```

## Sed

### Problem 1

From the sed/problem1-3.txt file transform the first occurrence of the word 'the' with 'this'. The search and transformation should be strictly case sensitive.

### Problem 2 

From the sed/problem1-3.txt file, transform all the occurrences of the word 'thy' with 'your'. The search should be case insensitive, i.e. 'thy', 'Thy', 'tHy' etc. should be transformed to 'your'.

### Problem 3
From the sed/problem1-3.txt file, in each line, highlight all the occurrences of 'thy' by wrapping them up in brace brackets. The search should be case-insensitive.

### Problem 4
From the sed/problem4.txt file, mask the first  digits of each credit card number with an asterisk (i.e., *) and print the masked card number on a new line. Each credit card number consists of four space-separated groups of four digits. For example, the credit card number `1234 5678 9101 1234` would be masked and printed as `**** **** **** 1234`.

Sample Input
```
1234 5678 9101 1234  
2999 5178 9101 2234  
9999 5628 9201 1232  
8888 3678 9101 1232  
```

Sample Output
```
**** **** **** 1234
**** **** **** 2234
**** **** **** 1232
**** **** **** 1232
```
### Problem 5 - CHALLENGING

From the sed/problem5.txt file, with N credit card numbers, each in a new line, your task is to reverse the ordering of segments in each credit card number. Assume that the credit card numbers will have 4 space separated segments with 4 digits each.

If the original credit card number is `1434 5678 9101 1234`, transform it to `1234 9101 5678 1434`.

Useful References: [This particular page on StackOverflow](https://stackoverflow.com/questions/2232200/regular-expression-in-sed-for-masking-credit-card) has a relevant example about sed, groups and backreferences. Here's a [detailed tutorial](https://www.thegeekstuff.com/2009/10/unix-sed-tutorial-advanced-sed-substitution-examples/) covering groups and backreferences. 

Sample Input
```
1234 5678 9101 1234  
2999 5178 9101 2234  
9999 5628 9201 1232  
8888 3678 9101 1232
```

Sample Output
```
1234 9101 5678 1234  
2234 9101 5178 2999  
1232 9201 5628 9999  
1232 9101 3678 8888 
```


## Awk

### Problem 1
You are given a file (awk/problem1.txt) with four space separated columns containing the scores of students in three subjects. The first column contains a single character (A-Z), the student identifier. The next three columns have three numbers each. The numbers are between  and , both inclusive. These numbers denote the scores of the students in English, Mathematics, and Science, respectively.

Your task is to identify those lines that do not contain all three scores for students.

Sample Input
```
A 25 27 50
B 35 75
C 75 78 
D 99 88 76
```

Sample Output
```
Not all scores are available for B
Not all scores are available for C
```

### Problem 2
You are given a file (awk/problem2-4.txt) with four space separated columns containing the scores of students in three subjects. The first column contains a single character (A-Z), the student identifier. The next three columns have three numbers each. The numbers are between 0 and 100, both inclusive. These numbers denote the scores of the students in English, Mathematics, and Science, respectively.

Your task is to identify whether each of the students has passed or failed.
A student is considered to have passed if (s)he has a score 50 or more in each of the three subjects.

Resource: [Conditionals with awk](https://www.thegeekstuff.com/2010/02/awk-conditional-statements/)

Sample Input
```
A 25 27 50
B 35 37 75
C 75 78 80
D 99 88 76
```

Sample Output
```
A : Fail
B : Fail
C : Pass
D : Pass
```

### Problem 3
You are provided a file (awk/problem2-4.txt) with four space-separated columns containing the scores of students in three subjects. The first column, contains a single character (A-Z) - the identifier of the student. The next three columns have three numbers (each between 0 and 100, both inclusive) which are the scores of the students in English, Mathematics and Science respectively.

Your task is to identify the performance grade for each student. If the average of the three scores is 80 or more, the grade is 'A'. If the average is 60 or above, but less than 80, the grade is 'B'. If the average is 50 or above, but less than 60, the grade is 'C'. Otherwise the grade is 'FAIL'.

Resource: [Conditionals with awk](https://www.thegeekstuff.com/2010/02/awk-conditional-statements/)

Sample Input
```
A 25 27 50
B 35 37 75
C 75 78 80
D 99 88 76
```

Sample Output
```
A 25 27 50 : FAIL
B 35 37 75 : FAIL
C 75 78 80 : B
D 99 88 76 : A
```

### Problem 4
You are provided a file (awk/problem2-4.txt) with four space-separated columns containing the scores of students in three subjects. The first column, contains a single character (A-Z) - the identifier of the student. The next three columns have three numbers (each between 0 and 100, both inclusive) which are the scores of the students in English, Mathematics and Science respectively.

Sample Input
```
A 25 27 50
B 35 37 75
C 75 78 80
D 99 88 76 
```

Sample Output
```
A 25 27 50;B 35 37 75
C 75 78 80;D 99 88 76 
```


-------

## Copyright

Trilogy Education Services © 2019. All Rights Reserved.
