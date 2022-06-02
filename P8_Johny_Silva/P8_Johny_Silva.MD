# Johny Silva Mendes
# PRACTICA 8: Buses de Comunicación IV (UART)


## BUCLE DE COMUNICACIÓN UART2

### FUNCIONAMIENTO DEL PROGRAMA 

**Setup:**
Se crea un objeto de la clase *Serial*, el cual se configura a un baut rate de 9600. Luego se crea un segundo objeto como el anterior, *Serial2*.

```cs
#include <Arduino.h>

void setup() {
    Serial.begin(9600);
    Serial2.begin(9600);
    Serial.write("Inicializando...");
}
  ```

**Loop:**
En la función loop se comprueba primero que todo si el objeto *Serial* tiene alguna información disponible para leer desde el serial port de UART0 mediante la función "available()".

Ahora se podrá escribir información la cual se guardaría en el buffer. Esta información se escribirá en el UART2 mediante *write()*. Se hará lo mismo pero aplicando la función *available()* con el objeto *Serial2* y copiando la información almacenada en el buffer en el UART0 con la función *write()*.  

 ```cs
void loop() {
  if(Serial.available()){
    Serial2.write(Serial.read());
    delay(10);
    if(Serial2.available()){
      Serial.write(Serial2.read());
    }
  }
}
  ```


### **Código entero:**
```cpp
#include <Arduino.h>

void setup(){
    serial.begin(9600);
    serial2.begin(9600);
    serial.write("Inicializando...");
}

void loop (){
if(Serial.available()){
    serial2.write(Serial.read());
    delay(10);
    if(serial2.available()){
        serial.write(Serial2.read());
    }
}
}
```

### Salidas y Entradas

La salida y la entrada de la consola coinciden

**Salidas:**
```cpp
Inicializando...�Practica 8 Bucle de comunicación UART2. 
```

**Entradas:**
```cpp
Practica 8 Bucle de comunicación UART2.
```
El texto dependría de la información que se escriba y se guarde en el buffer.