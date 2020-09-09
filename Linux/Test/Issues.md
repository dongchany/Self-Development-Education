# How to check your knowledge
Please do the following question and pass it. *Good luck.*

## Valid Phone numbers
Given a text file file.txt that contains list of phone numbers (one per line), write a one liner bash script to print all valid phone numbers.

You may assume that a valid phone number must appear in one of the following two formats: (xxx) xxx-xxxx or xxx-xxx-xxxx. (x means a digit)

You may also assume each line in the text file must not contain leading or trailing white spaces.

Example:

Assume that file.txt has the following content:
```
987-123-4567
123 456 7890
(123) 456-7890
```
Your script should output the following valid phone numbers:
```
987-123-4567
(123) 456-7890
```

## Tenth Line
Given a text file file.txt, print just the 10th line of the file.

Example:

Assume that file.txt has the following content:
```
Line 1
Line 2
Line 3
Line 4
Line 5
Line 6
Line 7
Line 8
Line 9
Line 10
```
Your script should output the tenth line, which is:
```
Line 10
```
Note:
1. If the file contains less than 10 lines, what should you output?
2. There's at least three different solutions. Try to explore all possibilities.




# Answer
```
Valid phone number

A1: 
egrep "^\([0-9]{3}\) [0-9]{3}\-[0-9]{4}$|^[0-9]{3}\-[0-9]{3}\-[0-9]{4}$" file.txt
```

```
Tenth Line

A1:
awk 'NR==10' file.txt

A2: 
index=0
cat file.txt | while read line
do
    index=$index+1
    if [[ index -eq 10 ]]; then
        echo $line
        break
    fi
done
```