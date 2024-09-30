#include <DHT.h>
#include <Servo.h>
#include <ArduinoJson.h>

#define ledG 13 // Definição do LED verde
#define ledR 12 // Definição do LED vermelho
#define DHTPIN 7 // Pino de leitura do sensor DHT11
#define DHTTYPE DHT11 // Tipo do sensor DHT11
#define ServoPin 11 // Pino de controle do Servo

Servo myServo; // Objeto Servo
DHT dht(DHTPIN, DHTTYPE); // Objeto DHT

void setup() {
  pinMode(ledG, OUTPUT); // Define o LED verde como saída
  pinMode(ledR, OUTPUT); // Define o LED vermelho como saída
  myServo.attach(ServoPin); // Anexa o servo ao pino definido
  dht.begin(); // Inicializa o sensor DHT11
  Serial.begin(9600); // Inicializa a comunicação serial
}

void loop() {
  // Lê a temperatura e a umidade do sensor
  float temp = dht.readTemperature(); // Lê a temperatura em Celsius
  float humidity = dht.readHumidity(); // Lê a umidade

  // Verifica se a leitura falhou
  if (isnan(temp) || isnan(humidity)) {
    Serial.println("Falha ao ler o sensor DHT!");
    return;
  }

  // Cria um objeto JSON para enviar os dados via Serial
  StaticJsonDocument<100> json;
  json["Temperatura"] = temp;
  json["Umidade"] = humidity;

  // Converte o objeto JSON para uma string e envia via Serial
  String output;
  serializeJson(json, output);
  Serial.println(output);

  // Controla os LEDs com base na temperatura
  if (temp > 25) {
    digitalWrite(ledG, LOW);
    digitalWrite(ledR, HIGH); // Liga o LED vermelho se a temperatura for maior que 25°C
    myServo.write(90); // Move o servo para 90 graus
  } else {
    digitalWrite(ledR, LOW);
    digitalWrite(ledG, HIGH); // Liga o LED verde se a temperatura for menor ou igual a 25°C
    myServo.write(0); // Move o servo para 0 graus
  }

  delay(2000); // Aguarda 2 segundos antes da próxima leitura
}
