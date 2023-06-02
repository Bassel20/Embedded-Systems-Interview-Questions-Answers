# C Coding questions for Embedded SW Engineers #

## Questions & Answers ##

### Q1: Write a C function that counts the number of ones in the binary representation of an integer number ###
```
#include <stdio.h>

int countOnes(int num) 
{
    int count = 0;

    while (num != 0) 
    {
        if (num & 1) count++;
        num >>= 1; // Shift right by 1 bit
    }

    return count;
}
```

### Q2: 4th Bit ### 
Digits within an integer go from least significant to most significant from right to left. For instance, in a decimal number the ones digit is less significant than the tens digit. Given a decimal number, convert it to binary and then determine the value of of the 4th least significant bit (1 or 0).

For example 23 = (10111) the value of the 4th index from the right in binary representation is 0.

Write a C function *fourthbit()*. The function takes in an integer and it must return a 0 or 1 matching the 4th least significant digit in the binary representation of num.

**Solution 1:**
```
int fourthbit(int num){
    int r;
    for(int i=0; i<4; i++){
        r = num % 2;
        num = num / 2;
    }
    return r;
}
```
**Solution 2:**
```
int fourthbit(int num){
    return (num >> 3) & 1;
}
```

### Q3: Write a C function that calculates the fifth root of a number ###
**Solution:**
```
#include <stdio.h>
#include <math.h>

double fifthRoot(double num) 
{
    return pow(num, 1.0 / 5.0);
}
```

### Q4:	Right circular shift
Write a C function to perform a right circular shift for an unsigned 32 bit integer a given number of times and copy the output to the third argument, and return 0 if OK and 0xFF if not. If number of shifts > 32, in this case copy input to output without doing any shifts.
In the figure below,  0x17 (00010111) is circularly shifted right 1 time and the result is 0x8B (10001011).

![Alt_text](https://github.com/Bassel20/Embedded-Systems-Interview-Questions-Answers/blob/main/Figures/circular_shift.png)
**Example:**
```
Input = 0xaabbccdd 
Number of shifts = 4
--------------------
Output = 0xdaabbccd
Return value = 0
```
**Solution:**
```
unsigned char u8RightCircularShift (unsigned int u32InputNumber, int u8NumberOfShifts, unsigned int *pu32Output) 
{
    if (u8NumberOfShifts > 32)
    {
        *pu32Output = u32InputNumber;
        return 0xff;
    }
    while(u8NumberOfShifts) 
    {
        u32InputNumber = u32InputNumber << 31 | u32InputNumber >> 1;
        u8NumberOfShifts --;
    }
    *pu32Output = u32InputNumber;
    return 0;
}
```

### Q5: Last and Second-Last
Given a string, create a new string made up of its last two letters, reversed and separated by a space.

**Example:**
```
input: ‘bat’ 
output: ‘t a’. 
```
**Solution:**
```
char* lastLetters (char* x) {
    int len = strlen(x);
    if (len < 2){
        return NULL; // not enough characters in string
    }
    char* result = malloc(3); // allocate space for result and null terminator
    if (result == NULL) {
        return NULL; // malloc failed
    }
    result[0] = x[len - 1]; // last character
    result[1] = ' ';
    result[2] = x[len - 2]; // second to last character
    result[3] = '\0'; // null terminator
    return result;
}
```

### Q6: Values between two 8-bit unsigned integers in descending order inclusive
Write a C function to return an array containing the values between two 8-bit unsigned integers in descending order inclusive. The function takes 2 values (LowerValue, UpperValue), it shall determine the values in between, and then arrange the sequence in descending order including the upper and lower values. If LowerValue is greater than UpperValue, return an array of 2 elements, both containing value = “0xFF”
**Example:**
```
Input:
LowerValue = 2
UpperValue = 5
--------------------------
Output:
Output array = 5, 4, 3, 2
Output array size = 4
```
**Solution:**
```
int* ptintReverseInclusive(int lower, int upper, int* result_size) {
    if (lower >= upper) 
    { // invalid input, return array of 2 elements with value 0xFF
        int* result = (int*) malloc(2 * sizeof(int));
        result[0] = 0xFF;
        result[1] = 0xFF;
        *result_size = 2;
        return result;
    } 
    else 
    { // valid input, calculate array size and allocate memory
        int array_size = upper - lower + 1;
        int* result = (int*) malloc(array_size * sizeof(int));
        *result_size = array_size;
        // fill the array with values in descending order
        for (int i = 0; i < array_size; i++) {
            result[i] = upper - i;
        }
        return result;
    }
}

```

