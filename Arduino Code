#include<LiquidCrystal.h> 
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

int ss,mm,hh,MM,DD,YYYY,AP;

int k=0;

void setup()

{

Serial.begin(9600);

lcd.begin(16,2);

}

void loop()

{

/*After asking for details k=1 so never asks for instructions again*/

if(k<=0)

{

/*Details() - Asks for time and date*/

Details();

}

ss=ss+1;

if(ss==60)

{

ss=0;

mm=mm+1;

if(mm==60)

{

mm=0;

hh=hh+1;

if(hh==12)

{

AP=AP+1;

printTime2();

/*Day only advances when going from PM to AM*/

if(AP%2==0)

{

DD=DD+1;

}

// assumes that all months have 28 days

if(DD==28)

{

DD=1;

MM=MM+1;

if(MM==13)

{

MM=1;

YYYY=YYYY+1;

}

}

}

if(hh==13)

{

hh=1;

}

}

}

/*printTime2 - adds one second and displays time on LCD display*/

printTime2();

}

void line()

{

Serial.println("");

}

void Details()

{

Serial.println("Enter current hour:");

while(Serial.available()==0);

hh=Serial.parseInt();

/*line() - inserts blank line into serial monitor to separate data*/

line();

Serial.println("Enter current minute:");

while(Serial.available()==0);

mm=Serial.parseInt();

line();

Serial.println("Enter current second:");

while(Serial.available()==0);

ss=Serial.parseInt();

line();

Serial.println("Enter AM(0) or PM(1)");

while(Serial.available()==0);

AP=Serial.parseInt();

line();

Serial.println("Enter current month:");

while(Serial.available()==0);

MM=Serial.parseInt();

line();

Serial.println("Enter current date:");

while(Serial.available()==0);

DD=Serial.parseInt();

line();

Serial.println("Enter current year:");

while(Serial.available()==0);

YYYY=Serial.parseInt();

line();

k=k+1;

}

void printTime(int x)

{

if(x<=9)

{

lcd.print("0");lcd.print(x);

}

else

{

lcd.print(x);

}

}

void printTime2()

{

lcd.setCursor(0,0);

/*printTime - places "0" in front of single digit numbers*/

printTime(hh); lcd.print(":");

printTime(mm); lcd.print(":");

printTime(ss); lcd.print(" ");

/*if AP is odd, it reads AM

if AP is even, it reads PM*/

if(AP%2==0)

{lcd.print("AM");}

if(AP%2==1)

{lcd.print("PM");}

lcd.setCursor(0,1);

printTime(DD); lcd.print("/");

printTime(MM); lcd.print("/");

printTime(YYYY);

delay(1000);

}
