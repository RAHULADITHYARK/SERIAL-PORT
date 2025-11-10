
# Serial Transfer of Single Byte / Character using 8051 (Keil)

## AIM
To write and execute an Embedded C Program for Serial Transfer of Single Byte / Character using 8051 in Keil.

## APPARATUS REQUIRED
- Personal Computer  
- Keil µVision Software  

## PROGRAM

### (i) Serial Port Transfer a Single Character

```scilab
ORG 00H 
MOV TMOD, #20H 
MOV TH1, #0FCH 
MOV SCON, #40H 
SETB TR1 
MOV SBUF, #'B' 
WAIT:JNB TI, WAIT
CLR TI 
END
```
```c
#include<reg51.h>
void main(void)
{
TMOD=0X20; //TIMER 1, MODE 2
TH1=0XFA;
SCON=0X50;
TR1=1;
while(1)
{
SBUF='B';
while(TI==0);
T1=0;
}
}
```
### (ii) Serial Port to Transfer a Message

```scilab
ORG 00H
MOV TMOD,#20H
MOV TH1,#0FCH
MOV SCON,#40H
SETB TR1
MOV B,30H
MOV DPTR,#4500H
AGAIN:MOVX A,@DPTR
MOV SBUF,A
WAIT:JNB TI,WAIT
CLR TI
INC DPTR
DJNZ B,AGAIN
END
```
```c
#include<reg51.h>
void main(void)
{
unsigned char msg[]="RAHUL ADITHYA R K";
unsigned char i;
TMOD=0X20;//TIMER 1,MODE 2
TH1=0XFC;
SCON=0X40;
TR1=1;
for (i=0; i<17;i++)
{
SBUF= msg[i];
while(TI==0);
TI=0;
}
while(1);
}
```
### OUTPUT:

<img width="2630" height="1185" alt="image" src="https://github.com/user-attachments/assets/93e65800-aa35-4feb-95a1-c03f87c1586e" />

<img width="2755" height="1350" alt="image" src="https://github.com/user-attachments/assets/b03d00ab-6837-4445-94a5-9195878aa574" />

### RESULT:
Thus the Serial transfer of Single Byte / Character using 8051 KEIL was done and shown the output.
