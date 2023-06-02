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

### Q2: Write a C function that calculates the fifth root of a number ###
```
#include <stdio.h>
#include <math.h>

double fifthRoot(double num) 
{
    return pow(num, 1.0 / 5.0);
}
```

### Q3:	Right circular shift
### Write a C function to perform a right circular shift for an unsigned 32 bit integer a given number of times and copy the output to the third argument, and return 0 if OK and 0xFF if not. If number of shifts > 32, in this case copy input to output without doing any shifts.
### Example on 8 bits unsigned integer:

In the figure above,  0x17 (00010111) is circularly shifted right 1 time and the result is 0x8B (10001011), the bit marked in red is moved from right most position to left most position. 

Example of the expected output:
Input = 0xaabbccdd
Number of shifts = 4
---------------------
Output = 0xdaabbccd
Return value = 0

###
