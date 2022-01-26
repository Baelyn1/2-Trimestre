# Proceso

El proceso de la fabricacion de la lampara tactil fue simple y sin ningun tipo de inconvenientes, se conecto todo de manera correcta se escribio el codigo bien y para la parte donde se activa y desactiva la lampara se puso el papel de aluminio doblado y bien puesto.


## Codigo de la lampara y foto

```C++


#include <CapacitiveSensor.h>
CapacitiveSensor capSensor = CapacitiveSensor(4,2);

int threshold = 1000;
const int ledPin = 12;

void setup() {
  Serial.begin(9600);
  pinMode(ledPin, OUTPUT);
}

void loop() {
  long sensorValue = capSensor.capacitiveSensor(30);
  Serial.println(sensorValue);

  if(sensorValue > threshold) {
    digitalWrite(ledPin, HIGH);
  }
  else{
    digitalWrite(ledPin, LOW);
  }
  delay(10);
}
```

