SERIAL INTERRUP USING UART IN KEIL

#include <reg51.h> #include <stdio.h>

void serial_ISR(void) interrupt 4 { char ch;

if(RI)
{
    RI = 0;
    ch = SBUF;

    printf(">>> INTERRUPT RECEIVED: ");
    printf("%c\n", ch);
}
}

void delay(void) { unsigned int i;

for(i = 0; i < 50000; i++);
}

void main(void) { SCON = 0x50; // UART Mode 1, 8-bit, REN enabled TMOD = 0x20; // Timer 1 Mode 2, auto-reload TH1 = 0xFD; // Baud rate 9600 TR1 = 1; // Start Timer 1

IE = 0x90;         // EA = 1, ES = 1 (enable serial interrupt)

TI = 1;            // Enable printf transmission

while(1)
{
    printf("Hello World\n");
    delay();
}
}
