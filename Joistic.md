# El joistic

paguina donde estam las instrucciones del Joistic de David: https://github.com/d-prieto/arduinoCourse/blob/main/Clase_de_Joystick.md


## Codigo

```C++

const int pinBoton = 3; 
const int pinEjeY = A1; 
const int pinEjeX = A0; 
 
void setup() {
  pinMode(pinBoton, INPUT);
  digitalWrite(pinBoton, HIGH);
  Serial.begin(9600);
}
 
void loop() {
  Serial.print("Boton:  ");
  Serial.print(digitalRead(pinBoton));
  Serial.print("\n");
  Serial.print("Eje X: ");
  Serial.print(analogRead(pinEjeX));
  Serial.print("\n"); //esto es un salto de linea
  Serial.print("Eje Y: ");
  Serial.println(analogRead(pinEjeY));
  Serial.print("\n\n");
  delay(150);
}
```
# Funcionamiento

El funcionamiento del joistic y del codigo de arriba esta correctamente hecho y el unico problema surguido fue una pequeña dificultad de poner los cables y conectarlos donde debian ponerse.


## Variacion

```C++

const int pinBoton = 3; 
const int pinEjeY = A1; 
const int pinEjeX = A0; 
const int pinLed = 2; 

 int switchState = 0;
 
void setup() {
  pinMode(pinBoton, INPUT);
  digitalWrite(pinBoton, HIGH);
  Serial.begin(9600);
  pinMode(2,OUTPUT);
}

 
void loop() {
  Serial.print("Boton:  ");
  Serial.print(digitalRead(pinBoton));
  Serial.print("\n");
  Serial.print("Eje X: ");
  Serial.print(analogRead(pinEjeX));
  Serial.print("\n"); //esto es un salto de linea
  Serial.print("Eje Y: ");
  Serial.println(analogRead(pinEjeY));
  Serial.print("\n\n");
  delay(150);

  switchState = digitalRead(pinBoton);
   if (switchState == LOW) {
    digitalWrite(2, HIGH);
   }
   else {
    digitalWrite(2, LOW);
   }
}
```

