# aud5i022-2023-control

* Integrantes:

- Antonio Cerón 
- Gabriela Echenique

* Materiales: 
- Protoboard
- Arduino Uno
- Cables
- Pulsador 
- Luces Led 

* Circuito / Imagenes:
![Foto1](https://user-images.githubusercontent.com/115827031/235255750-0184c919-d8c2-4a52-a76f-c492185469d4.jpg)
Conectamos la protoboard a la entrada GND del arduino con un cable azul y pusimos 4 resistencias de 220.
![Foto2](https://user-images.githubusercontent.com/115827031/235255794-cdbf3ac7-3f38-4b9f-9d16-af7b6a6d3cd4.jpg)
Conectamos 3 led rojos con un cable desde su pie largo a las entradas del arduino 8,9,10,7. Su pie corto fue conectado a las resistencias de 220 previamente mencionadas.
![Foto3](https://user-images.githubusercontent.com/115827031/235255814-791ca391-0e36-4c25-b274-ecb9d1ba22c6.jpg)
Agregamos una cuarta luz led al circuito.
![Foto4](https://user-images.githubusercontent.com/115827031/235255821-e33dc221-ccf8-4c0d-99f7-8138ef4ee703.jpg)
Agregamos un pulsador que active la secuencia, se utilizo un cable rojo para conectar la linea positiva de la protoboard a la entrada de tierra del arduino y un cable rojo que conecte la linea positiva con una de las patas de el pulsador


* Código

//Antonio Ceron
//Gabriela Echenique

// Cronometro de secuencia led accionado mediante a un pulsor

// variable para almacenar estado pulsador
int estadoPulsador = 0;

int pinPulsador = 6;

// variable para conectar LED
int pinLED1 = 8;
int pinLED2 = 9;
int pinLED3 = 10;
int pinLED4 = 7;

void setup() {

  pinMode(pinPulsador, INPUT);

  pinMode(pinLED1, OUTPUT);
  pinMode(pinLED2, OUTPUT);
  pinMode(pinLED3, OUTPUT);
  pinMode(pinLED4, OUTPUT);

  // Abrir comunicacion serial
  Serial.begin(9600);
}

void loop() {

  estadoPulsador = digitalRead(pinPulsador);
  Serial.println(estadoPulsador);

// Se configura para que la secuencia ocurra solo al presionarse el pulsador
  if (estadoPulsador == HIGH) {
    //se enciende la primera luz durante un segundo
    digitalWrite(pinLED1, HIGH);  // enciende
    digitalWrite(pinLED2, LOW);   // apaga
    digitalWrite(pinLED3, LOW);   // apaga
    digitalWrite(pinLED4, LOW);   // apaga
    delay(1000);


    // se apaga la primera luz y se enciende la segunda
    digitalWrite(pinLED1, LOW);
    digitalWrite(pinLED2, HIGH);
    digitalWrite(pinLED3, LOW);
    digitalWrite(pinLED4, LOW);
    delay(1000);

    // se apaga la segunda luz y se enciende la tercera 
    digitalWrite(pinLED1, LOW);
    digitalWrite(pinLED2, LOW);
    digitalWrite(pinLED3, HIGH);
    digitalWrite(pinLED4, LOW);
    delay(1000);
    // se apaga la tercera luz y se enciende la cuarta
    digitalWrite(pinLED1, LOW);
    digitalWrite(pinLED2, LOW);
    digitalWrite(pinLED3, LOW);
    digitalWrite(pinLED4, HIGH);
    delay(1000);

    // En caso de no apretar el pulsador todas las luces permaneceran apagadas
  } else {
    digitalWrite(pinLED1, LOW);
    digitalWrite(pinLED2, LOW);
    digitalWrite(pinLED3, LOW);
    digitalWrite(pinLED4, LOW);
  }
}


* Conclusiones: 

- La programación en arduino permite entre muchas otras cosas la elaboración de mecanismos que funcionen para medir un tiempo determinado. En este caso mediante luces realizando una secuencia, podemos medir el paso de los segundos mientras se presiona un pulsador. Si una luz se encuentra en el mismo carril que las patitas de el pulsador, esta no encendera, tuvimos un problema con esto y lo solucionamos notando esta condición de la placa.

* Inspiracion: 

- Ejemplo clase 02; Semáforo
- Ejemplo clase 04; Pulsador 
- Video Secuencia de Leds con Arduino - Ivan Espinoza YT
- Practicasconarduino.cl

* https://github.com/jibbx/AV-ERDDEL
