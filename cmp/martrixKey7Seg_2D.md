```
#define LATCH_DIO D15   
#define CLK_DIO D14
#define DATA_DIO 2

//char KeyValue[]={'1','2','3','A','4','5','6','B','7','8','9','C','*','0','#','D'};
/*const byte KeyMap[]={0x06,0x5b,0x4F,0X77,
                     0x66,0x6D,0x7D,0x7c,
                     0x27,0X7F,0X67,0x39,
                     0x79,0x3F,0x71,0X5e, 0};*/
const byte KeyMap[4][4]={{0x06,0x5b,0x4F,0X77},
                         {0x66,0x6D,0x7D,0x7c},
                         {0x27,0X7F,0X67,0x39},
                         {0x79,0x3F,0x71,0X5e}};                     
const byte SEGMENT_SELECT[] = {0xFE,0xFD,0xFB,0xF7};
byte Row=0, Col=0;

void setup() {
  // put your setup code here, to run once:
  pinMode(LATCH_DIO,OUTPUT);
  pinMode(CLK_DIO,OUTPUT);
  pinMode(DATA_DIO,OUTPUT);
  pinMode(10, INPUT); //R1: S1,S2,S3,S4 (1,2,3,A)                                   
  pinMode(11, INPUT_PULLUP); //R2: S5,S6,S7,S8 (4,5,6,B)
  pinMode(12, INPUT_PULLUP); //R3: S9, S10, S11,S12 (7,8,9,C)
  pinMode(13, INPUT_PULLUP); //R4: (*,0,#,D) //*->E, #->F
  pinMode(A0, OUTPUT); //A1, C1: S1,S5,S9 (1,4,7,*)
  pinMode(A1, OUTPUT); //A2, C2: S2,S6,S10 (2,5,8,0)
  pinMode(A2, OUTPUT); //A3, C3: S3,S7,S11 (3,6,9,#)
  pinMode(A3, OUTPUT); //A4, C4, S4,S8,S12 (*,0, #,D)
  //Pin left to right :R1 R2 R3 R4 C1 C2 C3 C4
  for(int i=0; i<4; i++){
    digitalWrite(LATCH_DIO,LOW);
    shiftOut(DATA_DIO, CLK_DIO, MSBFIRST, 0);
    shiftOut(DATA_DIO, CLK_DIO, MSBFIRST, SEGMENT_SELECT[i] );
    digitalWrite(LATCH_DIO,HIGH);
  }
    ;
} 

void loop() {
  // put your main code here, to run repeatedly:
  static int keypressedcount=0;
  byte keyindex=0;
  //if key is pressed in the first round scan, 
  //then call keyscan() again to check if the key pressed in first round is actually pressed 
  if(keyscan()==true) 
  {
    keyindex=(Row-1)*4+Col-1;
    delay(5);
    if ((keyscan()==true) && (keyindex==(Row-1)*4+Col-1))
    {
      digitalWrite(A0,LOW);
      digitalWrite(A1,LOW);
      digitalWrite(A2,LOW);
      digitalWrite(A3,LOW);
      delayMicroseconds(100);
      while( (digitalRead(10)==LOW) || (digitalRead(11)==LOW)||(digitalRead(12)==LOW) || (digitalRead(13)==LOW))
        ;  
      WriteNumberToSegment(3, KeyMap[Row-1][Col-1]);  
    }
  } 
}

bool keyscan( )
{
  Row=0;Col=0;
  bool keypressed = false;
  //scan col1
  digitalWrite(A0, LOW);
  digitalWrite(A1, HIGH);
  digitalWrite(A2, HIGH);
  digitalWrite(A3, HIGH);
  delayMicroseconds(100);
  //Read keys in row.1
  if(digitalRead(10)==LOW)
  {
      digitalWrite(A0, HIGH);
      Col=1;Row=1;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.2
  if(digitalRead(11)==LOW)
  {
      digitalWrite(A0, HIGH);
      Col=1;Row=2;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.3
  if(digitalRead(12)==LOW)
  {
      digitalWrite(A0, HIGH);
      Col=1;Row=3;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.4
  if(digitalRead(13)==LOW)
  {
       digitalWrite(A0, HIGH);
      Col=1;Row=4;
      keypressed = true;
      return(keypressed);
  }
  //scan col2
  digitalWrite(A0, HIGH);
  digitalWrite(A1, LOW);
  digitalWrite(A2, HIGH);
  digitalWrite(A3, HIGH);
  delayMicroseconds(100);
  //Read keys in row.1
  if(digitalRead(10)==LOW)
  {
      digitalWrite(A1, HIGH);
      Col=2;Row=1;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.2
  if(digitalRead(11)==LOW)
  {
      digitalWrite(A1, HIGH);
      Col=2;Row=2;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.3
  if(digitalRead(12)==LOW)
  {
      digitalWrite(A1, HIGH);
      Col=2;Row=3;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.4
  if(digitalRead(13)==LOW)
  {
      digitalWrite(A1, HIGH);
      Col=2;Row=4;
      keypressed = true;
      return(keypressed);
  }
  //scan col3
  digitalWrite(A0, HIGH);
  digitalWrite(A1, HIGH);
  digitalWrite(A2, LOW);
  digitalWrite(A3, HIGH);
  delayMicroseconds(100);
  //Read keys in row.1
  if(digitalRead(10)==LOW)
  {
      digitalWrite(A2, HIGH);
      Col=3;Row=1;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.2
  if(digitalRead(11)==LOW)
  {
      digitalWrite(A2, HIGH);
      Col=3;Row=2;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.3
  if(digitalRead(12)==LOW)
  {
      digitalWrite(A2, HIGH);
      Col=3;Row=3;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.4
  if(digitalRead(13)==LOW)
  {
      digitalWrite(A2, HIGH);
      Col=3;Row=4;
      keypressed = true;
      return(keypressed);
  }
  //scan col4
  digitalWrite(A0, HIGH);
  digitalWrite(A1, HIGH);
  digitalWrite(A2, HIGH);
  digitalWrite(A3, LOW);
  delayMicroseconds(100);
  //Read keys in row.1
  if(digitalRead(10)==LOW)
  {
      digitalWrite(A3, HIGH);
      Col=4;Row=1;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.2
  if(digitalRead(11)==LOW)
  {
      digitalWrite(A3, HIGH);
      Col=4;Row=2;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.3
  if(digitalRead(12)==LOW)
  {
      digitalWrite(A3, HIGH);
      Col=4;Row=3;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.4
  if(digitalRead(13)==LOW)
  {
       digitalWrite(A3, HIGH);
      Col=4;Row=4;
      keypressed = true;
      return(keypressed);
  }
  return(false);
}
void WriteNumberToSegment(byte Segment, byte Value)
{
digitalWrite(LATCH_DIO,LOW);
shiftOut(DATA_DIO, CLK_DIO, MSBFIRST, Value);
shiftOut(DATA_DIO, CLK_DIO, MSBFIRST, SEGMENT_SELECT[Segment] );
digitalWrite(LATCH_DIO,HIGH);
}



```
# 數字左移
```
#define LATCH_DIO D15   
#define CLK_DIO D14
#define DATA_DIO 2

//char KeyValue[]={'1','2','3','A','4','5','6','B','7','8','9','C','*','0','#','D'};
/*const byte KeyMap[]={0x06,0x5b,0x4F,0X77,
                     0x66,0x6D,0x7D,0x7c,
                     0x27,0X7F,0X67,0x39,
                     0x79,0x3F,0x71,0X5e, 0};*/
const byte KeyMap[4][4]={{0x06,0x5b,0x4F,0X77},
                     {0x66,0x6D,0x7D,0x7c},
                     {0x27,0X7F,0X67,0x39},
                     {0x79,0x3F,0x71,0X5e}};                     
const byte SEGMENT_SELECT[] = {0xFE,0xFD,0xFB,0xF7};
byte Row=0, Col=0;
byte displaybuf[4]={0,0,0,0};

void bufshift(byte dir, byte databyte)//dir=0:shift left, dir=1:shift right
{
  if(dir == 0)
  {
    for (int j=0; j<3; j++)
    {
      displaybuf[3-j]=displaybuf[3-j-1];
    }
    displaybuf[0]=databyte;
  }
  else
  {
    for (int j=0; j<3; j++)
    {
      displaybuf[j]=displaybuf[j+1];
    }
    displaybuf[3]=databyte;
  }
}

void show7seg()
{
  int i;
  for(i=0; i<4; i++)
  {
    WriteNumberToSegment(3-i, displaybuf[i]);
    delay(2);
  }
}

void setup() {
  // put your setup code here, to run once:
  pinMode(LATCH_DIO,OUTPUT);
  pinMode(CLK_DIO,OUTPUT);
  pinMode(DATA_DIO,OUTPUT);
  pinMode(10, INPUT); //R1: S1,S2,S3,S4 (1,2,3,A)                                   
  pinMode(11, INPUT_PULLUP); //R2: S5,S6,S7,S8 (4,5,6,B)
  pinMode(12, INPUT_PULLUP); //R3: S9, S10, S11,S12 (7,8,9,C)
  pinMode(13, INPUT_PULLUP); //R4: (*,0,#,D) //*->E, #->F
  pinMode(A0, OUTPUT); //A1, C1: S1,S5,S9 (1,4,7,*)
  pinMode(A1, OUTPUT); //A2, C2: S2,S6,S10 (2,5,8,0)
  pinMode(A2, OUTPUT); //A3, C3: S3,S7,S11 (3,6,9,#)
  pinMode(A3, OUTPUT); //A4, C4, S4,S8,S12 (*,0, #,D)
  //Pin left to right :R1 R2 R3 R4 C1 C2 C3 C4
  show7seg();
} 

void loop() {
  // put your main code here, to run repeatedly:
  static int keypressedcount=0;
  byte keyindex=0;
  //if key is pressed in the first round scan, 
  //then call keyscan() again to check if the key pressed in first round is actually pressed 
  if(keyscan()==true) 
  {
    keyindex=(Row-1)*4+Col-1;
    delay(5);
    if ((keyscan()==true) && (keyindex==(Row-1)*4+Col-1))
    {
      digitalWrite(A0,LOW);
      digitalWrite(A1,LOW);
      digitalWrite(A2,LOW);
      digitalWrite(A3,LOW);
      delayMicroseconds(100);
      while( (digitalRead(10)==LOW) || (digitalRead(11)==LOW)||(digitalRead(12)==LOW) || (digitalRead(13)==LOW))
        ;
      bufshift(0, KeyMap[Row-1][Col-1]);    
      
    }
  }
  show7seg(); 
}

bool keyscan( )
{
  Row=0;Col=0;
  bool keypressed = false;
  //scan col1
  digitalWrite(A0, LOW);
  digitalWrite(A1, HIGH);
  digitalWrite(A2, HIGH);
  digitalWrite(A3, HIGH);
  delayMicroseconds(100);
  //Read keys in row.1
  if(digitalRead(10)==LOW)
  {
      digitalWrite(A0, HIGH);
      Col=1;Row=1;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.2
  if(digitalRead(11)==LOW)
  {
      digitalWrite(A0, HIGH);
      Col=1;Row=2;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.3
  if(digitalRead(12)==LOW)
  {
      digitalWrite(A0, HIGH);
      Col=1;Row=3;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.4
  if(digitalRead(13)==LOW)
  {
       digitalWrite(A0, HIGH);
      Col=1;Row=4;
      keypressed = true;
      return(keypressed);
  }
  //scan col2
  digitalWrite(A0, HIGH);
  digitalWrite(A1, LOW);
  digitalWrite(A2, HIGH);
  digitalWrite(A3, HIGH);
  delayMicroseconds(100);
  //Read keys in row.1
  if(digitalRead(10)==LOW)
  {
      digitalWrite(A1, HIGH);
      Col=2;Row=1;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.2
  if(digitalRead(11)==LOW)
  {
      digitalWrite(A1, HIGH);
      Col=2;Row=2;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.3
  if(digitalRead(12)==LOW)
  {
      digitalWrite(A1, HIGH);
      Col=2;Row=3;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.4
  if(digitalRead(13)==LOW)
  {
      digitalWrite(A1, HIGH);
      Col=2;Row=4;
      keypressed = true;
      return(keypressed);
  }
  //scan col3
  digitalWrite(A0, HIGH);
  digitalWrite(A1, HIGH);
  digitalWrite(A2, LOW);
  digitalWrite(A3, HIGH);
  delayMicroseconds(100);
  //Read keys in row.1
  if(digitalRead(10)==LOW)
  {
      digitalWrite(A2, HIGH);
      Col=3;Row=1;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.2
  if(digitalRead(11)==LOW)
  {
      digitalWrite(A2, HIGH);
      Col=3;Row=2;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.3
  if(digitalRead(12)==LOW)
  {
      digitalWrite(A2, HIGH);
      Col=3;Row=3;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.4
  if(digitalRead(13)==LOW)
  {
      digitalWrite(A2, HIGH);
      Col=3;Row=4;
      keypressed = true;
      return(keypressed);
  }
  //scan col4
  digitalWrite(A0, HIGH);
  digitalWrite(A1, HIGH);
  digitalWrite(A2, HIGH);
  digitalWrite(A3, LOW);
  delayMicroseconds(100);
  //Read keys in row.1
  if(digitalRead(10)==LOW)
  {
      digitalWrite(A3, HIGH);
      Col=4;Row=1;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.2
  if(digitalRead(11)==LOW)
  {
      digitalWrite(A3, HIGH);
      Col=4;Row=2;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.3
  if(digitalRead(12)==LOW)
  {
      digitalWrite(A3, HIGH);
      Col=4;Row=3;
      keypressed = true;
      return(keypressed);
  }
  //Read keys in row.4
  if(digitalRead(13)==LOW)
  {
       digitalWrite(A3, HIGH);
      Col=4;Row=4;
      keypressed = true;
      return(keypressed);
  }
  return(false);
}
void WriteNumberToSegment(byte Segment, byte Value)
{
digitalWrite(LATCH_DIO,LOW);
shiftOut(DATA_DIO, CLK_DIO, MSBFIRST, Value);
shiftOut(DATA_DIO, CLK_DIO, MSBFIRST, SEGMENT_SELECT[Segment] );
digitalWrite(LATCH_DIO,HIGH);
}





```
