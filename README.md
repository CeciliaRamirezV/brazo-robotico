# brazo-robotico
#include <Servo.h>

const int servo1 = 4;       // Servo 1
const int servo2 = 5;       // Servo 2
const int servo2 = 6;       // Servo 3
const int servo2 = 7;       // Servo 4
const int joyH = 3;        // Joystick 1
const int joyV = 4;        // Joystick 2
const int joyX = 5;        // Joystick 3
const int joyZ = 6;        // Joystick 4

int servoVal;           // valor para servos

Servo myservo1;  // Creando Servors
Servo myservo2;
Servo myservo3;
Servo myservo4;



void setup() {

  // Servo  
  myservo1.attach(servo1);  // Asignamos Servos a pin
  myservo2.attach(servo2); 
  myservo2.attach(servo3); 
  myservo2.attach(servo4); 

  Serial.begin(9600);
}


void loop(){

    //Mostramos valores Joysticks
    outputJoystick();

    // Leemos el Valor del Joystick y Hacemos un MAPEO de valores , luego lo enviamos al servo

    servoVal = analogRead(joyX);          
    servoVal = map(servoVal, 0, 1023, 0, 180);   

    myservo4.write(servoVal);          

    servoVal = analogRead(joyZ);          
    servoVal = map(servoVal, 0, 1023, 0, 180);   

    myservo3.write(servoVal);          

    servoVal = analogRead(joyH);          
    servoVal = map(servoVal, 0, 1023, 0, 180);   

    myservo2.write(servoVal);                       


    servoVal = analogRead(joyV);           
    servoVal = map(servoVal, 0, 1023,0, 180);    

    myservo1.write(servoVal);                           

    delay(15);                                      

}


/**
* Display joystick values
*/
void outputJoystick(){

    Serial.print(analogRead(joyH));
    Serial.print ("---"); 
    Serial.print(analogRead(joyV));
    Serial.print ("---"); 
    Serial.print(analogRead(joyX));
    Serial.print ("---"); 
    Serial.print(analogRead(joyZ));
    Serial.println ("----------------");
}
