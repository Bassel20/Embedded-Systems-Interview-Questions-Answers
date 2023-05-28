# C Coding questions for Embedded SW Engineers #

## Questions & Answers##

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
