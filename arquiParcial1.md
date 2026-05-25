# Resumen — Ciclos de captación, interrupciones y arquitectura de buses

# 1. Ciclo de instrucción

La CPU ejecuta programas repitiendo continuamente dos etapas:

1. Captar la instrucción
2. Ejecutarla

Ese proceso se llama ciclo de instrucción.

---

# 2. Registros importantes de la CPU

## PC — Program Counter
Guarda la dirección de la próxima instrucción.

Ejemplo:
Si PC = 300, la CPU va a buscar la instrucción en la memoria 300.

---

## IR — Instruction Register
Guarda la instrucción que se está ejecutando actualmente.

---

## AC — Acumulador
Registro temporal donde la CPU guarda datos y resultados.

---

# 3. Codop y dirección

Las instrucciones están divididas en:

| Parte | Función |
|---|---|
| Codop | Dice qué operación hacer |
| Dirección | Indica dónde está el dato |

Ejemplo:

1940

- 1 → cargar
- 940 → dirección de memoria

Significa:

Cargar en AC el dato guardado en la posición 940

---

# 4. Estados del ciclo de instrucción

1. IAC → Instruction Address Calculation  
   → Cálculo de la dirección de instrucción

2. IF → Instruction Fetch  
   → Captación de instrucción

3. IOD → Instruction Operation Decoding  
   → Decodificación de la operación de la instrucción

4. OAC → Operand Address Calculation  
   → Cálculo de la dirección del operando

5. OF → Operand Fetch  
   → Captación de operando

6. DO → Data Operation  
   → Operación con datos

7. OS → Operand Store  
   → Almacenamiento de operando

---

# 5. Tipos de operaciones que puede hacer la CPU

## Procesador ↔ Memoria
Mover datos entre CPU y memoria.

## Procesador ↔ E/S
Mover datos con dispositivos externos.

## Procesamiento de datos
Operaciones aritméticas y lógicas.

## Control
Cambiar la secuencia del programa (saltos).

---

# 6. Interrupciones

Una interrupción ocurre cuando otro componente le pide atención a la CPU.

Sirven para evitar que el procesador quede esperando mientras un dispositivo lento trabaja.

---

# 7. Tipos de interrupciones

| Tipo | Ejemplo |
|---|---|
| Programa | división por cero |
| Temporización | temporizador |
| E/S | terminó una impresión |
| Hardware | error físico |

---

# 8. Qué hace la CPU cuando ocurre una interrupción

## 1. Guarda el contexto actual
La CPU guarda información importante del programa para poder continuar después donde quedó.

## 2. Suspende el programa
El programa actual se pausa temporalmente.

## 3. Ejecuta el gestor de interrupción
La CPU ejecuta una rutina especial para atender la interrupción.

## 4. Atiende el problema
Se realiza la acción necesaria según el dispositivo o error.

## 5. Vuelve al programa original
La CPU recupera el contexto guardado y continúa normalmente.

---

# 9. Interrupciones múltiples

Puede haber varias interrupciones al mismo tiempo.

## Desactivar interrupciones
La CPU atiende una por vez.

## Prioridades
Una interrupción importante puede interrumpir a otra menos importante.

---

# 10. Entrada y salida (E/S)

Los módulos de E/S permiten comunicar la computadora con dispositivos externos:

- teclado
- impresora
- disco
- etc.

---

# 11. DMA — Direct Memory Access

Permite transferir datos directamente entre memoria y dispositivos sin usar constantemente la CPU.

---

# 12. Estructura de interconexión

Los componentes principales son:

- CPU
- Memoria
- Módulos de E/S

Todos se comunican mediante líneas de conexión.

---

# 13. Bus

Un bus es un conjunto de líneas compartidas que conectan los componentes.

---

# 14. Tipos de buses

## Bus de datos
Transporta datos.

## Bus de direcciones
Indica origen o destino.

## Bus de control
Coordina señales y operaciones.

---

# 15. Señales importantes del bus

- Memory Read: lee un dato desde memoria.
- Memory Write: escribe un dato en memoria.
- I/O Read: lee un dato desde un dispositivo de E/S.
- I/O Write: envía un dato a un dispositivo de E/S.
- Transfer ACK: confirma la transferencia.
- Bus Request: solicita usar el bus.
- Bus Grant: concede el uso del bus.
- Interrupt Request: indica una interrupción pendiente.
- Interrupt ACK: confirma la interrupción.
- Clock: sincroniza las operaciones.
- Reset: reinicia el sistema.

---

# Resumen — Introducción a Memorias

# 1. Concepto de memoria

Las memorias se usan para:
- almacenar datos
- almacenar instrucciones

---

# 2. Características de las memorias

Las memorias se diferencian por:
- ubicación
- capacidad
- método de acceso
- prestaciones
- soporte físico
- organización

---

# 3. Ubicación

## Interna
Dentro de la computadora.

Ejemplos:
- registros
- caché
- RAM

## Externa
Dispositivos conectados mediante E/S.

Ejemplos:
- discos
- cintas

---

# 4. Capacidad

Indica cuánto puede almacenar una memoria.

Se expresa en:
- bytes
- palabras

---

# 5. Unidad de transferencia

## Memoria interna
Transfiere palabras.

## Memoria externa
Transfiere bloques.

---

# 6. Métodos de acceso

## Secuencial
Acceso uno por uno.

## Directo
Acceso aproximado y luego búsqueda.

## Aleatorio
Acceso directo a cualquier posición.

## Asociativo
Busca por contenido y no por dirección.

---

# 7. Prestaciones

## Tiempo de acceso
Tiempo para leer o escribir.

## Tiempo de ciclo
Tiempo mínimo entre accesos.

## Velocidad de transferencia
Velocidad de envío de datos.

---

# 8. Soportes físicos

- semiconductores
- magnéticos
- ópticos
- magneto-ópticos

---

# 9. Características físicas

## Volátil
Pierde datos sin energía.

## No volátil
Mantiene datos sin energía.

## ROM
Memoria solo lectura.

---

# 10. Organización

Forma en que los bits forman palabras.

---

# 11. Jerarquía de memorias

Busca equilibrio entre:
- capacidad
- velocidad
- costo

---

# 12. Idea de jerarquía

Se combinan memorias:
- rápidas y pequeñas
- lentas y grandes

---

# 13. Localidad referencial

Los datos más usados se mantienen en memorias rápidas.

---

# 14. Tipos de memoria

## Registros
Más rápidos y pequeños.

## Caché
Intermedia entre CPU y RAM.

## RAM
Memoria principal.

## Memoria masiva
Discos, SSD, pendrives.

## Memoria externa
Almacenamiento permanente.

---

# 15. Caché

- pequeña
- rápida
- mejora rendimiento
- guarda datos frecuentes

---

# 16. RAM

- memoria principal
- acceso aleatorio
- volátil

---

# 17. Ejemplo de jerarquía

Si el dato está en caché:
- acceso rápido

Si no:
- se busca en memoria lenta
- luego se copia al nivel rápido

---

# Resumen — Memoria Caché

# 1. ¿Por qué existe la memoria caché?

La CPU es mucho más rápida que la memoria principal.

La caché aparece para:
- acelerar accesos a memoria
- mejorar el rendimiento del sistema

---

# 2. ¿Qué es la memoria caché?

Es una memoria:

- pequeña
- muy rápida
- ubicada entre CPU y RAM

Guarda copias de datos usados frecuentemente.

---

# 3. Funcionamiento básico

## Si el dato está en caché
La CPU lo obtiene rápidamente.

→ Hit (acierto)

## Si el dato NO está
Se trae un bloque desde RAM hacia caché.

→ Miss (falla)

El dato pasa a caché cuando ocurre una falla de caché.

O sea:

1. La CPU pide un dato.
2. La caché revisa si lo tiene.
3. Si NO está:
   - lo busca en RAM
   - trae el bloque completo
   - lo guarda en caché

RAM → bloque con datos → caché

No es un bloque vacío.

---

## Ejemplo

La CPU pide el dato 22.

### Primera vez
- caché NO lo tiene
- se busca en RAM
- se trae el bloque:

20 21 22 23

- ese bloque se guarda en caché

### Segunda vez
Si la CPU vuelve a pedir 22:
- ya está en caché
- acceso rápido (hit)

La caché guarda temporalmente datos usados recientemente porque probablemente vuelvan a utilizarse.

---

# 4. Localidad de referencia

Si un dato fue usado recientemente:
- probablemente vuelva a usarse
- o se usen datos cercanos

Por eso se cargan bloques completos y no una sola palabra.

---

# 5. Estructura de la caché

## Memoria principal
Está dividida en bloques.

## Caché
Está dividida en líneas.

Cada línea contiene:
- palabras
- etiqueta (tag)

La etiqueta identifica qué bloque está guardado ahí.

---

# 6. Operación de lectura

La CPU genera una dirección.

## Si hay acierto
La caché entrega el dato directamente.

## Si hay falla
El bloque se copia desde RAM a caché y luego a la CPU.

---

# 7. Tipos de carga ante una falla

## Load Through
Primero se envía el dato a la CPU y después se completa la carga del bloque.

## Load Back
Primero se completa la carga en caché y luego se entrega a la CPU.

---

# 8. Elementos de diseño de caché

La caché se diseña considerando:
- tamaño
- correspondencia
- reemplazo
- escritura
- tamaño de línea
- cantidad de cachés

---

# 9. Tamaño de caché

Se busca equilibrio entre:
- velocidad
- costo
- capacidad

Más caché:
- mejora rendimiento
- aumenta costo

---

# 10. Función de correspondencia

Define dónde puede ubicarse un bloque de RAM dentro de caché.

Tipos:
- directa
- asociativa
- asociativa por conjuntos

---

# 11. Correspondencia directa

Cada bloque de RAM puede ir solamente a una línea específica de caché.

## Ventaja
- simple
- barata

## Desventaja
Dos bloques pueden pelear por la misma línea constantemente.

---

# 12. Correspondencia asociativa

Un bloque puede ir a cualquier línea.

## Ventaja
- flexible
- mejor tasa de aciertos

## Desventaja
- hardware complejo

---

# 13. Correspondencia asociativa por conjuntos

La caché se divide en conjuntos.

Un bloque puede ir a cualquier línea dentro de su conjunto.

Combina:
- simplicidad de directa
- flexibilidad de asociativa

---

# 14. Algoritmos de sustitución

## LRU
Reemplaza el menos usado recientemente.

## LFU
Reemplaza el menos usado frecuentemente.

## FIFO
Sale el primero que entró.

## Aleatorio
Reemplazo al azar.

---

# 15. Políticas de escritura

## Write Through
Escribe en caché y RAM al mismo tiempo.

## Write Back
Primero escribe en caché y después en RAM.

## Write Allocate
Carga el bloque en caché antes de escribir.

## Write No Allocate
Escribe directo en RAM.

---

# 16. Coherencia de caché

Si una caché modifica un dato,
las demás deben actualizarse o invalidarse.

---

# 17. Tamaño de línea

Bloques grandes:
- mejoran aciertos
- aprovechan localidad

Pero:
- ocupan más espacio
- reemplazan más datos

---

# 18. Caché multinivel

Puede haber:
- L1
- L2
- L3

## L1
Más rápida y pequeña.

---

# 19. Caché unificada y partida

## Unificada
Guarda datos e instrucciones.

## Partida
Separada en:
- datos
- instrucciones

---

# 20. Conceptos importantes

## Hit Rate (HR)
Porcentaje de aciertos.

## Miss Rate (MR)
Porcentaje de fallas.

## Tiempo efectivo de acceso
Tiempo promedio real de acceso.
