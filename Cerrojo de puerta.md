# Proceso

El proceso de creacion del cerrojo de puerta hubieron inconvenientes con el codigo que gracias a la correccion del profesor David que arreglo todos los desperfectos y me señalo todos los puntos donde el circuito tenia un fallo. El funcionamiento del circuito es como deberia cuando esta abierta esta encendida la luz verde, cuando es ta cerrada la luz roja esta encendidada, la luz amarilla es encendida brevemente cuando se tetecta y registra cada golpe sobre la superficie donde esta situada.

## Codigo y foto

``` C++

#include <Servo.h>
Servo myServo;

const int piezo = A0;
const int switchPin = 2;
const int yellowLed = 3;
const int greenLed = 4;
const int redLed = 5;

int knockVal;
int switchVal;

const int quietKnock = 100;
const int loudKnock = 200;

boolean locked = false;
int numberOfKnocks = 0;

void setup(){
  myServo.attach(9);
  pinMode(yellowLed, OUTPUT);
  pinMode(redLed, OUTPUT);
  pinMode(greenLed, OUTPUT);
  pinMode(switchPin, INPUT);
  Serial.begin(9600);

  digitalWrite(greenLed, HIGH);
  myServo.write(0);
  Serial.println("La caja está abierta");
}

void loop(){
  if(locked == false){
    switchVal = digitalRead(switchPin);
    if(switchVal == HIGH){
      locked = true;
      digitalWrite(greenLed,LOW);
      digitalWrite(redLed,HIGH);
      myServo.write(90);
      Serial.println("LA caja está cerrada");
      delay (1000);
    }
  }
  
  if(locked ==true){
    Serial.println("Entrando en el if de locked == true");
    knockVal = analogRead (piezo);

    if(numberOfKnocks < 3 && knockVal > 0){
      if(checkForKnock (knockVal) == true){
        numberOfKnocks++;
    }
    Serial.print(3-numberOfKnocks);
    Serial.println("Moras golpes para ir");
  }

  if(numberOfKnocks >= 3){
    locked = false;
    myServo.write(0);
    delay(20);
    digitalWrite(greenLed, HIGH);
    digitalWrite(redLed, LOW);
    Serial.println("La caja está abierta");
    numberOfKnocks =0;
  }
}
}

boolean checkForKnock(int value){

  if(value > quietKnock && value < loudKnock){

    digitalWrite(yellowLed, HIGH);
    delay(50);
    digitalWrite(yellowLed, LOW);
    Serial.print("Valor de golpe válido");
    Serial.println(value);

    return true;
  }

else {
  Serial.print("Valor de golpe no valido");
  Serial.println(value);
  return false;
}
}


```



https://raw.githubusercontent.com/Baelyn1/2-Trimestre/main/IMG_2562.JPG

