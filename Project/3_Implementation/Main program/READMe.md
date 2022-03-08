## Arduino IDE program

#include<Keypad.h> // KEYPAD LIBRARY FOR KEYPAD INTERFACING 
#include<LiquidCrystal.h> // LIBRARY FOR LCD INTERFACING
#include<Servo.h>// LIBRARY FOR SERVO MOTOR
#include<EEPROM.h>



# define buzzer  11// DEFINING PIN FOR BUZZER
# define redPin  9// DEFINING PIN FOR RED LED
# define greenPin 8 // DEFINING PIN FOR GREEN LED
# define ledpin  12// DEFINING PIN FOR OUTDOOR LIGHT

LiquidCrystal lcd(A0, A1, A2, A3, A4, A5);// PINS FOR LCD


char keys[4][3]={ // LAYOUT OF KEYPAD
  {'1', '2', '3'},
  {'4', '5', '6'},
  {'7', '8', '9'},
  {'*', '0', '#'}};
 
byte rowPin[4]={1, 2, 3, 4}; // ROW PINS OF KEYPAD
byte colPin[3]={5, 6, 7}; // COLUMN PINS OF KEYPAD

Servo servo_Motor; 
char initial_password[3],new_password[3]; //VARIABLES FOR PASSWORD.
int position = 0; // VARIABLE FOR DETERMINING THE POSITION.

int wrong = 0; // VARIABLE FOR CALCULATING THE WRONG INPUT.
 
Keypad keypad=Keypad(makeKeymap(keys),rowPin,colPin,4,3);// MAPPING THE KEYPAD.


int total = 0; // VARIABLE TO DETERMINE THE NUMBER OF WRONG ATTEMPTS.

void setup()
{
 pinMode(ledpin,OUTPUT);
 pinMode(redPin,OUTPUT);
 pinMode(greenPin,OUTPUT);
 
lcd.begin(16,2);
lcd.print("HOME AUTOMATION");
lcd.setCursor(0,2);
lcd.print("BASED ENERGYMETER");
delay(2000);
lcd.clear();
servo_Motor.attach(10);
setLocked(true);
delay(1000);
initialpassword();
pinMode(buzzer, OUTPUT);
}

void loop()
{
   
  lcd.clear();
  lcd.print("ENTER PASSWORD");
  delay(100);
  
 char pressed=keypad.getKey();// TAKING THE INPUT FROM KEYPAD
 String key[3];
 digitalWrite(ledpin,HIGH);
 if(pressed) // IF THE KEY IS PRESSED
 {
  lcd.clear();
  lcd.print("ENTER PASSWORD");
  lcd.setCursor(position,2);
  lcd.print(pressed);
  delay(500);
    if(pressed == '*')// IF THE KEY * IS PRESSED
      {
          lcd.clear();
          lcd.print("DOOR LOCKED");
          position = 0;
          setLocked(true);
          lcd.clear();
      }
      else if (pressed == '#')// IF THE KEY # IS PRESSED
       {
         
         position = 0;
         lcd.clear();
         change();
       }

    else if(pressed == initial_password[position])// CHECK THE PASSWORD
      {
          key[position]=pressed;
          position++;
      }
 
    else if (pressed != initial_password[position] )
      {
          wrong++;// IN CASE OF WRONG INPUT INCREMENT BOTH WRONG AND POSITION.
          position ++;
      }
      

    if(position == 3)// WHEN POSITION == 3 THEN CHECK THE FOLLOWING
      {
          if( wrong >0) // IF ANY WRONG INPUT IF GIVEN THEN INCREMENT TOTAL AND
          
            {
                total++;
                wrong = 0;
                position = 0;// SET WRONG AND POSITION TO ZERO.
                lcd.clear();
                lcd.print("WRONG");
                lcd.setCursor(5,2);
                lcd.print("PASSWORD");
                delay(1000);
                setLocked(true);
            }

          else if(position == 3 && wrong == 0)// IF NO WRONG VALUE IS GIVEN THEN DISPLAY THE ACCEPTED PASSWORD AND
            {                                  // MOVE THE SERVO MOTOR.
             
                position = 0;
                wrong = 0;
                lcd.clear();
                lcd.print("PASSWORD");
                lcd.setCursor(6,2);
                lcd.print("ACCEPTED");
                delay(2000);
                lcd.clear();
                lcd.print("DOOR OPEN");
                delay(2000);
                setLocked(false);
            }

          if(total ==3)// IF TOTAL OF 3 ATTEMPTS ARE DONE BY ENTERING WRONG PASS
         
            {
                total=0; //WORD THEN SOUND A BUZZER AND SET TOTAL TO 0.
                buzzer_beep();
                delay(500);
            }
       } 
          
    }
}

void setLocked(int locked)// FUNCTION TO CHANGE STATUS OF SERVO MOTOR.
  {
    if (locked)
      {
          digitalWrite(redPin, HIGH);
          digitalWrite(greenPin, LOW);
          delay(1000);
          servo_Motor.attach(10);
          servo_Motor.write(10);
          delay(1000);
          servo_Motor.detach();
      }
    else
      {
          digitalWrite(redPin, LOW);
          digitalWrite(greenPin, HIGH);
          delay(1000);
          servo_Motor.attach(10);
          servo_Motor.write(90);
          delay(1000);
          servo_Motor.detach();
      }
  }
void buzzer_beep()// FUNCTION TO BEEP THE BUZZER.
{
 analogWrite(buzzer, 200);     
 delay(1000);          
  
   while(1)
   {
   lcd.scrollDisplayLeft();
   delay(200);
   }
}

void change()// FUNCTION TO CHECK THE PASSWORD.
{
  char pressed;
  int j=0;
  lcd.clear();
  lcd.print("CURRENT PASSWORD");
  lcd.setCursor(0,1);
  while(j<3)
  {
   char pressed=keypad.getKey();// TAKING THE INPUT FROM KEYPAD
    if(pressed)

    {
      new_password[j++]=pressed;
      lcd.print(pressed);
    }
    pressed=0;
  }
  delay(500);
  if((strncmp(new_password, initial_password, 3)))// IF THE PASSWORD IS NOT EQUAL TO INITIAL PASSWORD
  {
    lcd.clear();
    lcd.print("WRONG PASSWORD");
    lcd.setCursor(0,1);
    lcd.print("TRY AGAIN");
    delay(1000);
  }
  else       // IF THE PASSWORD IS EQUAL TO INITIAL PASSWORD
 {                           
    j=0;
    lcd.clear();
    lcd.print("NEW PASSWORD");
    lcd.setCursor(0,1);
    while(j<3)
    {
      char pressed=keypad.getKey();// TAKING THE INPUT FROM KEYPAD
      if(pressed)
      {
        initial_password[j]=pressed;
        lcd.print(pressed);
        EEPROM.write(j,pressed);// WRITING NEW PASSWORD TO EEPROM
        j++;
      }
    }
    lcd.print("PASS CHANGED");
    delay(1000);
  }
  lcd.clear();
  lcd.print("ENTER PASSWORD");
  lcd.setCursor(0,1);
  pressed=0;
}

 
void initialpassword()// FUNCTION TO GENERATE INITIAL PASSWORD AS 123.
{
  for(int j=0;j<3;j++)
  EEPROM.write(j, j+49);// WRITING PASSWORD TO EEPROM
  for(int j=0;j<3;j++)
    initial_password[j]=EEPROM.read(j);
}
