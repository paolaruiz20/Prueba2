# Prueba2
#include <DHT.h>//Libreria
#define DHTPIN 8 
int VERDE = 3;
int azul = 4;
DHT dht(DHTPIN, DHTTYPE);
void setup() {
  Serial.begin(9600);
  dht.begin();
  pinMode(rojo,OUTPUT);
  pinMode(azul,OUTPUT);
}
void loop() {
  float humedad = dht.readHumidity();
  float temperatura = dht.readTemperature();
  Serial.print("Humedad: ");
  Serial.print(humedad);
  Serial.print("%  ");
  Serial.print("Temperatura: ");
  Serial.print(temperatura);
  Serial.println("°C");
  delay(2000);
  if (temperatura >= 21) {
    Serial.println("calor");
    digitalWrite(rojo, HIGH);
    digitalWrite(azul, LOW);
  } else {
    Serial.println("frio");
    digitalWrite(rojo, LOW);
    digitalWrite(azul, HIGH);
  }
}


