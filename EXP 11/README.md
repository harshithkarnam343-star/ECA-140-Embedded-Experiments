STUDY OF GPIO AND BIT ADDRESSING IN AT89C51 USIN KEIL

#include <reg51.h>

sbit LED1 = P1^0;
sbit LED2 = P1^1;

void delay()
{
    unsigned int i,j;

    for(i=0;i<16;i++)
        for(j=0;j<10;j++);
}

void main()
{
    while(1)
    {
        LED1 = 1;
        LED2 = 0;
        delay();

        LED1 = 0;
        LED2 = 1;
        delay();
    }
}
