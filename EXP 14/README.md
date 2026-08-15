INFINITE HELLO WORLD USING KEIL 

#include <reg51.h>
#include <stdio.h>

void main(void)
{
    SCON = 0x50;     // UART Mode 1
    TMOD = 0x20;     // Timer1 Mode2
    TH1  = 0xFD;     // 9600 Baud
    TR1  = 1;        // Start Timer1
    TI   = 1;        // Enable first transmission

    while(1)
    {
        printf("Hello World !\n");
    }
}
