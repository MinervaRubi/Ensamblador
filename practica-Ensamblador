const int ledA = 2;
const int ledB = 3;
const int ledC = 4;
const int ledD = 5;
const int ledE = 6;
const int ledF = 7;
const int ledG = 8;

const int pinesLed[] = {ledA, ledB, ledC, ledD, ledE, ledF, ledG};
//como deben  plrender los leds segun lo deseado 
const bool numeros[16][7] = {
  {HIGH, HIGH, HIGH, HIGH, HIGH, HIGH, LOW},   // 0
  {LOW, HIGH, HIGH, LOW, LOW, LOW, LOW},       // 1
  {HIGH, HIGH, LOW, HIGH, HIGH, LOW, HIGH},    // 2
  {HIGH, HIGH, HIGH, HIGH, LOW, LOW, HIGH},    // 3
  {LOW, HIGH, HIGH, LOW, LOW, HIGH, HIGH},     // 4
  {HIGH, LOW, HIGH, HIGH, LOW, HIGH, HIGH},    // 5
  {HIGH, LOW, HIGH, HIGH, HIGH, HIGH, HIGH},   // 6
  {HIGH, HIGH, HIGH, LOW, LOW, LOW, LOW},      // 7
  {HIGH, HIGH, HIGH, HIGH, HIGH, HIGH, HIGH},  // 8
  {HIGH, HIGH, HIGH, HIGH, LOW, HIGH, HIGH},   // 9
  {HIGH, HIGH, HIGH, LOW, HIGH, HIGH, HIGH},   // A
  {LOW, LOW, HIGH, HIGH, HIGH, HIGH, HIGH},    // b
  {LOW, LOW, LOW, HIGH, HIGH, LOW, HIGH},      // C
  {LOW, HIGH, HIGH, HIGH, HIGH, LOW, HIGH},    // d
  {HIGH, LOW, LOW, HIGH, HIGH, HIGH, HIGH},    // E
  {HIGH, LOW, LOW, LOW, HIGH, HIGH, HIGH}      // F
};

void setup() {
  // hacer las salidas 
  for (int i = 0; i < 7; i++) {
    pinMode(pinesLed[i], OUTPUT);
  }

  Serial.begin(9600); //hace la comunicacion 
  Serial.println("Introduce un número entre 0 y F para mostrar en el display:");
  pruebaDisplay(); // funcion de los leds 
}

void loop() {
  // leer las entradas
  if (Serial.available() > 0) {
    char input = Serial.read(); // Leer caracter insertado 
    int numero;

    // condicion para ver que salidas dar 
    if (input >= '0' && input <= '9') {
      numero = input - '0';
    } else if (input >= 'A' && input <= 'F') {
      numero = input - 'A' + 10;
    } else if (input >= 'a' && input <= 'f') {
      numero = input - 'a' + 10;
    } else {
      Serial.println("Entrada no valida. Ingresa un numero entre 0 y F.");
      return;
    }

    // mostrar en el display 
    mostrarNumero(numero);
    Serial.print("Número mostrado: ");
    Serial.println(input);
  }
}

// utilizado para mostrar los numeros 
void mostrarNumero(int numero) {
  if (numero >= 0 && numero < 16) {
    Serial.print("Mostrando número: ");
    Serial.println(numero);
    for (int i = 0; i < 7; i++) {
      digitalWrite(pinesLed[i], numeros[numero][i]);
      Serial.print("Segmento ");
      Serial.print(i);
      Serial.print(": ");
      Serial.println(numeros[numero][i] == HIGH ? "ENCENDIDO" : "APAGADO");
    }
  }
}

// prueba del display 
void pruebaDisplay() {
  Serial.println("Probando segmentos uno por uno...");
  for (int i = 0; i < 7; i++) {
    digitalWrite(pinesLed[i], HIGH);
    Serial.print("Segmento ");
    Serial.print(i);
    Serial.println(" ENCENDIDO");
    delay(500);
    digitalWrite(pinesLed[i], LOW);
  }

  Serial.println("Mostrando números del 0 al F...");
  for (int i = 0; i <= 15; i++) {
    mostrarNumero(i);
    delay(300);
  }
}
