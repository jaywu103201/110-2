# 四位數常駐
```
/* Define shift register pins used for seven segment display */
/*https://swf.com.tw/?p=715*/
#define LATCH_DIO D15   
#define CLK_DIO D14
#define DATA_DIO 2
#define BUTTON1 BT1
#define BUTTON2 BT2
#define BUTTON3 BT3
#define BUTTON4 BT4
#define BUTTON_A1 A1
#define BUTTON_A2 A2
#define BUTTON_A3 A3
/* Segment byte maps for numbers 0 to 9 , A, b , C,d,E,F*/
const byte SEGMENT_MAP[] = {0x79,0x3f,0x3f,0x6d};
/* Byte maps to select digit 1 to 4 */
const byte SEGMENT_SELECT[] = {0xFE,0xFD,0xFB,0xF7};
void setup ()
{
/* Set DIO pins to outputs */
pinMode(LATCH_DIO,OUTPUT);
pinMode(CLK_DIO,OUTPUT);
pinMode(DATA_DIO,OUTPUT);
}
/* Main program */
void loop()
{
  int i;
  while(i<4)
  {
    unsigned long int starttime=millis(); 
    while((millis()-starttime) <= 1000) 
    {
      for(int j=0; j<4; j++)
      {  
        WriteNumberToSegment((i+j)%4 , i+j);
        delay(3);
      }
    }
    i += 4;
  }
}

/* Write a decimal number between 0 and 9 to one of the 4 digits of the display */
void WriteNumberToSegment(byte Segment, byte Value)
{
digitalWrite(LATCH_DIO,LOW);
shiftOut(DATA_DIO, CLK_DIO, MSBFIRST, SEGMENT_MAP[Value]);
shiftOut(DATA_DIO, CLK_DIO, MSBFIRST, SEGMENT_SELECT[Segment] );
digitalWrite(LATCH_DIO,HIGH);
}


```


# 八位數跑馬燈
```
/* Define shift register pins used for seven segment display */
/*https://swf.com.tw/?p=715*/
#define LATCH_DIO D15   
#define CLK_DIO D14
#define DATA_DIO 2
#define BUTTON1 BT1
#define BUTTON2 BT2
#define BUTTON3 BT3
#define BUTTON4 BT4
#define BUTTON_A1 A1
#define BUTTON_A2 A2
#define BUTTON_A3 A3
/* Segment byte maps for numbers 0 to 9 , A, b , C,d,E,F*/
const byte SEGMENT_MAP[] = {0x66,0x3f,0x67,0x3f,0x79,0x3f,0x3f,0x6d};
/* Byte maps to select digit 1 to 4 */
//const byte SEGMENT_SELECT[] = {0xFE,0xFD,0xFB,0xF7};/*右>左*/
const byte SEGMENT_SELECT[] = {0xF7,0xFB,0xFD,0xFE};/*左>右*/
void setup ()
{
/* Set DIO pins to outputs */
pinMode(LATCH_DIO,OUTPUT);
pinMode(CLK_DIO,OUTPUT);
pinMode(DATA_DIO,OUTPUT);
}
/* Main program */
void loop()
{
  int i;
 
  while(i<8)
  {
    WriteNumberToSegment(i%4 , i);
    i++;
    delay(500);
  }

}
/* Write a decimal number between 0 and 9 to one of the 4 digits of the display */
void WriteNumberToSegment(byte Segment, byte Value)
{
digitalWrite(LATCH_DIO,LOW);
shiftOut(DATA_DIO, CLK_DIO, MSBFIRST, SEGMENT_MAP[Value]);
shiftOut(DATA_DIO, CLK_DIO, MSBFIRST, SEGMENT_SELECT[Segment] );
digitalWrite(LATCH_DIO,HIGH);
}


```
