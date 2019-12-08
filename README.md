### 1. Write a program that prints the numbers from 1 to N. 
But, for **multiples of three,  print “Fizz”**instead of the number and for the **multiples of five print “Buzz”**. 
For numbers which are **multiples of both three and five print “FizzBuzz”**.

Below is an example:

Input: N = 17
Output:
1,2,Fizz,4,Buzz,Fizz,7,8,Fizz,Buzz,11,Fizz,13,14,FizzBuzz,16,17


```python
#Input the range (number time loop need to executed):

input1_value = int(input("Enter the range value: "))

for input1_value in range(1, input1_value+1):
    
#     We need to check first any number divisble by both 3 and 5 or 15(5*3) should print("FizzBuzz")
    if input1_value % 15 == 0:
        print("FizzBuzz")
#     If a number multiple of 3 can also divisible by 3,
#     So if any value divisible by only 3 print "Fizz"
    elif input1_value % 3 == 0:
        print("Fizz")
#     If a number multiple of 5 can also divisible by 5,
#     So if any value divisible by only 5 print "Buzz"
    elif input1_value % 5 == 0:
        print("Buzz")
    else:
#     If number is not divisible by 3 or 5 or 15 print input value as like 
        print(input1_value)
```

    Enter the range value: 20
    1
    2
    Fizz
    4
    Buzz
    Fizz
    7
    8
    Fizz
    Buzz
    11
    Fizz
    13
    14
    FizzBuzz
    16
    17
    Fizz
    19
    Buzz


### 2.  Given an array **print all the numbers that are repeating** in it and the number of times they are repeating.

Below is an example:

Input: [1, 2, 3, 5, 8, 4, 7, 9, 1, 4, 12, 5, 6, 5, 2, 1, 0, 8, 1]
Output:
1 - 4
2 - 2
5 - 3
8 - 2
4 - 2

Note: The final order of output need not be the same as above. The **number after the dash(-)** is the **repeating count**



```python
# Uncomment below pip commend to install collections in your system 
# !pip install collections-extended
import collections

# Enter the value into list by separating comma(,) for one value between another value
# sample input: (copy and paste) 1, 2, 3, 5, 8, 4, 7, 9, 1, 4, 12, 5, 6, 5, 2, 1, 0, 8, 1

input2_value  = list(map(int,input('Enter the value:').split(',')))

# Counters are accessed just like dictionaries
# Here we are collecting duplicate value as key and no of repetition as keyvalue

for item, count in collections.Counter(input2_value).items():
    if count > 1:
        print("{}-{} ".format(item,count))

```

    Enter the value: 1, 2, 3, 5, 8, 4, 7, 9, 1, 4, 12, 5, 6, 5, 2, 1, 0, 8, 1
    1-4 
    2-2 
    5-3 
    8-2 
    4-2 


### 3. Given an object/dictionary, containing names as keys and amount_paid by each of them as values, write a function that takes such an object as input and calculates the total sum paid by them together.

Below is an example:

Input: {"Rick": 85, "Amit": 42, "George": 53, "Tanya": 60, "Linda": 35}
Output: 275 


```python
input3_value = {}
# Input total number person/object to calculate the sum 

for totnum in range(0,int(input('Input the total number :'))):
    
#      Update the name and amount to input3_value dict by collecting from user
#      Enter the details one by one by Use ":" symbol to separate name and amount from input 
   
    name, amount = input('Enter name & score separated by ":" ').split(":")
    input3_value[name] = int(amount)
    
# Display total amount paid 
print("Total amount paid :",sum(input3_value.values()))
```

    Input the total number :5
    Enter name & score separated by ":" "Rick": 85
    Enter name & score separated by ":" "Amit": 42
    Enter name & score separated by ":" "George": 53
    Enter name & score separated by ":"  "Tanya": 60
    Enter name & score separated by ":" "Linda": 35
    Total amount paid : 275


### 4. Develop a program to calculate the total and individual player scores in a cricket match. 
Input would be an array with the index representing the ball number and the value representing the runs scored of that ball.

Assumptions/Tips:
1.	No Extras bowled
2.	Batsman has to be rotated after ever over
3.	Bowler can bowl any number of overs
4.	Assume Batsman 1 is on strike for the first ball.


Below is an example:

Input : [1,2,0,0,4,1,6,2,1,3];

Output:
Total Score: 20
Batsman 1 Score : 4 (1 + 3)
Batsman 2 Score : 16 (2 + 4 + 1 + 6 + 2 + 1)


```python

# Input score one by one by use "," to separate
input4_value = list(map(int, input("Total score:  ").split(",")))
# Create a variable to store  batsman score
batsman1_score = 0
batsman2_score = 0
# Create a list to store batsman score list 
batman1_score_list = []
batman2_score_list = []
# Create a variable to identify batsman strike
current_strike = [1]

for i in range(len(input4_value)):
#     Init and check current strike
        if current_strike[0] == 1:
#             If batsman hit 1 or 3 run
                if (input4_value[i] in (1, 3)):
#                     Update batsman score
                    batsman1_score += input4_value[i]
#                     Update batman score list
                    batman1_score_list.append(input4_value[i])
#                     current strike change 
                    current_strike[0]=2
#                     Current strike remind same when batsman hit 1 or 3 in last ball of the over
                    if((i+1)%6==0):
                        current_strike[0]=1
            
#             If batsman hit 0 or 2 or 4 or 6 run                              
                elif (input4_value[i] in (4, 6, 2,0)):
#                     Update batsman score     
                    batsman1_score += input4_value[i]
#                     Update batman score list
                    batman1_score_list.append(input4_value[i])
#                     current strike remind same 
                    current_strike[0]=1
#                     Current strike change when batsman hit 2 or 6 or 4 or 0 in last ball of the over

                    if((i+1)%6==0):
                         current_strike[0]=2
                            
                else:
                    pass #To end elif(switch case)statement else block used to pass 
            
        else:
#     Init and check current strike  
            if current_strike[0] == 2:
#             If batsman hit 1 or 3 run   
                if (input4_value[i] in (1, 3)):
#                     Update batsman score      
                    batsman2_score += input4_value[i]
#                     Update batman score list
                    batman2_score_list.append(input4_value[i])
#                     current strike change
                    current_strike[0]=1
#                     Current strike remind same when batsman hit 1 or 3 in last ball of the over
                    if((i+1)%6==0):
                         current_strike[0]=2
#             If batsman hit 0 or 2 or 4 or 6 run 
                elif (input4_value[i] in (4, 6, 2,0)):
#                     Update batsman score     
                    batsman2_score += input4_value[i]
#                     Update batman score list
                    batman2_score_list.append(input4_value[i])
#                     current strike remind same 
                    current_strike[0]=2
#                     Current strike change when batsman hit 2 or 6 or 4 or 0 in last ball of the over

                    if((i+1)%6==0):
                          current_strike[0]=1
                
                else:
                        pass #To end elif(switch case)statement else block used to pass 
                    
#  Display Total score                   
print("Total Score: ",sum(input4_value)) 
# Display the batsman 1 score
print("Batsman 1 Score : ",batsman1_score, end=" ");print("(", end=" ")

print(*batman1_score_list, sep = " + ",end=" ");print(")")
# Display the batsman 2 score
print("Batsman 2 Score : ",batsman2_score, end=" ");print("(", end=" ")

print(*batman2_score_list, sep = " + ",end=" ");print(")")
```

    Total score:  1,2,0,0,4,1,6,2,1,3
    Total Score:  20
    Batsman 1 Score :  4 ( 1 + 3 )
    Batsman 2 Score :  16 ( 2 + 0 + 0 + 4 + 1 + 6 + 2 + 1 )



```python

```
