Apunte_Arqui2_Recu1

LA FUNCION BASICA DE UN COMPUTADOR ES EJECUTAR UN PROGRAMA ACOMPAÑADO DE INSTRUCCIONES GUARDADAS EN MEMORIA. EL PROCESADOR EJECUTA ESTAS INSTRUCCIONES.

LA CPU SIEMPRE INCREMENTA EL PC DESPUES DE CAPTAR CADA INSTRUCCION, ES DECIR YA ESTA POSICIONADO EN LA PROXIMA INSTRUCCION.

LA INSTRUCCION CAPTADA SE ALMACENA EN UN REGISTRO DE LA CPU LLAMADA IR Y ES TRADUCIDO A CODIGO BINARIO Y LA CPU LLEVA A CABO X ACCION:

PROCESADOR-MEMORIA.
PROCESADOR-E/S.
PROCESAMIENTO DE DATOS.
CONTROL.

LA EJECUCION DE UNA INSTRUCCION PUEDE IMPLICAR UNA COMBINACION DE LAS ANTERIORES.

Codop y dirección

| Parte     | Para qué sirve                                          |
| --------- | ------------------------------------------------------- |
| Codop     | Dice QUÉ operación hacer                                |
| Dirección | Dice CON QUÉ dato o en qué posición de memoria trabajar |

Codop: Es el código que entiende la CPU para saber qué acción ejecutar.

| Codop | Acción                        |
| ----- | ----------------------------- |
| 0001  | Cargar AC desde memoria       |
| 0010  | Guardar AC en memoria         |
| 0101  | Sumar a AC un dato de memoria |

Dirección: Dice CON QUÉ dato o en qué posición de memoria trabajar

Ejemplo REAL de la diapositiva

Aparece esta instrucción: 1940

La CPU la separa así:

| Parte | Valor     |
| ----- | --------- |
| 1     | codop     |
| 940   | dirección |

Entonces:

el 1 significa:

“Cargar AC desde memoria”

el 940 significa:

“usá el dato que está en la dirección 940”

Estados del ciclo de instrucción

IAC → Instruction Address Calculation
→ Cálculo de la dirección de instrucción

IF → Instruction Fetch
→ Captación de instrucción

IOD → Instruction Operation Decoding
→ Decodificación de la operación de la instrucción

OAC → Operand Address Calculation
→ Cálculo de la dirección del operando

OF → Operand Fetch
→ Captación de operando

DO → Data Operation
→ Operación con datos

OS → Operand Store
→ Almacenamiento de operando

5. Tipos de operaciones que puede hacer la CPU
   Procesador ↔ Memoria

Mover datos entre CPU y memoria.

Procesador ↔ E/S

Mover datos con dispositivos externos.

Procesamiento de datos

Operaciones aritméticas y lógicas.

Control

Cambiar la secuencia del programa (saltos).

Interrupciones

Una interrupción ocurre cuando otro componente le pide atención a la CPU.
Sirven para evitar que el procesador quede esperando mientras un dispositivo lento trabaja.

Tipos de interrupciones

| Tipo          | Ejemplo               |
| ------------- | --------------------- |
| Programa      | división por cero     |
| Temporización | temporizador          |
| E/S           | terminó una impresión |
| Hardware      | error físico          |

Qué hace la CPU cuando ocurre una interrupción

1. Guarda el contexto actual

   La CPU guarda en memoria información importante del programa que estaba ejecutando, como el valor del PC, para poder continuar después exactamente donde quedó.

2. Suspende el programa

   El programa actual se pausa temporalmente para atender la interrupción.

3. Ejecuta el gestor de interrupción

   La CPU salta a una rutina especial llamada “gestor de interrupción”, encargada de atender el evento ocurrido.

4. Atiende el problema

   El gestor identifica qué dispositivo o situación generó la interrupción y realiza la acción necesaria.

5. Vuelve al programa original

   Cuando termina el gestor de interrupción, la CPU recupera el contexto guardado y continúa ejecutando el programa normal.

Interrupciones múltiples

Puede haber varias interrupciones al mismo tiempo.

Dos opciones:

Desactivar interrupciones

La CPU atiende una por vez.

Prioridades

Una interrupción importante puede interrumpir a otra menos importante.

Los módulos de E/S permiten comunicar la computadora con dispositivos externos:

teclado
impresora
disco
etc.

DMA — Direct Memory Access

Permite que un módulo de E/S transfiera datos directamente con la memoria sin usar constantemente la CPU.

Estructura de interconexión

Los componentes principales son:

CPU
Memoria
Módulos de E/S

Todos deben comunicarse entre sí mediante líneas de conexión.

Bus

Un bus es un conjunto de líneas compartidas que conectan los componentes de la computadora.

Tipos de buses

Bus de datos

    Transporta datos.

Bus de direcciones

    Indica origen o destino.

Bus de control

    Coordina operaciones y señales.

Señales importantes del bus

    Memory Read: lee un dato desde memoria.
    Memory Write: escribe un dato en memoria.
    I/O Read: lee un dato desde un dispositivo de E/S.
    I/O Write: envía un dato a un dispositivo de E/S.
    Transfer ACK: confirma que la transferencia se realizó.
    Bus Request: un módulo solicita usar el bus.
    Bus Grant: se concede el uso del bus.
    Interrupt Request: indica una interrupción pendiente.
    Interrupt ACK: confirma que la interrupción fue aceptada.
    Clock: sincroniza las operaciones del sistema.
    Reset: reinicia los módulos del sistema.
