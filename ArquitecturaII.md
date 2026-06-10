---
title: "Arquitectura II"
subtitle: "Verdadero / Falso (1 al 8) y Ejercicios de Caché"
author: "Apuntes de cátedra"
date: "2026-05-06"
lang: "es-AR"
---

# Arquitectura II

> Resumen completo con teoría, verdadero/falso y ejercicios resueltos.

## Índice
- [Parte 0 - Teoría esencial](#parte-0---teoría-esencial)
- [Parte 1 - Verdadero / Falso](#parte-1---verdadero--falso)
- [Parte 2 - Ejercicios](#parte-2---ejercicios-de-memoria-caché)

---

## Parte 0 - Teoría esencial

### Interrupciones
- **IRQ (enmascarables):** la CPU puede ignorarlas.
- **NMI (no enmascarables):** no se pueden deshabilitar. Para errores críticos.

### DMA
Permite transferir datos a RAM sin CPU.
1. Ráfaga: CPU cede el bus completo.
2. Robo de ciclo: toma 1 ciclo por vez.
3. Transparente: usa ciclos libres del bus.

### Complemento a dos
Rango con n bits: de -2^(n-1) a 2^(n-1)-1
Ejemplo 4 bits: 1001 = -7 (invertir 0110 + 1)

### IEEE 754 (1985)
Estándar de coma flotante. Simple: 1 bit signo, 8 exponente, 23 mantisa.

### Memoria Caché
- Hit rate H = aciertos / accesos
- Tiempo medio: Ts = T1 + (1-H) * T2
- Mapeo directo: etiqueta + línea + offset
- Asociativo: etiqueta + offset

---

## Parte 1 - Verdadero / Falso

1) NMI no pueden aplazarse
**Respuesta: ✅ VERDADERO**

2) DMA es polling
**Respuesta: ❌ FALSO** - Eso es E/S programada.

3) DMA solo tiene un modo
**Respuesta: ❌ FALSO** - Tiene 3 modos.

4) Robo de ciclos usa semiciclos
**Respuesta: ✅ VERDADERO**

5) 1001 en C2 es 9
**Respuesta: ❌ FALSO** - Es -7.

6) Negación es complemento a uno +1
**Respuesta: ✅ VERDADERO**

7) Desde 1985 se usa punto fijo
**Respuesta: ❌ FALSO** - Es IEEE 754.

8) Overflow de exponente existe
**Respuesta: ✅ VERDADERO**

---

## Parte 2 - Ejercicios

### Ejercicio 1
Ts = 1 + (1-0,9) * 10 = 1 + 1 = 2 ns

### Ejercicio 2
Ts = 1 + (1-0,975) * 10 = 1 + 0,25 = 1,25 ns

### Ejercicio 3 - Mapeo directo
- MP: 256M = 2^28 → 28 bits
- Offset: log2(256) = 8 bits
- Líneas: 4096 → 12 bits
- Etiqueta: 28-12-8 = 8 bits
Formato: | Etiqueta 8 | Línea 12 | Palabra 8 |
Bloques MP: 1.048.576

### Ejercicio 4 - Asociativo
- Offset: 8 bits
- Etiqueta: 20 bits
Formato: | Etiqueta 20 | Palabra 8 |

### Ejercicio 5
- a) bloque = 64 bytes
- b) 20 = 5 + (1-H)*200
   1-H = 15/200 = 0,075
   H = 0,925 = 92,5%

### Ejercicio 6
- a) Memoria: 2^32 bytes = 4096 MB
- b) Líneas: 4096, Palabras totales: 16384
- c) Líneas por conjunto: 4
- d) Número de líneas: 4096
- e) Conjuntos: 1024
- f) 10 = 2 + (1-H)*80 → H = 0,9 = 90%

### Ejercicio 7
1) H = 600000/1200000 = 0,5
   Ts = 120 + 0,5*1260 = 750 ns
2) Campos:
   - MP 8MB = 2^23 → 23 bits
   - Offset: 8 bits
   - Líneas: 4 bits
   - Etiqueta: 11 bits
Formato: | Etiqueta 11 | Línea 4 | Offset 8 |


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


# Resumen — Memoria Interna

# 1. Memoria principal

La memoria principal utiliza tecnología semiconductora.

Su elemento básico es la celda de memoria.

---

# 2. Celda de memoria

Cada celda:

- representa 0 o 1
- puede escribirse
- puede leerse

Tiene dos estados estables para almacenar bits.

---

# 3. Funcionamiento de una celda

## Selección
Elige la celda que se va a usar.

## Control
Indica si será lectura o escritura.

## Escritura
Coloca un 0 o un 1 en la celda.

## Lectura
Obtiene el valor almacenado.

---

# 4. Memoria RAM

RAM significa:

Random Access Memory

(acceso aleatorio)

Se puede acceder directamente a cualquier posición de memoria.

---

# 5. Características de la RAM

- lectura y escritura
- volátil
- almacenamiento temporal
- rápida
- usa señales eléctricas

Guarda:
- programas en ejecución
- datos usados actualmente

---

# 6. Tipos de RAM

## SRAM
RAM estática.

Basada en flip-flops.

## DRAM
RAM dinámica.

Basada en transistores y capacitores.

---

# 7. DRAM

La DRAM:

- almacena cargas eléctricas
- usa capacitores
- necesita refrescos periódicos
- se usa como memoria principal

La carga eléctrica se pierde con el tiempo aunque siga encendida.

---

# 8. SRAM

La SRAM:

- usa biestables
- es más rápida
- no necesita refrescos
- mantiene datos mientras tenga energía

---

# 9. SRAM vs DRAM

## DRAM
- más barata
- más densa
- más lenta
- necesita refresco
- usada como memoria principal

## SRAM
- más rápida
- más cara
- usada en caché

---

# 10. Memoria ROM

ROM significa:

Read Only Memory

(memoria de solo lectura)

Contiene datos permanentes y no volátiles.

---

# 11. Funciones de la ROM

La ROM:

- almacena configuraciones básicas
- ayuda al arranque de la PC
- activa periféricos
- guarda programas permanentes

---

# 12. PROM

PROM:
- programable una sola vez
- no volátil
- escritura eléctrica

---

# 13. EPROM

EPROM:
- puede borrarse con luz ultravioleta
- puede reprogramarse
- el borrado afecta todo el chip

---

# 14. EEPROM

EEPROM:
- borrado eléctrico
- permite actualizar bytes específicos
- más flexible

---

# 15. Memoria Flash

La memoria Flash:

- usa borrado eléctrico
- es rápida
- puede borrar bloques completos

---

# 16. RAM vs ROM

## RAM
- lectura y escritura
- volátil
- temporal

## ROM
- solo lectura
- no volátil
- permanente

---

# 17. Errores en memoria

## Fallo permanente
Daño físico en la memoria.

Puede dejar bits “pegados” en 0 o 1.

## Error transitorio
Error temporal sin daño físico.

Puede deberse a problemas eléctricos.

---

# 18. Corrección de errores

Se agregan bits extra llamados códigos de error.

Sirven para:
- detectar errores
- corregir algunos errores

Cuando se lee la memoria:
- se recalcula el código
- se compara con el guardado

---

# 19. Resultados posibles al verificar errores

## Sin errores
Los datos se usan normalmente.

## Error corregible
El sistema corrige el dato.

## Error no corregible
El sistema informa el problema.

---

# 20. SDRAM

SDRAM:
- funciona sincronizada con el reloj
- trabaja a la velocidad del bus
- reduce tiempos de espera

---

# 21. DDR SDRAM

DDR:
- envía datos dos veces por ciclo
- más rápida
- más económica

---

# 22. RDRAM

RDRAM:
- muy rápida
- muy costosa
- reemplazada por DDR

---

# 23. CDRAM

CDRAM:
- puede funcionar como caché
- sirve como buffer de datos

  # Resumen — Memoria Externa

# 1. Definición

La memoria externa o auxiliar incluye todos los dispositivos de almacenamiento que no forman parte de la memoria interna (RAM y ROM).

Se usa para:
- almacenamiento masivo
- almacenamiento permanente
- guardar datos e información

Es:
- no volátil
- de gran capacidad
- más lenta que la memoria principal

No es fundamental para que la computadora funcione.

Ejemplos:
- discos duros
- SSD
- pendrives
- CDs
- DVDs

---

# 2. Tecnologías de almacenamiento

Existen distintos tipos de tecnologías para almacenar información.

---

# 3. Almacenamiento magnético

Utiliza propiedades magnéticas para guardar datos.

Ejemplos:
- disquete
- disco duro
- cinta magnética

Características:
- gran capacidad
- almacenamiento tradicional
- usa magnetismo para leer y escribir

---

# 4. Almacenamiento óptico

Usa rayos láser para leer y escribir información.

La información se almacena en surcos microscópicos sobre discos.

Ejemplos:
- CD
- DVD

Características:
- tecnología digital
- lectura óptica mediante láser

---

# 5. Almacenamiento magneto-óptico

Combina:
- magnetismo
- tecnología óptica

Permite:
- escribir
- reescribir datos

Ejemplos:
- Disco Zip
- Floptical
- Minidisc

---

# 6. Almacenamiento de estado sólido

SSD significa:

Solid State Drive

Usa memoria no volátil para almacenar datos.

Características:
- más rápido
- silencioso
- resistente a golpes
- menor tiempo de acceso
- menor latencia

Ejemplos:
- memorias USB
- tarjetas de memoria
- discos SSD

---

# 7. RAID

RAID es un sistema que usa varios discos trabajando juntos como una sola unidad lógica.

Puede usar:
- discos duros
- SSD

Objetivos:
- mejorar rendimiento
- aumentar capacidad
- tolerar fallos
- mejorar integridad de datos

---

# 8. Beneficios de RAID

- mayor integridad
- tolerancia a fallos
- mejor velocidad de transferencia
- mayor capacidad

Se usa principalmente en servidores.

---

# 9. Tipos de RAID

## RAID 0
Conjunto dividido.

Mejora velocidad.

No tiene tolerancia a fallos.

---

## RAID 1
Conjunto en espejo.

Duplica los datos en varios discos.

Mayor seguridad.

---

## RAID 5
Conjunto dividido con paridad distribuida.

Combina:
- rendimiento
- tolerancia a fallos

---

# 10. Actualidad

## HDD
Siguen siendo importantes por su capacidad y costo.

---

## SSD
Cada vez reemplazan más a los HDD porque:
- son más rápidos
- tienen menor latencia
- son más resistentes

---

## RAID
Muy utilizado en servidores y sistemas grandes.

---

## Medios ópticos
Perdieron popularidad frente al almacenamiento sólido.

---

## Disquetes
Prácticamente desaparecieron con la llegada de las memorias USB.

# Unidad 6 - Segundo Parcial
## Direccionamiento, Formato de Instrucciones y Ensamblador

> Apuntes para segundo parcial - Arquitectura II

## Índice
- [1. Modos de Direccionamiento](#1-modos-de-direccionamiento)
- [2. Formato de Instrucción](#2-formato-de-instrucción)
- [3. Lenguaje Ensamblador](#3-lenguaje-ensamblador)

---

## 1. Modos de Direccionamiento

### Clasificación general
- **Con datos:** inmediato, directo, indirecto
- **Sin datos:** implícito

### Principales modos
1. **INMEDIATO:** el operando está en la instrucción. Ej: `LDA #5`
2. **DIRECTO / ABSOLUTO:** dirección completa en instrucción. Ej: `LDA $2000`
3. **INDIRECTO:** la instrucción tiene la dirección de la dirección. Ej: `LDA ($2000)`
4. **REGISTRO:** operando en registro. Ej: `ADD A,B`
5. **REGISTRO INDIRECTO:** registro contiene dirección. Ej: `LDA (X)`
6. **INDEXADO:** dirección = base + índice. Ej: `LDA $1000,X`
7. **RELATIVO:** dirección = PC + desplazamiento. Para saltos.
8. **IMPLÍCITO:** no lleva operando. Ej: `NOP`, `RTS`

### Resumen del PDF
Modos de Direccionamiento 
Clasificación General
Instrucción
con datos
sin datos o dato implícito
dato en memoria
dato en un registro
dirección del dato
dirección de la dirección del dato
en la instrucción
en un registro
dirección efectiva
dirección de referencia
+ desplazamiento
MODO REGISTRO
MODO IMPLICITO o INHERENTE
MODO INDIRECTO
MODO DIRECTO
MODO REGISTRO
INDIRECTO
MODO RELATIVO
MODO ABSOLUTO
si hay datos
¿ dónde están ?
¿ cómo se indica dónde está el dato  ?
¿ cómo se da la dirección del dato ?
(idem M6800)
(modo extendido del M6800)
Formato de Instrución
Código de Operación 
Datos
Los datos pueden ser operandos o direcciones
INMEDIATO
INDEXADO 
R. BASE y DESP.
RELATIVO ppd.
PAGINADO

Modos de Direccionamiento Relativo 
Clasificación General
Modos Relativos
INMEDIATO
INDEXADO
REGIST

---

## 2. Formato de Instrucción

Del PDF Direccionamiento:
Direccionamiento
Direccionamiento en el Pentium
Formatos de instrucciones
Formatos de instrucciones en el Pentium
Unidad 6
Instrucciones   
Direccionamiento y formatos

Direccionamiento
• Los modos de direccionamiento son las diferentes maneras de especificar un operando 
dentro de una instrucción en lenguaje ensamblador.
• El modo de direccionamiento especifica la forma de calcular la dirección de memoria 
efectiva de un operando (EA) mediante el uso de la información contenida en registros y/o 
constantes, contenida dentro de una instrucción de la máquina o en otra parte.
• No existe una forma generalmente aceptada de nombrar a los distintos modos de 
direccionamiento. En particular, los distintos autores y fabricantes de equipos pueden dar 
nombres diferentes para el modo de hacer frente al mismo, o los mismos nombres, a los 
diferentes modos de direccionamiento.
• Un modo de direccionamiento que en una determinada arquitectura se trata como un 
modo de direccionamiento, puede representar la funcionalidad que en otra arquitectura 
está cubierto por dos o más modos de direccionamiento.

2

Direccionamiento
• Todas las arquitecturas de computadores ofrecen más de un modo. La cuestión que surge 
es cómo determina la unidad de control qué modo de direccionamiento se está 
empleando en cada instrucción.
• A menudo, codops diferentes emplearán modos de direccionamiento distintos.
• Uno o más bits del formato de instrucción pueden utilizarse 

Estructura típica:
- **Código de Operación (CO):** 1-2 bytes
- **Modo:** define cómo obtener operando
- **Operando/Dirección:** 0, 1 o 2 bytes

Ejemplo M6800:
- Inherente: 1 byte
- Inmediato: 2 bytes
- Extendido: 3 bytes

---

## 3. Lenguaje Ensamblador

Del PDF Ensamblador:
Unidad 6
Lenguaje ensamblador
Introducción
Estructura programa en Assembler
Simulador
Ejemplos

Introducción
• El lenguaje ensamblador, como cualquier lenguaje de programación, 
es un conjunto de palabras que le indican la computadora lo que 
tiene que hacer. 
• La diferencia fundamental es que cada instrucción escrita en lenguaje 
ensamblador tiene una correspondencia exacta con una operación de 
la CPU. 
• Son operaciones muy sencillas tales como: “Cargar el valor 12 en el registro 
interno B” o “Transferir el contenido del registro interno A al registro interno 
B”.  
• Las palabras del lenguaje ensamblador son nemotécnicos (sirven para 
ayudar a memorizar) que representan el código máquina, lenguaje 
que entiende la CPU. 
2

Lenguaje ensamblador (Assembler)

Lenguaje ensamblador (Assembler)
• El único lenguaje que entienden los procesadores 
es el código máquina, formado por el sistema 
binario.
• El lenguaje ensamblador, lenguaje de 
programación de bajo nivel, expresa las 
instrucciones de una forma más natural al 
hombre a la vez que muy cercana al procesador, 
ya que cada una de esas instrucciones se 
corresponde con otra en código máquina.
• Trabaja con nemónicos, que son grupos de 
caracteres alfanuméricos que simbolizan las 
órdenes o tareas a realizar.
• La traducción de los nemónicos a código máquina 
entendible por el microcontrolador la lleva a cabo 
un programa ensamblador.
• El programa escrito en lenguaje ens

### Elementos
- **Etiquetas:** identifican direcciones
- **Mnemonicos:** ADD, LDA, STA
- **Operandos:** #inmediato, $directo
- **Directivas:** ORG, END, EQU

### Proceso
1. Ensamblador traduce mnemonicos a código máquina
2. Dos pasadas: tabla de símbolos y generación

### Ejemplo
```
ORG $1000
INICIO LDA #10
       STA $2000
       JMP INICIO
END
```

# Unidad 7 - Segundo Parcial
## Organización del Procesador

## Contenido
Unidad 7
Estructura y funcionamiento 
del procesador
Organización del procesador
Organización de los registros
Ciclos de instrucción
Segmentación de instrucciones
Tratamiento de saltos

1 ORGANIZACIÓN DEL PROCESADOR
Ciclo de instrucción básico.
Para comprender la organización del procesador, consideremos los requisitos 
que ha de cumplir:
• Captar instrucción: el procesador lee una instrucción de la memoria 
(registro, caché o memoria principal).
• Interpretar instrucción: la instrucción se decodifica para determinar qué 
acción es necesaria.
• Captar datos: la ejecución de una instrucción puede exigir leer datos de la 
memoria o de un módulo de E/S.
• Procesar datos: la ejecución de una instrucción puede exigir llevar a cabo 
alguna operación aritmética o lógica con los datos.
• Escribir datos: los resultados de una ejecución pueden exigir escribir datos 
en la memoria o en un módulo de E/S.


2 ORGANIZACIÓN DEL PROCESADOR
Logica Aritmetica 
y booleana
Indicadores de 
estado
BUS INTERNO DEL PROCESADOR
UNIDAD DE 
CONTROL
Caminos de control
Unidad Aritmetico Logica
Desplazador
Complementador
REGISTRO
Para hacer estas cosas, es obvio que el procesador necesita almacenar 
algunos datos temporalmente.
Debe recordar la posición de la última instrucción de forma que pueda 
saber de dónde tomar la siguiente. Necesita almacenar instrucciones y 
datos temporalmente mientras una instrucción está ejecutándose. En 
otras palabras, el procesador necesita una pequeña memoria interna.
La Figura de la izquierda presenta una visión un poco más detallada 
del procesador. Se indican los caminos de transferencia de datos y de 
la lógica de control, que incluyen un elemento con el rótulo bus 
interno del procesador. Este elemento es necesario para transferir 
datos entre los diversos registros y la ALU, ya que la ALU en realidad 
solo opera con datos de la memoria interna del procesador. La figura 
muestra también los elementos básicos típicos de la ALU. Observe la 
similitud entre la estructura interna del computador en su totalidad 
y la estructura interna del procesador. En ambos casos hay una 
pequeña colección de elementos principales (computador: 
procesador, E/S, memoria; procesador, unidad de control, ALU, 
registros) conectados por caminos de datos.



3 ORGANIZACIÓN DE LOS REGISTROS
Un computador emplea una jerarquía de memoria. En los niveles más altos de la jerarquía, la memoria es más rápida, más pequeña y más cara (por bit). 
Dentro del procesador hay un conjunto de registros que funciona como un nivel de memoria por encima de la memoria principal y de la caché en la 
jerarquía. Los registros del procesador son de dos tipos:
• Registros visibles por el usuario: permiten al programador de lenguaje máquina o de ensamblador minimizar las referencias a memoria principal por 
medio de la optimización del uso de registros.
• Registros de control y de estado: son utilizados por la unidad de control para controlar el funcionamiento del procesador y por programas privilegiados 
del sistema operativo para controlar la ejecución de programas.
No hay una separación bien definida de registros dentro de estas dos categorías. Por ejemplo, enalgunas máquinas el contador de programa es visible por 
el usuario (por ejemplo, en el Pentium), pero en muchas no lo es. Para el objetivo de la siguiente discusión, no obstante, usaremos estas categorías.
REGISTROS VISIBLES POR EL USUARIO
Un registro visible por el usuario es aquél que puede ser referenciado por medio del lenguaje máquina
que ejecuta el procesador. Podemos clasificarlos en las siguientes categorías:
• Uso general
• Datos
• Direcciones
• Códigos de condición


4 ORGANIZACIÓN DE LOS REGISTROS
Los registros de uso general pueden ser asignados por el programador a diversas funciones. A veces, su uso dentro del repertorio de instrucciones es ortogonal.


# Unidad 8 - Segundo Parcial
## Computadores RISC y Coherencia de Caché

### 1. Coherencia de Caché
La esencia del problema es que pueden existir varias copias del mismo dato en cachés diferentes. Si un procesador actualiza su copia, se produce inconsistencia.

**Políticas de escritura:**
1. Write-back (post-escritura): escribe solo en caché, memoria se actualiza al reemplazar línea.
2. Write-through (escritura directa): escribe en caché y memoria simultáneamente.

### 2. Soluciones de coherencia
- Snooping: cada caché observa el bus
- Directorio: tabla centralizada de estados
- Estados MESI: Modified, Exclusive, Shared, Invalid

### 3. Computadores RISC
Características principales:
1. Conjunto reducido de instrucciones
2. Formato fijo (32 bits)
3. Arquitectura load/store
4. Pipeline profundo
5. Muchos registros

### 4. RISC vs CISC
- RISC: 1 ciclo por instrucción, compilador optimiza
- CISC: instrucciones complejas, microcódigo

# Unidad 8
## Computadores RISC

Coherencia de Cache

Coherencia de Cache

La esencia del del problema de la coherencia de cache se basa 
en que pueden existir varias copias del mismo dato 
simultáneamente en cachés diferentes, y si los procesadores 
actualizan sus copias, puede producirse una visión 
inconsistente de la memoria.
De clases anteriores se definieron dos políticas de escritura 
usuales: 
• Post-escritura (Write back): las operaciones de escritura se 
hacen usualmente solo en la caché. La memoria principal solo 
se actualiza cuando la línea de caché correspondiente se 
reemplaza.
• Escritura directa (Write through): todas las operaciones de 
escritura se realizan en memoria principal a la vez que en la 
caché, asegurándose así que el contenido de la memoria 
principal siempre es válido. 

Coherencia de Cache

De clases anteriores se definieron dos políticas de escritura usuales: 
• Post-escritura (Write back): las operaciones de escritura se hacen usualmente solo en la caché. La memoria principal solo 
se actualiza cuando la línea de caché correspondiente se reemplaza.
• Escritura directa (Write through): todas las operaciones de escritura se realizan en memoria principal a la vez que en la 
caché, asegurándose así que el contenido de la memoria principal siempre es válido. 

Resulta evidente que una política de postescritura puede ocasionar inconsistencia. Si dos cachés contienen la 
misma línea, y la línea se actualiza en una caché, la otra caché tendrá un valor no válido. Las lecturas siguientes a 
dicha línea producirán resultados no válidos. 
Incluso con la política de escritura directa puede existir inconsistencia, a no ser que las otras cachés comprueben 
los accesos a la memoria principal o reciban algún tipo de notificación directa de la escritura realizada.

Protocolo de Coherencia de Cache

El objetivo de un protocolo de coherencia de caché es situar las variables locales utilizadas recientemente en la caché 
apropiada y mantenerlas allí para las distintas escrituras y lecturas, al mismo tiempo que se mantiene la consistencia de las
variables compartidas que pudieran encontrarse en varias cachés al mismo tiempo. Las aproximaciones de coherencia de 
caché generalmente se han dividido en aproximaciones software y hardware. Algunas implementaciones adoptan una 
estrategia que implica tanto elementos software como hardware. No obstante, la distinción entre aproximaciones 680 
Organización y arquitectura de computadores software y hardware es todavía instructiva y es comúnmente utilizada en la 
presentación de las estrategias de coherencia de caché.

Soluciones por 
Software
Soluciones por 
Hardware
Coherencia de 
Cache

Coherencia de Cache: Soluciones por Software

Los esquemas software de coherencia de caché intentan evitar la necesidad de circuitería y lógica hardware adicional 
dejando que el compilador y el sistema operativo se encarguen del problema. Las propuestas software son atractivas 
porque transfieren el costo de la detección de posibles problemas desde el hardware al software. Por otra parte, en el 
momento de la compilación, el software generalmente debe tomar ciertas decisiones conservadoras que pueden ocasionar 
una utilización ineficiente de la caché.

Soluciones por 
Software
Los mecanismos de coherencia basados en el compilador 
realizan un análisis del código para determinar qué datos 
pueden dar problemas al pasar a caché, y los marcan en 
consecuencia. Después, el sistema operativo o el hardware 
impiden que se pasen a caché los datos marcados como no 
almacenables en caché (non-cachéable).

Coherencia de Cache: Soluciones por Software

Soluciones por 
Software
El enfoque más sencillo consiste en impedir que cualquier dato compartido pase a caché. Esto es demasiado 
conservador puesto que una estructura de datos compartida puede utilizarse de manera exclusiva durante 
ciertos periodos de tiempo y solo para lectura en otros periodos. Es solo durante aquellos periodos en los que al 
menos un procesador pueda actualizar una variable y otro procesador pueda acceder a la variable cuando hay 
que considerar la coherencia de caché.
Hay aproximaciones más eficientes que analizan el 
código y determinan periodos seguros para las variables 
compartidas. El compilador inserta entonces 
instrucciones en el código generado para reforzar la 
coherencia de caché en los periodos críticos.

Coherencia de Cache: Soluciones por Hardware

Soluciones por 
Hardware
Las soluciones basadas en el hardware generalmente se denominan protocolos de coherencia de caché. Estas 
soluciones permiten reconocer dinámicamente en el momento de la ejecución las situaciones de inconsistencias 
potenciales. Puesto que el problema se considera solo en el momento en que aparece, existe un uso más 
efectivo de las cachés, mejorándose las prestaciones en relación a las aproximaciones software. Además, estas 
aproximaciones son transparentes para el programador y el compilador, reduciendo la complejidad en el 
desarrollo del software.
Los esquemas hardware difieren en una serie de 
aspectos, que incluyen el lugar donde se encuentra la 
información de estado de las líneas de datos, cómo se 
organiza esa información, dónde se impone la 
coherencia y los mecanismos para imponerla. En 
general, los esquemas hardware se pueden dividir en 
dos categorías: protocolos de directorio y protocolos de 
sondeo
Soluciones por 
Hardware
Protocolos de Sondeo
Protocolos de 
Directorio

Coherencia de Cache: Protocolo de Directorio

Soluciones por 
Hardware
•
Los protocolos de directorio recogen y mantienen la información acerca de dónde residen las copias de las 
líneas. 
•
Usualmente, hay un controlador centralizado que es parte del controlador de memoria principal, y un 
directorio que se almacena en la memoria principal. 
•
El directorio contiene información de estado global en relación con los contenidos de las diferentes cachés 
locales. 
Soluciones por 
Hardware
Protocolos de Sondeo
Protocolos de 
Directorio
Cuando el controlador individual de una caché hace una 
petición, el controlador centralizado comprueba y emite las 
órdenes precisas para la transferencia entre memoria y caché o 
entre distintas cachés. Además, es responsable de mantener 
actualizada la información de estado; de esta  forma, cualquier 
acción local que pueda afectar al estado global de una línea 
debe comunicarse al controlador central.
Los esquemas de directorio presentan las desventajas propias de tener un cuello de botella central y del coste de comunicación entre los controladores de las 
distintas cachés y el controlador central. No obstante, son efectivos en sistemas de gran escala que poseen múltiples buses o algún esquema complejo de 
interconexión.

Coherencia de Cache: Protocolo de Sondeo

Soluciones por 
Hardware
Los protocolos de sondeo distribuyen la responsabilidad de mantener la coherencia de caché entre todos los 
controladores de caché del multiprocesador. Una caché debe reconocer cuando una línea de las que contiene 
está compartida con otras cachés. Cuando se realiza una actualización en una línea de caché compartida, debe 
anunciarse a todas las otras cachés mediante un mecanismo de difusión (broadcast). Cada controlador de caché 
es capaz de sondear o «espiar» («snoop») la red para observar las notificaciones que se difunden, y reaccionar 
adecuadamente.
Soluciones por 
Hardware
Protocolos de Sondeo
Protocolos de 
Directorio
•
Los protocolos de sondeo se adaptan bien a los 
multiprocesadores basados en un bus, puesto que el bus 
compartido proporciona una forma sencilla para la difusión 
y el sondeo. 
•
No obstante, puesto que uno de los objetivos de utilizar 
cachés locales es evitar los accesos al bus, hay que cuidar 
que el incremento en el tráfico del bus que requiere la 
difusión y el sondeo no anule los beneficios de las cachés 
locales.

Coherencia de Cache: Protocolo de Sondeo

Soluciones por 
Hardware
Se han explorado dos enfoques básicos del protocolo de sondeo: invalidar-si-escritura (writeinvalidate) y 
actualizar-si-escritura, o difundir-escritura (write-update o write-broadcast). 
Con un protocolo de invalidar-si-escritura, puede haber múltiples procesadores que leen pero un solo 
procesador que escribe en un momento dado. Inicialmente, una línea puede compartirse por varias cachés con 
el propósito de lectura. Cuando se quiere hacer una escritura en la línea de una caché, primero envía una 
notificación que invalida la línea en las otras cachés, haciendo que dicha línea sea exclusiva para la caché donde 
se va a escribir. Una vez que la línea es exclusiva, el procesador puede realizar escrituras locales en la misma 
hasta que otro procesador solicita la misma línea.
Protocolo de Sondeo
Wtrite Update
Write Invalidate
Con un protocolo de actualizar-si-escritura, puede haber varios 
procesadores que escriben igual que varios procesadores que 
leen. Cuando un procesador desea escribir en una línea 
compartida, la palabra a actualizar se distribuye a los demás, y 
las cachés que contienen esa línea lo pueden actualizar.

Coherencia de Cache: Protocolo MESI

Para proporcionar coherencia de caché en un SMP, la caché 
de datos usualmente implementa un protocolo conocido 
como MESI. Con el protocolo MESI, la caché de datos incluye 
dos bits de estado en la marca, puesto que cada línea puede 
estar en uno de estos cuatro estados:
• Modificado (Modified): la línea de caché ha sido 
modificada (es distinta a su valor en memoria principal) y 
está disponible solo en esta caché. 
• Exclusivo (Exclusive): la línea de caché tiene el mismo 
contenido que en memoria principal y no está presente en 
ninguna otra caché. 
• Compartido (Shared): la línea de caché tiene el mismo 
contenido que en memoria principal y puede estar presente 
en otra caché. 
• No-Válido (Invalid): la línea de caché no contiene datos 
válidos. 

Coherencia de Cache: Protocolo MESI

Fallo de lectura. Cuando se produce un fallo de lectura en la caché local, el procesador inicial una 
lectura en memoria para acceder a la línea de memoria principal que contiene la dirección que no está 
en caché. El procesador inserta una señal en el bus que avisa a todos los otros procesadores/cachés 
para que sondeen la transacción. 
• Si una de las cachés tiene una copia limpia (clean) de la línea (es decir, una copia no modificada desde que se leyó de 
memoria) en el estado exclusivo, devuelve una señal indicando que comparte la línea. El procesador que envía esta señal 
pasa su copia al estado compartido y el procesador inicial lee la línea y pasa el estado de esta en su caché de no-válido a 
compartido.
• Si una o más cachés tienen una copia limpia de la línea en estado compartido, cada una de ellas indica que comparte la 
línea. El procesador inicial lee la línea y pasa su estado en caché de no válido a compartido. 
• Si una de las cachés tiene una copia modificada de la línea, entonces esa caché bloquea la lectura de memoria y 
proporciona la línea a la caché que la solicita a través del bus compartido. La caché que proporciona la línea pasa esta del 
estado modificado al estado compartido. 
• Si ninguna otra caché tiene una copia de la línea (limpia o en estado modificado), no se envía ninguna señal. El 
procesador lee la línea y cambia el estado de la línea en su caché de no válido a exclusivo.

Coherencia de Cache: Protocolo MESI

Acierto de lectura. Cuando se produce un acierto en una lectura dentro de una línea presente en la 
caché local, el procesador simplemente lee el dato solicitado. No hay ningún cambio de estado: se 
mantiene como modificado, compartido o exclusivo.
Fallo de escritura. Cuando se produce un fallo en una 
escritura en la caché local, el procesador comienza una 
lectura de memoria para acceder a la línea de memoria 
principal que contiene la dirección que no está en 
caché. Para ello, el procesador envía una señal a través 
del bus que indica lectura-para-modificación (RWITM, 
Read-With-Intent-To-Modify). Cuando se carga la línea, 
se marca inmediatamente como modificada. Con 
respecto a las otras cachés, hay dos escenarios posibles 
previos a la carga del bloque de datos.

Coherencia de Cache: Protocolo MESI

Acierto de escritura. Cuando se produce un acierto de escritura en una línea de caché local, el efecto 
depende del estado de la línea:
• Compartido: antes de realizar la actualización, el procesador 
debe conseguir el acceso exclusivo a la línea. El procesador 
señala esta intención a través del bus. Todo procesador que 
tenga una copia de la línea en su caché la cambia del estado 
compartido al no válido. Después el procesador inicial actualiza 
la línea y cambia su copia de la línea del estado compartido al 
estado modificado.
• Exclusivo: puesto que el procesador tiene el control exclusivo 
de esta línea, simplemente la actualiza y cambia el estado de la 
línea de exclusivo a modificado.
• Modificado: puesto que el procesador tiene el control 
exclusivo de la línea y la tiene marcada en el estado 
modificado, solo tiene que actualizarla.

PROCESADORES RISC

CARACTERISTICAS DE UN CISC

En los años 50, todos los ordenadores se diseñaban de forma completamente aislada unos de otros. Esto hacía que sus 
instrucciones fuesen independientes, haciendo que un programa escrito para un cierto ordenador no se pudiese ejecutar en 
otro. A finales de la década, IBM reunió a un grupo de sus investigadores para estudiar la forma con la que un programa 
pudiese trabajar en múltiples ordenadores ampliando la compatibilidad del software.
La arquitectura CISC ( Complex Instruction Set Compute) es uno de los modelos de arquitectura de ordenadores. Los 
microprocesadores CISC tienen un conjunto de instrucciones que se caracteriza por ser muy amplio y por poder permitir 
operaciones complejas entre operandos situados en la memoria o en los registros internos, en contraposición a la 
arquitectura RISC.
Este tipo de arquitectura dificulta el paralelismo entre instrucciones, por lo que, en la actualidad, la mayoría de los sistemas
CISC de alto rendimiento implementan un sistema que convierte dichas instrucciones complejas en varias instrucciones 
simples del tipo RISC, llamadas generalmente microinstrucciones.
Los CISC pertenecen a la primera corriente de construcción de procesadores, antes del desarrollo de los RISC. Varios ejemplos
son: Motorola 68000, Zilog Z80 y toda la familia Intel x86, AMD x86-64 usada en la mayoría de los PCs actuales.

CARACTERISTICAS DE UN RISC

Tras el lanzamiento de CISC, los científicos de IBM empezaron a comprobar que los diseñadores de software creaban sus 
propias instrucciones más simples y precisas. Entonces, ya en la década de los 70, empezaron a diseñar una alternativa que 
posteriormente se introdujo en el mercado bajo el acrónimo RISC.
La arquitectura RISC (Reduced Instruction Set Computer) es un tipo de diseño de CPU generalmente utilizado en 
microprocesadores que tienen las siguientes características fundamentales:
Instrucciones de tamaño fijo y presentadas en un reducido número de formatos.
Sólo las instrucciones de carga y almacenamiento acceden a la memoria de datos. Además estos procesadores suelen 
disponer de muchos registros de propósito general.
El objetivo de diseñar máquinas con esta arquitectura es posibilitar la segmentación y el paralelismo en la ejecución de 
instrucciones y reducir los accesos a memoria.
La arquitectura RISC esta hecho para un ordenador que esté a favor de los conjuntos de instrucciones pequeñas y simples que 
toman menor tiempo para ejecutarse. El tipo de procesador más comúnmente utilizado en equipos de escritorio, el x86, está 
basado en CISC en lugar de RISC.

CARACTERISTICAS DE UN RISC

• Una instrucción por ciclo.
• Operaciones registro a registro. 
• Modos de direccionamiento sencillos. 
• Formatos de instrucción sencillos

CARACTERISTICAS DE UN RISC

Una instrucción por ciclo de maquina:
Un ciclo máquina se define como el tiempo que se tarda en captar dos operandos desde dos registros, realizar 
una operación de la ALU y almacenar el resultado en un registro. Así, las instrucciones máquina de un RISC no 
deberían ser más complicadas que las microinstrucciones de las máquinas CISC, y deberían ejecutarse más o 
menos igual de rápido. Con instrucciones sencillas y de un ciclo, hay poca o ninguna necesidad de 
microcódigo; las instrucciones máquina pueden estar cableadas. Tales instrucciones deben ejecutarse más 
rápido que las instrucciones máquina comparables de otras máquinas, ya que no hay que acceder a la 
memoria de control de microprograma durante la ejecución de la instrucción.

CARACTERISTICAS DE UN RISC

Operaciones de  registro a registro
Esta forma de diseño simplifica el repertorio de instrucciones y por 
tanto la unidad de control. Por ejemplo, un repertorio de 
instrucciones RISC puede incluir solo una o dos instrucciones ADD 
(por ejemplo, suma entera y suma con acarreo); el VAX tiene 25 
instrucciones ADD diferentes. Otra ventaja es que tal arquitectura 
fomenta la optimización del uso de registros, ya que los operandos 
accedidos frecuentemente permanecen en el almacenamiento de alta 
velocidad. Este énfasis en las operaciones registro a registro es 
notable en los diseños RISC. Las máquinas CISC contemporáneas 
tienen tales instrucciones, pero incluyen también operaciones 
memoria a memoria y operaciones mixtas registro/memoria. En los 
años setenta, antes de la aparición de los RISC, se hicieron intentos de 
comparar estas aproximaciones. 

CARACTERISTICAS DE UN RISC

Modos de direccionamiento sencillos.
Casi todas las instrucciones RISC usan direccionamiento sencillo a registro. Se pueden incluir varios modos 
adicionales, como el desplazamiento y el relativo al contador de programa. Otros modos más complejos se 
pueden sintetizar por software a partir de los simples. Nuevamente, esta característica de diseño simplifica el 
repertorio de instrucciones y la unidad de control.
Formatos de instrucción sencillos. 
Generalmente, solo se usa un formato o unos pocos. La longitud de las instrucciones es fija y alineada en los 
límites de una palabra. Las posiciones de los campos, especialmente la del código de operación, son fijas. Este 
tipo de diseño tiene varias ventajas. Con campos fijos, la decodificación del código de operación y el acceso a 
los operandos en registros puede tener lugar simultáneamente. Los formatos sencillos simplifican la unidad de 
control. Se optimiza la captación de instrucciones ya que se captan unidades de una palabra de longitud. La 
alineación en el límite de una palabra también significa que una única instrucción no traspasa los límites de 
una página.

RISC vs CISC

Aspectos
RISC
CISC
Aplicación
Utilizada para entornos de red
Aplicada a ordenardores
domesticos
Características
Instrucciones de tamaño fijo. 
Solo las instrucciones de carga y 
almacenamiento acceden a la 
memoria de datos.
Instrucciones muy amplias.
Objetivos
Posiibilitar la segmentación y el 
paralelismo  en la ejecución de 
instrucciones y reducir los accesos a 
memoria.
Permitir operaciones complejas 
entre operandos situados en la 
memoria o en los registros internos.
Ventajas
La CPU trabaja mas rápido al utilizar 
menos ciclos de reloj. 
Reduciendo la ejecución de las 
operaciones.
Cada instrucción puede ser 
ejecutada en un solo ciclo de la CPU.
Reduce la dificultad de crear 
compiladores.
Permite reducir el costo total del 
sistema.
Mejora la compactación de código.
Facilita la depuración de errores.# Unidad 8 - Parte 2
## Computadores RISC - Completo (continuación)

No-Válido (Invalid): la línea de caché no contiene datos 
válidos. 

Coherencia de Cache: Protocolo MESI

Coherencia de Cache: Protocolo MESI

Fallo de lectura. Cuando se produce un fallo de lectura en la caché local, el procesador inicial una 
lectura en memoria para acceder a la línea de memoria principal que contiene la dirección que no está 
en caché. El procesador inserta una señal en el bus que avisa a todos los otros procesadores/cachés 
para que sondeen la transacción. 
• Si una de las cachés tiene una copia limpia (clean) de la línea (es decir, una copia no modificada desde que se leyó de 
memoria) en el estado exclusivo, devuelve una señal indicando que comparte la línea. El procesador que envía esta señal 
pasa su copia al estado compartido y el procesador inicial lee la línea y pasa el estado de esta en su caché de no-válido a 
compartido.
• Si una o más cachés tienen una copia limpia de la línea en estado compartido, cada una de ellas indica que comparte la 
línea. El procesador inicial lee la línea y pasa su estado en caché de no válido a compartido. 
• Si una de las cachés tiene una copia modificada de la línea, entonces esa caché bloquea la lectura de memoria y 
proporciona la línea a la caché que la solicita a través del bus compartido. La caché que proporciona la línea pasa esta del 
estado modificado al estado compartido. 
• Si ninguna otra caché tiene una copia de la línea (limpia o en estado modificado), no se envía ninguna señal. El 
procesador lee la línea y cambia el estado de la línea en su caché de no válido a exclusivo.

Coherencia de Cache: Protocolo MESI

Acierto de lectura. Cuando se produce un acierto en una lectura dentro de una línea presente en la 
caché local, el procesador simplemente lee el dato solicitado. No hay ningún cambio de estado: se 
mantiene como modificado, compartido o exclusivo.
Fallo de escritura. Cuando se produce un fallo en una 
escritura en la caché local, el procesador comienza una 
lectura de memoria para acceder a la línea de memoria 
principal que contiene la dirección que no está en 
caché. Para ello, el procesador envía una señal a través 
del bus que indica lectura-para-modificación (RWITM, 
Read-With-Intent-To-Modify). Cuando se carga la línea, 
se marca inmediatamente como modificada. Con 
respecto a las otras cachés, hay dos escenarios posibles 
previos a la carga del bloque de datos.

Coherencia de Cache: Protocolo MESI

Acierto de escritura. Cuando se produce un acierto de escritura en una línea de caché local, el efecto 
depende del estado de la línea:
• Compartido: antes de realizar la actualización, el procesador 
debe conseguir el acceso exclusivo a la línea. El procesador 
señala esta intención a través del bus. Todo procesador que 
tenga una copia de la línea en su caché la cambia del estado 
compartido al no válido. Después el procesador inicial actualiza 
la línea y cambia su copia de la línea del estado compartido al 
estado modificado.
• Exclusivo: puesto que el procesador tiene el control exclusivo 
de esta línea, simplemente la actualiza y cambia el estado de la 
línea de exclusivo a modificado.
• Modificado: puesto que el procesador tiene el control 
exclusivo de la línea y la tiene marcada en el estado 
modificado, solo tiene que actualizarla.

PROCESADORES RISC

CARACTERISTICAS DE UN CISC

En los años 50, todos los ordenadores se diseñaban de forma completamente aislada unos de otros. Esto hacía que sus 
instrucciones fuesen independientes, haciendo que un programa escrito para un cierto ordenador no se pudiese ejecutar en 
otro. A finales de la década, IBM reunió a un grupo de sus investigadores para estudiar la forma con la que un programa 
pudiese trabajar en múltiples ordenadores ampliando la compatibilidad del software.
La arquitectura CISC ( Complex Instruction Set Compute) es uno de los modelos de arquitectura de ordenadores. Los 
microprocesadores CISC tienen un conjunto de instrucciones que se caracteriza por ser muy amplio y por poder permitir 
operaciones complejas entre operandos situados en la memoria o en los registros internos, en contraposición a la 
arquitectura RISC.
Este tipo de arquitectura dificulta el paralelismo entre instrucciones, por lo que, en la actualidad, la mayoría de los sistemas
CISC de alto rendimiento implementan un sistema que convierte dichas instrucciones complejas en varias instrucciones 
simples del tipo RISC, llamadas generalmente microinstrucciones.
Los CISC pertenecen a la primera corriente de construcción de procesadores, antes del desarrollo de los RISC. Varios ejemplos
son: Motorola 68000, Zilog Z80 y toda la familia Intel x86, AMD x86-64 usada en la mayoría de los PCs actuales.

CARACTERISTICAS DE UN RISC

Tras el lanzamiento de CISC, los científicos de IBM empezaron a comprobar que los diseñadores de software creaban sus 
propias instrucciones más simples y precisas. Entonces, ya en la década de los 70, empezaron a diseñar una alternativa que 
posteriormente se introdujo en el mercado bajo el acrónimo RISC.
La arquitectura RISC (Reduced Instruction Set Computer) es un tipo de diseño de CPU generalmente utilizado en 
microprocesadores que tienen las siguientes características fundamentales:
Instrucciones de tamaño fijo y presentadas en un reducido número de formatos.
Sólo las instrucciones de carga y almacenamiento acceden a la memoria de datos. Además estos procesadores suelen 
disponer de muchos registros de propósito general.
El objetivo de diseñar máquinas con esta arquitectura es posibilitar la segmentación y el paralelismo en la ejecución de 
instrucciones y reducir los accesos a memoria.
La arquitectura RISC esta hecho para un ordenador que esté a favor de los conjuntos de instrucciones pequeñas y simples que 
toman menor tiempo para ejecutarse. El tipo de procesador más comúnmente utilizado en equipos de escritorio, el x86, está 
basado en CISC en lugar de RISC.

CARACTERISTICAS DE UN RISC

• Una instrucción por ciclo.
• Operaciones registro a registro. 
• Modos de direccionamiento sencillos. 
• Formatos de instrucción sencillos

CARACTERISTICAS DE UN RISC

Una instrucción por ciclo de maquina:
Un ciclo máquina se define como el tiempo que se tarda en captar dos operandos desde dos registros, realizar 
una operación de la ALU y almacenar el resultado en un registro. Así, las instrucciones máquina de un RISC no 
deberían ser más complicadas que las microinstrucciones de las máquinas CISC, y deberían ejecutarse más o 
menos igual de rápido. Con instrucciones sencillas y de un ciclo, hay poca o ninguna necesidad de 
microcódigo; las instrucciones máquina pueden estar cableadas. Tales instrucciones deben ejecutarse más 
rápido que las instrucciones máquina comparables de otras máquinas, ya que no hay que acceder a la 
memoria de control de microprograma durante la ejecución de la instrucción.

CARACTERISTICAS DE UN RISC

Operaciones de  registro a registro
Esta forma de diseño simplifica el repertorio de instrucciones y por 
tanto la unidad de control. Por ejemplo, un repertorio de 
instrucciones RISC puede incluir solo una o dos instrucciones ADD 
(por ejemplo, suma entera y suma con acarreo); el VAX tiene 25 
instrucciones ADD diferentes. Otra ventaja es que tal arquitectura 
fomenta la optimización del uso de registros, ya que los operandos 
accedidos frecuentemente permanecen en el almacenamiento de alta 
velocidad. Este énfasis en las operaciones registro a registro es 
notable en los diseños RISC. Las máquinas CISC contemporáneas 
tienen tales instrucciones, pero incluyen también operaciones 
memoria a memoria y operaciones mixtas registro/memoria. En los 
años setenta, antes de la aparición de los RISC, se hicieron intentos de 
comparar estas aproximaciones. 

CARACTERISTICAS DE UN RISC

Modos de direccionamiento sencillos.
Casi todas las instrucciones RISC usan direccionamiento sencillo a registro. Se pueden incluir varios modos 
adicionales, como el desplazamiento y el relativo al contador de programa. Otros modos más complejos se 
pueden sintetizar por software a partir de los simples. Nuevamente, esta característica de diseño simplifica el 
repertorio de instrucciones y la unidad de control.
Formatos de instrucción sencillos. 
Generalmente, solo se usa un formato o unos pocos. La longitud de las instrucciones es fija y alineada en los 
límites de una palabra. Las posiciones de los campos, especialmente la del código de operación, son fijas. Este 
tipo de diseño tiene varias ventajas. Con campos fijos, la decodificación del código de operación y el acceso a 
los operandos en registros puede tener lugar simultáneamente. Los formatos sencillos simplifican la unidad de 
control. Se optimiza la captación de instrucciones ya que se captan unidades de una palabra de longitud. La 
alineación en el límite de una palabra también significa que una única instrucción no traspasa los límites de 
una página.

RISC vs CISC

Aspectos
RISC
CISC
Aplicación
Utilizada para entornos de red
Aplicada a ordenardores
domesticos
Características
Instrucciones de tamaño fijo. 
Solo las instrucciones de carga y 
almacenamiento acceden a la 
memoria de datos.
Instrucciones muy amplias.
Objetivos
Posiibilitar la segmentación y el 
paralelismo  en la ejecución de 
instrucciones y reducir los accesos a 
memoria.
Permitir operaciones complejas 
entre operandos situados en la 
memoria o en los registros internos.
Ventajas
La CPU trabaja mas rápido al utilizar 
menos ciclos de reloj. 
Reduciendo la ejecución de las 
operaciones.
Cada instrucción puede ser 
ejecutada en un solo ciclo de la CPU.
Reduce la dificultad de crear 
compiladores.
Permite reducir el costo total del 
sistema.
Mejora la compactación de código.
Facilita la depuración de errores.

# Unidad 9
## Arquitectura de Computadoras Paralelas

Unidad 9
Arquitectura de Computadoras Paralelas

GUIA DE LECTURA

Introducción

Ciclo de instrucción básico.
Tradicionalmente, el computador se ha visto como una máquina secuencial. La mayoría de los lenguajes de programación 
del computador requieren que el programador especifique los algoritmos mediante una secuencia de instrucciones. Los 
procesadores ejecutan los programas procesando instrucciones máquina de una en una. Cada instrucción se ejecuta 
mediante una secuencia de operaciones (captar instrucción, captar operandos, realizar la operación, almacenar los
resultados).
Esta perspectiva del computador no es completamente cierta. En el nivel de microoperación, se generan al mismo tiempo 
múltiples señales de control. La segmentación de las instrucciones, al menos en cuanto al solapamiento de las 
operaciones de captación y ejecución, se ha utilizado desde hace tiempo. Ambos casos son ejemplos de funciones que se 
realizan en paralelo. Es el mismo enfoque de la organización superescalar, que aprovecha el paralelismo entre 
instrucciones. Un procesador superescalar dispone de varias unidades de ejecución que pueden ejecutar en paralelo 
varias instrucciones del mismo programa.

La taxonomía introducida primeramente por Flynn [FLYN72] es todavía la forma más común de 
clasificar a los sistemas según sus capacidades de procesamiento paralelo. Flynn propuso las 
siguientes categorías o clases de computadores:
• Una secuencia de instrucciones y una secuencia de datos (SISD, Single Instruction Single 
Data): un único procesador interpreta una única secuencia de instrucciones para operar con los 
datos almacenados en una única memoria. Los computadores monoprocesador caen dentro
de esta categoría.
• Una secuencia de instrucciones y múltiples secuencias de datos (SIMD, de Single Instruction 
Multiple Data): una única instrucción máquina controla paso a paso la ejecución simultánea y 
sincronizada de un cierto número de elementos de proceso. Cada elemento de proceso tiene 
una memoria asociada, de forma que cada instrucción es ejecutada por cada procesador con un 
conjunto de datos diferentes. Los procesadores vectoriales y los matriciales pertenecen a esta 
categoría.
• Múltiples secuencias de instrucciones y una secuencia de datos (MISD): se transmite una 
secuencia de datos a un conjunto de procesadores, cada uno de los cuales ejecuta una 
secuencia de instrucciones diferente. Esta estructura nunca ha sido implementada.
• Múltiples secuencias de instrucciones y múltiples secuencias de datos (MIMD): un conjunto 
de procesadores ejecuta simultáneamente secuencias de instrucciones diferentes con 
conjuntos de datos diferentes. Los SMP, los clusters y los sistemas NUMA son ejemplos de esta 
categoría.

Tipos de Sistemas Paralelos

Multi-Procesadores Simetricos
Hasta hace poco, prácticamente todos los computadores personales y estaciones de trabajo utilizaban un único microprocesador de 
uso general. A medida que aumenta la demanda de mayores prestaciones y dado que el coste de los microprocesadores continúa 
reduciéndose, los fabricantes han introducido los sistemas SMP. El término SMP se refiere a la arquitectura hardware del computador 
y también al comportamiento del sistema operativo que utiliza dicha arquitectura. Un SMP puede definirse como un computador con 
las siguientes características:
1. Hay dos o más procesadores similares de capacidades comparables.
2. Estos procesadores comparten la memoria principal y las E/S y están interconectados mediante un bus u otro tipo de sistema de interconexión, de 
forma que el tiempo de acceso a memoria es aproximadamente el mismo para todos los procesadores.
3. Todos los procesadores comparten los dispositivos de E/S, bien a través de los mismos canales o mediante canales distintos que proporcionan 
caminos de acceso al mismo dispositivo.
4. Todos los procesadores pueden desempeñar las mismas funciones (de ahí el término simétrico).
5. El sistema está controlado por un sistema operativo integrado que proporciona la interacción entre los procesadores y sus programas a los niveles 
de trabajo, tarea, fichero y datos.

Multi-Procesadores Simetricos
El significado de los puntos 1 a 4 es claro. El punto 5 corresponde a una de las diferencias con los 
sistemas multiprocesador débilmente acoplados, tales como los clusters. En estos, la unidad de 
interacción física es normalmente un mensaje o un fichero completo. En un SMP, la interacción se 
puede producir a través de elementos de datos individuales, y puede existir un elevado nivel de 
cooperación entre procesadores.
El sistema operativo de un SMP planifica la distribución de procesos o hilos (threads) entre todos los 
procesadores. Un SMP tiene las siguientes ventajas potenciales con respecto a una arquitectura 
monoprocesador:
• Prestaciones: si el trabajo a realizar por un computador puede organizarse de forma que partes del 
mismo se puedan realizar en paralelo, entonces un sistema con varios procesadores proporcionará 
mejores prestaciones que uno con un solo procesador del mismo tipo 
• Disponibilidad: en un multiprocesador simétrico, debido a que todos los procesadores pueden 
realizar las mismas funciones, un fallo en un procesador no hará que el computador se detenga.
• Crecimiento incremental: se pueden aumentar las prestaciones del sistema añadiendo más
procesadores.
• Escalado: los fabricantes pueden ofrecer una gama de productos con precios y prestaciones
diferentes en función del número de procesadores que configuran el sistema.
Es importante resaltar que los anteriores son beneficios potenciales más que beneficios garantizados.
El sistema operativo debe disponer de herramientas y funciones que permitan explotar el 
paralelismopresente en un SMP.
Una característica atractiva de un SMP es que la existencia de varios procesadores es transparente
al usuario. El sistema operativo se encarga de la sincronización entre los procesadores y de la 
planificaciónde los hilos o de los procesos, asignándolos a los distintos procesadores.

Organización
La Figura de abajo describe en términos generales la organización de un sistema multiprocesador. Hay dos o más procesadores. Cada procesador es autónomo, incluyendo una 
unidad de control, una ALU, registros y, posiblemente, caché. Cada procesador tiene acceso a una memoria principal compartida y a los dispositivos de E/S a través de alguna 
forma de mecanismo de interconexión. Los procesadores pueden comunicarse entre sí a través de la memoria (mensajes e información de control almacenada en áreas 
comunes para datos). También es posible que los procesadores intercambien señales directamente. La memoria a menudo se organiza de forma que sean posibles los accesos 
simultáneos a bloques de memoria separados. En algunas configuraciones, cada procesador puede tener también su propia memoria principal privada y sus canales de E/S, 
además de los recursos compartidos.

BUS de tiempo compartido
La organización más común en los computadores personales, estaciones de trabajo y 
servidores es el bus de tiempo compartido. El bus de tiempo compartido es el mecanismo 
más simple para construir un sistema multiprocesador (Figura 18.5). La estructura y las 
interfaces son básicamente las mismas que las de un sistema de un único procesador que 
utilice un bus para la interconexión. El bus consta de líneas de control, dirección y datos. 
Para facilitar las transferencias de DMA con los procesadores de E/S, se proporcionan los 
elementos para el:
• Direccionamiento: debe ser posible distinguir los módulos del bus para determinar la 
fuente y el destino de los datos.
• Arbitraje: cualquier módulo de E/S puede funcionar temporalmente como un «maestro». 
Se proporciona un mecanismo para arbitrar entre las peticiones que compiten por el control 
del bus, utilizando algún tipo de esquema de prioridad.

BUS de tiempo compartido
• Tiempo Compartido: cuando un módulo está controlando el bus, los otros módulos no tienen 
acceso al mismo y deben, si es necesario, suspender su operación hasta que dispongan del bus. 
Estas características monoprocesador son utilizables directamente en una configuración de 
SMP.
En este caso, hay varias CPU además de varios procesadores de E/S que intentan tener acceso a 
uno o más módulos de memoria a través del bus.
La organización del bus presenta varias características atractivas:
• Simplicidad: es la aproximación más simple para organizar el multiprocesador. La interfaz 
física y la lógica de cada procesador para el direccionamiento, el arbitraje y para compartir el 
tiempo del bus es el mismo que el de un sistema con un solo procesador.
• Flexibilidad: es generalmente sencillo expandir el sistema conectando más procesadores al 
bus.
• Fiabilidad: el bus es esencialmente un medio pasivo, y el fallo de cualquiera de los 
dispositivos conectados no provocaría el fallo de todo el sistema.
La principal desventaja de la organización de bus son las prestaciones. Todas las referencias a 
memoria pasan por el bus. En consecuencia, la velocidad del sistema está limitada por el 
tiempo de ciclo. Para mejorar las prestaciones, es deseable equipar a cada procesador de una 
memoria caché. Esta reduciría dramáticamente el número de accesos. Típicamente, los PC y las 
estaciones de trabajo de tipo SMP tienen dos niveles de caché, una caché L1 interna (en el 
mismo chip que el procesador) y una caché L2 externa o interna. Algunos procesadores 
actuales también utilizan una memoria caché L3.
El uso de cachés introduce algunas consideraciones de diseño nuevas. Puesto que cada caché 
local contiene una imagen de una parte de la memoria, si se altera una palabra en una caché,es 
concebible que eso podría invalidar una palabra en otra caché. Para evitarlo, se debe avisar a 
los otros procesadores de que se ha producido una actualización de memoria. Este problema se 
conoce como problema de coherencia de caché, que es resuelto típicamente por el hardware 
más que por el sistema operativo. 