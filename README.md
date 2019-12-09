```python

input5_value = input("Enter the string:")


chars = 256 

def reversepal(inp):
    
    repeat = [0] * 256
#     To find char is present in odd index 
    odd = 0
    
    for i in range(len(inp)):
#   Calculate no of time char repeated 
        repeat[ord(inp[i])] = repeat[ord(inp[i])] + 1
    
# To find string can be rearrange into palindrome or not
    for i in range(chars):
#         why "& 1" in chars list except input char remaining element are 0
#         To make if condition false we use and operator 0 & 1 = 0(false)

        if(repeat[i] & 1):
            odd += 1
#             If odd char is more then one time repeated it cant be a palindrome 
        if(odd > 1):
            return "palindrome is not possible"
    return "palindrom is posible "
      
   
reversepal(input5_value)
```
