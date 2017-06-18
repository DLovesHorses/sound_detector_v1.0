<b><h1># Sound Detector v1.0</h1></b>


<em><h3>Sound Detector and Air Vibration Sensor<h3></em>

/* Software Author : <h4><b><i>Puranjan Gaur.</i></b></h4>

<h5>Date of publishing : <h4><b><i> 18-June-2017.</i></b></h4></h5>



<b>Open-Source Hardware under Creative Commons License Agreement.


By Using this project, you agree that the designer will not held responsible for any of your actions.</b> */



<b> Source Code :- </b>


#include <Ultrasonic.h>


#include<LiquidCrystal.h>


Ultrasonic rangeFinder (A1,A2);


LiquidCrystal lcd(12,11,5,4,3,2);



byte heart[8]{
  B01010,
  
  B11111,
  
  B11111,
  
  B01110,
  
  B00100,
  
  B00000,
  
  B00000
  
};

int pinTrig = A1;

int pinEcho = A2;

int L1 = 6;

int L2 = 7;

int L3 = 8;

int L4 = 9;

int L5 = 10;

int L6 = 13;


int analogPin = A0;

int firstRef = 0;

int secondRef =0;


int finCompL1 = 0;

int finCompL2 = 0;

int finCompL3 = 0;

int finCompL4 = 0;

int finCompL5 = 0;

int finCompL6 = 0;

int mulL1 = 0;

int mulL2 = 0;

int mulL3 = 0;

int mulL4 = 0;

int mulL5 = 0;

int mulL6 = 0;

int finCompA = 0;

int inRange = 0;
  
void setup(){

  Serial.begin(9600);
  
  pinMode(L1,OUTPUT);
  
  pinMode(L2,OUTPUT);
  
  pinMode(L3,OUTPUT);
  
  pinMode(L4,OUTPUT);
  
  pinMode(L5,OUTPUT);
  
  pinMode(L6,OUTPUT);
  
  pinMode(analogPin,INPUT);
  
  digitalWrite(L1,LOW);
  
  digitalWrite(L2,LOW);
  
  digitalWrite(L3,LOW);
  
  digitalWrite(L4,LOW);
  
  digitalWrite(L5,LOW);
  
  digitalWrite(L6,LOW);
  
  
  lcd.begin (16,2);
  
  lcd.display();
  
  lcd.clear();
  
  delay(1000);



  //INITIAL DISPLAY

  lcd.createChar(1,heart);
  
  lcd.clear();
  
  delay(10);
  
  lcd.print("Made By");
  
  lcd.setCursor(7,1);
  
  lcd.print("Puranjan");
  
  Serial.println("Made By Puranjan");
  
  delay(5000);

  
  lcd.clear();
  
  lcd.print("Meow!");
  
  Serial.println("Done");
  
  delay(3000);
  
  lcd.clear();
  

  lcd.print(" Sound Detector ");
  
  lcd.setCursor(0,1);
  
  lcd.print("& Range Finder. ");
  
  delay(3000);
  
  lcd.clear();


  firstRef = analogRead(analogPin);
  
  lcd.print("A1 = ");
  
  lcd.print(firstRef);
  
  Serial.print("A1 = ");
  
  Serial.println(firstRef);
  
  delay(3000);
  
  lcd.clear();
  

  secondRef = analogRead(analogPin)+ 4;
  
  lcd.print("A2 = ");
  
  lcd.print(secondRef);
  
  Serial.print("A2 = ");
  
  Serial.println(secondRef);
  
  delay(3000);
  
  lcd.clear();

  mulL1 = ((firstRef - 555) / (secondRef - firstRef));
  
  mulL2 = ((firstRef - 560) / (secondRef - firstRef));
  
  mulL3 = ((570 - firstRef) / (secondRef - firstRef));
  
  mulL4 = ((580 - firstRef) / (secondRef - firstRef));
  
  mulL5 = ((590 - firstRef) / (secondRef - firstRef));
  
  mulL6 = ((600 - firstRef) / (secondRef - firstRef));
  

  Serial.print("First Limit = ");
  
  Serial.println(mulL1);
  
  Serial.print("Second Limit = ");
  
  Serial.println(mulL2);
  
  Serial.print("Third Limit = ");
  
  Serial.println(mulL3);
  
  Serial.print("Fourth Limit = ");
  
  Serial.println(mulL4);
  
  Serial.print("Fifth Limit = ");
  
  Serial.println(mulL5);
  
  Serial.print("Sixth Limit = ");
  
  Serial.println(mulL6);
  
  delay(500);
  

  finCompL1 = firstRef - (mulL1 * (secondRef - firstRef));
  
  lcd.print("finCompL1 = ");
  
  lcd.print(finCompL1);
  
  Serial.print("finCompL1 = ");
  
  Serial.println(finCompL1);
  
  delay(1500);
  
  lcd.clear();
  
  finCompL2 = firstRef - (mulL2 * (secondRef - firstRef));
  
  lcd.print("finCompL2 = ");
  
  lcd.print(finCompL2);
  
  Serial.print("finCompL2 = ");
  
  Serial.println(finCompL2);
  
  delay(1500);
  
  lcd.clear();

  finCompL3 = firstRef + (mulL3 *(secondRef - firstRef));
  
  lcd.print("finCompL3 = ");
  
  lcd.print(finCompL3);
  
  Serial.print("finCompL3 = ");
  
  Serial.println(finCompL3);
  
  delay(1500);
  
  lcd.clear();
  

  finCompL4 = firstRef + (mulL4 * (secondRef - firstRef));
  
  lcd.print("finCompL4 = ");
  
  lcd.print(finCompL4);
  
  Serial.print("finCompL4 = ");
  
  Serial.println(finCompL4);
  
  delay(1500);
  
  lcd.clear();

  finCompL5 = firstRef + (mulL5 *(secondRef - firstRef));
  
  lcd.print("finCompL5 = ");
  
  lcd.print(finCompL5);
  
  Serial.print("finCompL5 = ");
  
  Serial.println(finCompL5);
  
  delay(1500);
  
  lcd.clear();
  

  finCompL6 = firstRef + (mulL6 * (secondRef - firstRef));
  
  lcd.print("finCompL6 = ");
  
  lcd.print(finCompL6);
  
  
  Serial.print("finCompL6 = ");
  
  Serial.println(finCompL6);
  
  delay(1500);
  
  lcd.clear();


  lcd.clear();
  

  lcd.print("Made by ");
  
  lcd.setCursor(4,1);
  
  
  lcd.print("Puranjan");
  
  lcd.write(1);
  
  lcd.write(1);
  
  lcd.write(1);
  
  lcd.blink();
  
  
}


void loop(){


  finCompA = analogRead(analogPin);
  
  inRange = map(finCompA,565,1500,1,50);

  
  /*if ( finCompA >=finCompL6){
  
    lcd.clear();
    
    delay(5);
    
    digitalWrite(L6, HIGH);
    
    lcd.print("Sound Detected !");
    
    lcd.setCursor(0,1);
    
    lcd.print("Level = ");
    
    lcd.print(inRange*8);
    
    Serial.print("Sound Detected ! \t \t");
    
    Serial.print("Intensity Level = ");
    
    Serial.println(inRange * 8);
    
    delay(300);
    
    
  }

  else {
  
    lcd.clear();
    
    digitalWrite(L6,LOW);
    
    lcd.print("No Sound Detecte");
    
    lcd.setCursor(0,1);
    
    lcd.print("d");
    
    delay(10);
    
  }

  */
  




if (finCompA >= finCompL1){

  digitalWrite(L1,HIGH);
  

    if ( finCompA >= finCompL2){
    
      digitalWrite(L2, HIGH);
      
      
        if (finCompA >= finCompL3){
        
          digitalWrite(L3, HIGH);
          

            if (finCompA >= finCompL4){
            
              digitalWrite(L4, HIGH);
              

                if (finCompA >= finCompL5){
                
                  digitalWrite (L5, HIGH);
                  

                  if (finCompA >= finCompL6){
                  
                    digitalWrite (L6, HIGH);
                    
                    }
                  else{
                  
                    digitalWrite (L6, LOW);
                    
                    }
                  }
                
                else {
                
                  digitalWrite (L5, LOW);
                  
                }
              }

            else {
            
            digitalWrite(L4, LOW);
            
            }
        }

      else {
      
        digitalWrite(L3,LOW);
        
      }
    }

  else {
  
    digitalWrite(L2,LOW);
    
  }
  
}


else {

  digitalWrite(L1, LOW);
  
  digitalWrite(L2, LOW);
  
  digitalWrite(L3, LOW);
  
  digitalWrite(L4, LOW);
  
  digitalWrite(L5, LOW);
  
  digitalWrite(L6, LOW);
  
}



}



