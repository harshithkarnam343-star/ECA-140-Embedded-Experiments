MULTIPLICATION OF TWO 16 BIT BINARY NUMBERS

#include <reg51.h>

void main()
{
    unsigned int num1, num2;
    unsigned long int product;

    while(1)
    {
        num1 = 0x4444;
        num2 = 0xBBBB;

        product = (unsigned long int)num1 * num2;

        P0 = product & 0xFF;
        P1 = (product >> 8) & 0xFF;
        P2 = (product >> 16) & 0xFF;
        P3 = (product >> 24) & 0xFF;
    }
}
