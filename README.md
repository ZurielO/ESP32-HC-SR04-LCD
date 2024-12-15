# ESP32-HC-SR04-LCD
Reporte de Práctica: Medición de Distancia con Sensor Ultrasonido y Pantalla LCD


## Objetivo
El objetivo de esta práctica es medir la distancia utilizando un sensor ultrasónico (HC-SR04) y mostrar el resultado en una pantalla LCD a través de la plataforma de simulación Wokwi. El valor de la distancia también se envía a través del puerto serial para su visualización en la consola.

## Materiales Utilizados

- Sensor ultrasónico (HC-SR04)
- Pantalla LCD con comunicación I2C
- Placa Arduino (simulada en Wokwi)
- Conexión a la plataforma Wokwi para la simulación
  
## Descripción del Código:

### Definición de Pines y Librerías:

El código comienza con la definición de los pines para el sensor ultrasónico: Trigger (pin 4) y Echo (pin 15).

Se incluye la librería **LiquidCrystal_I2C** que facilita la comunicación con la pantalla LCD a través del bus I2C.

Se establecen las configuraciones para la pantalla LCD, definiendo la dirección I2C (I2C_ADDR = 0x27) y las dimensiones de la pantalla (20 columnas y 4 filas).
Función setup():

Se inicializa la comunicación serial a 9600 baudios con Serial.begin(9600) para permitir la transmisión de datos a través del puerto serial.

Los pines Trigger y Echo se configuran como salida e entrada, respectivamente, usando pinMode().

El pin Trigger se establece en LOW para garantizar que esté en estado bajo al iniciar el programa.

La pantalla LCD se inicializa con lcd.init() y el retroiluminado se activa usando lcd.backlight().
Función loop():


Dentro del bucle principal loop(), se definen dos variables: t para almacenar el tiempo que tarda en llegar el eco del sensor y d para almacenar la distancia calculada.

Se genera un pulso de disparo de 10 microsegundos en el pin Trigger con digitalWrite(Trigger, HIGH) y delayMicroseconds(10).

Luego, el pin Trigger se pone en LOW para finalizar el pulso.

Usando la función pulseIn(), se mide el tiempo que tarda el eco en regresar al pin Echo, y se calcula la distancia en centímetros dividiendo el tiempo (t) entre 59. La constante 59 proviene de la velocidad del sonido en el aire (343 metros por segundo), que se ajusta para obtener la distancia en centímetros.

El valor calculado de la distancia se muestra en la pantalla LCD en la primera línea.

En la pantalla LCD también se imprimen mensajes estáticos como "MODULO V", "AIyM", "Zuriel Osio", e "I.E.E." en diferentes intervalos, cada uno acompañado de una pausa de 2 segundos (delay(2000)).

Finalmente, la distancia medida también se envía al monitor serial para su visualización.

![Texto alternativo](https://github.com/ZurielO/ESP32-HC-SR04-LCD/blob/main/imagen_2024-12-15_165455011.png).

![Texto alternativo](https://github.com/ZurielO/ESP32-HC-SR04-LCD/blob/main/imagen_2024-12-15_165522309.png).

## Flujo de Ejecución:

En cada iteración del bucle loop(), se mide la distancia con el sensor ultrasónico, se actualiza la pantalla LCD con la nueva distancia, y el valor también se envía al monitor serial.
Se alternan otros mensajes personalizados en la pantalla LCD entre las mediciones de distancia.
La función delay(2000) asegura que los mensajes en la pantalla LCD sean visibles durante un intervalo adecuado.
Explicación de las Funciones:

pulseIn(Echo, HIGH): Esta función mide el tiempo que tarda el pin Echo en recibir el pulso de retorno del sensor ultrasónico. El tiempo medido es proporcional a la distancia.

lcd.setCursor(x, y): Permite mover el cursor a una posición específica de la pantalla LCD (columna x, fila y), donde se imprimirá el texto.

lcd.print(): Imprime un texto o valor en la pantalla LCD en la posición del cursor.

Serial.print(): Imprime los valores de distancia en el monitor serial, permitiendo al usuario visualizar las mediciones en tiempo real.


## Resultados 

En la pantalla LCD se muestra el valor de la distancia medida en centímetros en la primera línea. Los mensajes personalizados ("MODULO V", "AIyM", "Zuriel Osio", "I.E.E.") se alternan entre las mediciones.
El valor de la distancia también se imprime en el monitor serial cada vez que se realiza una medición.
Conclusiones:

El código demuestra cómo utilizar un sensor ultrasónico para medir la distancia y cómo visualizar esos datos en una pantalla LCD usando la comunicación I2C.
La plataforma Wokwi es útil para simular y probar circuitos electrónicos sin necesidad de hardware físico, permitiendo experimentar con sensores y componentes de manera virtual.
El uso de la función pulseIn() para medir el tiempo de regreso del pulso es eficiente para calcular la distancia del objeto.


![Texto alternativo](https://github.com/ZurielO/ESP32-HC-SR04-LCD/blob/main/imagen_2024-12-15_165309684.png).
