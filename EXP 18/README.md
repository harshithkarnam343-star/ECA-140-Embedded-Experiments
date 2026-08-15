PWM USING INTERRUPT IN KEIL

#include <reg51.h>

sbit PWM = P1^0;

unsigned int count = 0;
unsigned char duty = 100;

void timer0_ISR(void) interrupt 1
{
    TH0 = 0xFC;
    TL0 = 0x66;

    count++;

    if(count < duty)
        PWM = 1;
    else
        PWM = 0;

    if(count >=  200)
        count = 0;
}

void main()
{
    TMOD = 0x01;       // Timer 0 Mode 1 (16-bit)
    
    TH0 = 0xFC;
    TL0 = 0x66;        // Approximately 1 ms

    IE = 0x82;         // EA = 1, ET0 = 1

    TR0 = 1;           // Start Timer 0

    while(1);
}
