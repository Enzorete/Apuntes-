---
title: "Arquitectura II"
subtitle: "Apuntes completos: Teoría, Ejercicios y Conceptos Avanzados"
author: "Apuntes de cátedra"
date: "2026-06-10"
lang: "es-AR"
---

# Arquitectura II

> Apuntes completos con teoría, ejercicios resueltos y conceptos de arquitectura de computadores.

## Tabla de Contenidos

- [Parte 1: Conceptos Fundamentales](#parte-1-conceptos-fundamentales)
- [Parte 2: Ejercicios Resueltos](#parte-2-ejercicios-resueltos)
- [Parte 3: Ciclos y Buses](#parte-3-ciclos-de-captación-interrupciones-y-arquitectura-de-buses)
- [Parte 4: Memorias](#parte-4-memorias)
- [Parte 5: Memoria Caché](#parte-5-memoria-caché)
- [Parte 6: Direccionamiento e Instrucciones](#parte-6-direccionamiento-formato-de-instrucciones-y-ensamblador)
- [Parte 7: Procesadores Modernos](#parte-7-procesadores-modernos)
- [Parte 8: Arquitecturas Paralelas](#parte-8-arquitectura-de-computadoras-paralelas)

---

# PARTE 1: CONCEPTOS FUNDAMENTALES

## 1. Interrupciones

Las interrupciones son solicitudes de atención que otros componentes hacen a la CPU.

### Tipos de Interrupciones

- **IRQ (Enmascarables):** La CPU puede ignorarlas mediante instrucciones de enmascaramiento.
- **NMI (No enmascarables):** No se pueden deshabilitar. Se usan para errores críticos o situaciones de emergencia.

---

## 2. DMA (Acceso Directo a Memoria)

Permite transferir datos entre RAM y dispositivos periféricos sin intervención directa de la CPU.

### Modos de Funcionamiento

1. **Ráfaga:** La CPU cede el control completo del bus al controlador DMA.
2. **Robo de ciclo:** El DMA toma un ciclo de bus por vez, intercalándose con la CPU.
3. **Transparente:** Usa ciclos libres del bus que la CPU no está utilizando.

---

## 3. Complemento a Dos (C2)

Sistema de representación para números negativos en binario.

### Características

- **Rango con n bits:** de **-2^(n-1)** a **2^(n-1) - 1**
- **Ejemplo (4 bits):** `1001` = **-7** (invertir `0110` y sumar 1)
- **Negación:** complemento a uno + 1

---

## 4. IEEE 754 (Estándar de Coma Flotante)

Estándar de 1985 para representación de números en coma flotante.

### Estructura (Precisión Simple)

- **1 bit:** signo
- **8 bits:** exponente
- **23 bits:** mantisa

### Nota sobre Overflow

El overflow de exponente sí existe en IEEE 754 (causa infinito).

---

## 5. Conceptos Clave de Memoria Caché

### Métricas de Rendimiento

- **Hit Rate (H):** H = aciertos / accesos totales
- **Tiempo medio de acceso:** Ts = T1 + (1 - H) × T2
  - T1 = tiempo de acceso a caché
  - T2 = tiempo adicional si hay fallo (miss)

### Mapeo de Bloques

- **Mapeo directo:** etiqueta + línea + offset
- **Mapeo asociativo:** etiqueta + offset
- **Mapeo asociativo por conjuntos:** combina ambas aproximaciones

---

# PARTE 2: EJERCICIOS RESUELTOS

## Ejercicio 1: Tiempo de Acceso a Caché

**Datos:** H = 0.9, T_caché = 1 ns, T_memoria = 10 ns

**Solución:**
```
Ts = 1 + (1 - 0.9) × 10 = 1 + 1 = 2 ns
```

---

## Ejercicio 2: Hit Rate Requerido

**Datos:** Ts objetivo = 1.25 ns, T_caché = 1 ns, T_memoria = 10 ns

**Solución:**
```
1.25 = 1 + (1 - H) × 10
0.25 = (1 - H) × 10
H = 0.975 = 97.5%
```

---

## Ejercicio 3: Mapeo Directo

**Datos:**
- Memoria principal: 256M = 2^28 bytes
- Tamaño de bloque: 256 bytes (2^8)
- Tamaño de caché: 4096 líneas

**Cálculos:**

| Parámetro | Cálculo | Bits |
|-----------|---------|------|
| Offset (palabra) | log₂(256) | 8 |
| Línea de caché | log₂(4096) | 12 |
| Etiqueta | 28 - 12 - 8 | 8 |

**Formato de dirección:**
```
┌──────────┬─────────────┬──────────┐
│ Etiqueta │   Línea     │  Offset  │
│   (8)    │    (12)     │   (8)    │
└──────────┴─────────────┴──────────┘
```

**Bloques en memoria:** 256M ÷ 256 = 1,048,576 bloques

---

## Ejercicio 4: Mapeo Asociativo

**Datos:** Memoria 2^28, bloque de 256 bytes

**Resultado:**
- Offset: 8 bits
- Etiqueta: 20 bits

**Formato:**
```
┌──────────────────────┬──────────┐
│     Etiqueta (20)    │  Offset  │
│                      │   (8)    │
└──────────────────────┴──────────┘
```

---

## Ejercicio 5: Cálculo de Hit Rate

**Datos:**
- a) Bloque: 64 bytes
- b) Ts = 20 ns, T_caché = 5 ns, T_memoria = 200 ns

**Solución:**
```
20 = 5 + (1 - H) × 200
15 = (1 - H) × 200
1 - H = 0.075
H = 0.925 = 92.5%
```

---

## Ejercicio 6: Caché Asociativa por Conjuntos

**Datos:** Memoria 2^32 bytes, líneas de 4096, palabras de 4 bytes

**Resultados:**

| Parámetro | Valor |
|-----------|-------|
| Memoria principal | 4096 MB |
| Líneas en caché | 4096 |
| Palabras totales | 16,384 |
| Líneas por conjunto | 4 |
| Número de conjuntos | 1024 |
| Hit Rate (Ts = 10 ns) | 90% |

---

## Ejercicio 7: Problema Completo de Caché

**Parte 1: Hit Rate y Tiempo de Acceso**
```
Accesos = 1,200,000
Aciertos = 600,000

H = 600,000 / 1,200,000 = 0.5 = 50%
Ts = 120 + 0.5 × 1260 = 750 ns
```

**Parte 2: Campos de Dirección**
- Memoria principal: 8 MB = 2^23 bytes
- Offset: 8 bits
- Líneas de caché: 16 = 2^4 bits
- Etiqueta: 23 - 4 - 8 = 11 bits

**Formato:**
```
┌───────────────┬────────┬──────────┐
│ Etiqueta (11) │ Línea  │  Offset  │
│               │  (4)   │   (8)    │
└───────────────┴────────┴──────────┘
```

---

# PARTE 3: CICLOS DE CAPTACIÓN, INTERRUPCIONES Y ARQUITECTURA DE BUSES

## 1. Ciclo de Instrucción

La CPU ejecuta programas repitiendo continuamente:

1. **Captar** la instrucción de memoria
2. **Ejecutarla**

Este proceso se denomina **ciclo de instrucción**.

---

## 2. Registros Importantes de la CPU

### PC — Program Counter

Guarda la dirección de la próxima instrucción a ejecutar.

**Ejemplo:** Si PC = 300, la CPU busca la instrucción en memoria[300].

---

### IR — Instruction Register

Almacena la instrucción que se está ejecutando actualmente.

---

### AC — Acumulador

Registro temporal donde la CPU guarda datos y resultados intermedios.

---

## 3. Estructura de Instrucciones

Las instrucciones están compuestas por dos partes:

| Parte | Función |
|-------|---------|
| **Codop** | Especifica qué operación ejecutar |
| **Dirección** | Indica dónde está el operando |

### Ejemplo de Instrucción

```
1940
├─ 1   → Codop (cargar en AC)
└─ 940 → Dirección de memoria

Significado: Cargar en AC el dato guardado en posición 940
```

---

## 4. Estados del Ciclo de Instrucción

El ciclo de instrucción consta de 7 estados principales:

| Acrónimo | Significado | Descripción |
|----------|-------------|-------------|
| **IAC** | Instruction Address Calculation | Cálculo de la dirección de instrucción |
| **IF** | Instruction Fetch | Captación de instrucción desde memoria |
| **IOD** | Instruction Operation Decoding | Decodificación de la operación |
| **OAC** | Operand Address Calculation | Cálculo de la dirección del operando |
| **OF** | Operand Fetch | Captación del operando |
| **DO** | Data Operation | Operación aritmética o lógica |
| **OS** | Operand Store | Almacenamiento del resultado |

---

## 5. Tipos de Operaciones de la CPU

### Procesador ↔ Memoria

Transferencia de datos entre CPU y memoria principal.

### Procesador ↔ E/S

Transferencia de datos con dispositivos externos (teclado, impresora, disco, etc.).

### Procesamiento de Datos

Operaciones aritméticas y lógicas sobre datos.

### Control

Cambio de la secuencia de ejecución del programa (saltos condicionales e incondicionales).

---

## 6. Interrupciones

Una interrupción es una solicitud de atención que otro componente hace a la CPU. Sirven para **evitar que el procesador quede esperando** mientras un dispositivo lento trabaja.

### Tipos de Interrupciones

| Tipo | Ejemplo |
|------|---------|
| **Programa** | División por cero, operación ilegal |
| **Temporización** | Temporizador (timer) |
| **E/S** | Impresión completada, dato disponible |
| **Hardware** | Error físico en memoria, fallo de bus |

---

## 7. Secuencia de Atención de Interrupciones

Cuando ocurre una interrupción, la CPU realiza:

1. **Guarda el contexto actual**
   - Almacena PC, registros y estado del programa
   - Permite continuar después donde quedó

2. **Suspende el programa**
   - El programa actual se pausa temporalmente

3. **Ejecuta el gestor de interrupción**
   - Rutina especial para atender el evento

4. **Atiende el problema**
   - Realiza la acción necesaria según el dispositivo o error

5. **Vuelve al programa original**
   - Recupera el contexto guardado
   - Continúa normalmente

---

## 8. Interrupciones Múltiples

Pueden ocurrir varias interrupciones simultáneamente.

### Estrategias de Manejo

**Desactivar interrupciones:**
- La CPU atiende una por vez
- Orden FIFO (primero en llegar, primero en atender)

**Usar prioridades:**
- Una interrupción importante puede interrumpir a otra menos importante
- Requiere hardware adicional

---

## 9. Entrada y Salida (E/S)

Los módulos de E/S permiten que la computadora se comunique con dispositivos externos:

- Teclado
- Impresora
- Disco
- Monitor
- Red

---

## 10. Arquitectura de Interconexión

Los componentes principales de una computadora se comunican mediante líneas de conexión:

- **CPU** (Unidad Central de Procesamiento)
- **Memoria** (RAM, ROM)
- **Módulos de E/S** (Controladores)

---

## 11. Bus

Un **bus** es un conjunto de líneas compartidas que conectan los componentes de una computadora, permitiendo comunicación entre ellos.

### Tipos de Buses

| Tipo | Función |
|------|---------|
| **Bus de datos** | Transporta datos entre componentes |
| **Bus de direcciones** | Indica origen o destino de datos |
| **Bus de control** | Coordina señales y operaciones |

---

## 12. Señales Importantes del Bus

| Señal | Función |
|-------|---------|
| **Memory Read** | Lee un dato desde memoria |
| **Memory Write** | Escribe un dato en memoria |
| **I/O Read** | Lee un dato desde dispositivo E/S |
| **I/O Write** | Envía un dato a dispositivo E/S |
| **Transfer ACK** | Confirma la transferencia |
| **Bus Request** | Solicita usar el bus |
| **Bus Grant** | Concede el uso del bus |
| **Interrupt Request** | Indica interrupción pendiente |
| **Interrupt ACK** | Confirma la interrupción |
| **Clock** | Sincroniza operaciones |
| **Reset** | Reinicia el sistema |

---

# PARTE 4: MEMORIAS

## 1. Concepto de Memoria

Las memorias sirven para:
- Almacenar datos
- Almacenar instrucciones

---

## 2. Características de las Memorias

Las memorias se clasifican por:

- **Ubicación** (interna/externa)
- **Capacidad** (bytes/palabras)
- **Método de acceso** (secuencial/directo/aleatorio/asociativo)
- **Prestaciones** (velocidad, latencia)
- **Soporte físico** (semiconductores, magnéticos, ópticos)
- **Organización** (cómo se estructuran los bits)

---

## 3. Ubicación de Memoria

### Interna

Dentro de la computadora:
- Registros (más rápido)
- Caché
- RAM

### Externa

Dispositivos conectados por E/S:
- Discos duros
- Cintas magnéticas
- Memorias USB

---

## 4. Capacidad

Indica cuánto datos puede almacenar una memoria.

Se expresa en:
- **Bytes**
- **Palabras** (palabra = múltiples bytes)

---

## 5. Unidad de Transferencia

### Memoria Interna

Transfiere **palabras** completas.

### Memoria Externa

Transfiere **bloques** de datos.

---

## 6. Métodos de Acceso

| Método | Descripción |
|--------|-------------|
| **Secuencial** | Acceso uno por uno, en orden |
| **Directo** | Acceso aproximado y luego búsqueda (ej: disco) |
| **Aleatorio** | Acceso directo a cualquier posición (ej: RAM) |
| **Asociativo** | Búsqueda por contenido, no por dirección |

---

## 7. Prestaciones

### Tiempo de Acceso

Tiempo requerido para leer o escribir un dato.

### Tiempo de Ciclo

Tiempo mínimo necesario entre dos accesos consecutivos.

### Velocidad de Transferencia

Velocidad a la que se envían datos desde/hacia memoria.

---

## 8. Soportes Físicos

- **Semiconductores** (RAM, ROM, Flash)
- **Magnéticos** (discos duros, cintas)
- **Ópticos** (CDs, DVDs)
- **Magneto-ópticos** (Minidisc, Floptical)

---

## 9. Volatilidad

### Volátil

Pierde datos al desconectar la energía (ej: RAM).

### No Volátil

Mantiene datos sin energía (ej: ROM, discos).

---

## 10. Jerarquía de Memorias

Las memorias se organizan en jerarquía buscando equilibrio entre:

```
        VELOCIDAD      CAPACIDAD       COSTO
Registros    ↑            ↓              ↑
Caché        ↑            ↓              ↑
RAM          ↓            ↑              ↓
Disco        ↓            ↑              ↓
```

Se combinan memorias:
- **Rápidas y pequeñas** (registros, caché)
- **Lentas y grandes** (RAM, disco)

---

## 11. Localidad Referencial

Principio fundamental de la jerarquía de memorias:

**Los datos más usados se mantienen en memorias rápidas.**

### Tipos de Localidad

- **Localidad temporal:** Datos recientemente usados serán usados pronto
- **Localidad espacial:** Datos cercanos a datos usados serán usados pronto

---

## 12. Tipos de Memoria en la Jerarquía

| Tipo | Características |
|------|-----------------|
| **Registros** | Más rápidos y pequeños |
| **Caché** | Intermedia entre CPU y RAM |
| **RAM** | Memoria principal, acceso aleatorio |
| **Memoria masiva** | Discos, SSD, pendrives |
| **Memoria externa** | Almacenamiento permanente |

---

# PARTE 5: MEMORIA CACHÉ

## 1. ¿Por Qué Existe la Caché?

La CPU es **mucho más rápida** que la memoria principal. La caché aparece para:

- Acelerar accesos a memoria
- Mejorar el rendimiento del sistema
- Reducir cuellos de botella

---

## 2. ¿Qué es la Memoria Caché?

Es una memoria:

- **Pequeña** en capacidad
- **Muy rápida** de acceso
- **Ubicada entre CPU y RAM**

Guarda copias de datos usados frecuentemente.

---

## 3. Funcionamiento Básico

### Si el dato está en caché

La CPU lo obtiene rápidamente → **Hit (acierto)**

### Si el dato NO está en caché

1. Se trae un bloque completo desde RAM hacia caché
2. Se entrega el dato a la CPU → **Miss (falla)**

El dato pasa a caché cuando ocurre una falla.

---

## 4. Ejemplo Ilustrativo

**La CPU pide el dato 22:**

**Primera vez:**
- Caché NO lo tiene
- Se busca en RAM
- Se trae el bloque: `[20, 21, 22, 23]`
- Se guarda completo en caché

**Segunda vez:**
- Ya está en caché
- Acceso rápido (hit)

---

## 5. Localidad de Referencia

Si un dato fue usado recientemente:
- Probablemente vuelva a usarse
- O se usen datos cercanos

**Por eso se cargan bloques completos y no una sola palabra.**

---

## 6. Estructura de la Caché

### Memoria Principal

Está dividida en **bloques**.

### Caché

Está dividida en **líneas**.

Cada línea contiene:
- **Palabras** (datos)
- **Etiqueta (tag)** que identifica qué bloque está guardado

---

## 7. Operación de Lectura

La CPU genera una dirección.

### Si hay acierto

La caché entrega el dato directamente.

### Si hay falla

1. Se copia el bloque desde RAM a caché
2. Se entrega el dato a la CPU

---

## 8. Tipos de Carga ante una Falla

### Load Through

Primero se envía el dato a la CPU y después se completa la carga del bloque.

### Load Back

Primero se completa la carga en caché y luego se entrega a la CPU.

---

## 9. Elementos de Diseño de Caché

La caché se diseña considerando:

- **Tamaño** (MB)
- **Correspondencia** (cómo se mapean bloques)
- **Política de reemplazo** (qué bloque sacar)
- **Política de escritura** (cómo escribir)
- **Tamaño de línea** (bytes por línea)
- **Cantidad de cachés** (L1, L2, L3)

---

## 10. Tamaño de Caché

Se busca equilibrio entre:
- **Velocidad** (más caché = más rápido)
- **Costo** (más caché = más caro)
- **Capacidad** (más caché = más datos)

---

## 11. Función de Correspondencia (Mapeo)

Define dónde puede ubicarse un bloque de RAM dentro de la caché.

### Tipos de Correspondencia

1. **Directa** (Direct Mapped)
2. **Asociativa** (Fully Associative)
3. **Asociativa por conjuntos** (Set Associative)

---

## 12. Correspondencia Directa

Cada bloque de RAM puede ir solamente a **una línea específica** de caché.

**Fórmula:** Línea caché = (Bloque RAM) mod (Líneas caché)

### Ventajas

- Simple de implementar
- Económico en hardware

### Desventajas

- Dos bloques pueden "pelear" por la misma línea constantemente
- Baja tasa de aciertos en ciertos patrones

---

## 13. Correspondencia Asociativa

Un bloque puede ir a **cualquier línea** de caché.

### Ventajas

- Flexible
- Mejor tasa de aciertos

### Desventajas

- Hardware muy complejo
- Búsqueda lenta

---

## 14. Correspondencia Asociativa por Conjuntos

La caché se divide en **conjuntos**.

Un bloque puede ir a cualquier línea **dentro de su conjunto**.

Combina:
- Simplicidad de correspondencia directa
- Flexibilidad de correspondencia asociativa

---

## 15. Algoritmos de Sustitución (Reemplazo)

Cuando la caché está llena, ¿qué bloque sacar?

| Algoritmo | Estrategia |
|-----------|-----------|
| **LRU** (Least Recently Used) | Reemplaza el menos usado recientemente |
| **LFU** (Least Frequently Used) | Reemplaza el menos usado frecuentemente |
| **FIFO** (First In First Out) | Sale el primero que entró |
| **Aleatorio** | Reemplazo al azar |

---

## 16. Políticas de Escritura

### Write Through (Escritura Directa)

Escribe en caché **y RAM simultáneamente**.

- Ventaja: Memoria siempre actualizada
- Desventaja: Más lento

### Write Back (Post-Escritura)

Escribe primero en caché, **luego en RAM** cuando se reemplaza.

- Ventaja: Más rápido
- Desventaja: Riesgo de inconsistencia

### Write Allocate

Carga el bloque en caché antes de escribir.

### Write No Allocate

Escribe directo en RAM sin traer a caché.

---

## 17. Coherencia de Caché

Si una caché modifica un dato, las demás cachés deben:
- Actualizarse con el nuevo valor, O
- Invalidar su copia antigua

Problema importante en multiprocesadores.

---

## 18. Tamaño de Línea

### Bloques Grandes

- Mejoran aciertos (localidad espacial)
- Aprovechan mejor el ancho de banda

**Pero:**
- Ocupan más espacio
- Reemplazan más datos

---

## 19. Caché Multinivel

Las computadoras modernas tienen múltiples niveles:

| Nivel | Característica |
|-------|-----------------|
| **L1** | Más rápida y pequeña (en el chip) |
| **L2** | Intermedia |
| **L3** | Más grande (compartida entre núcleos) |

---

## 20. Caché Unificada vs Partida

### Caché Unificada

Guarda datos **e instrucciones** juntos.

### Caché Partida

Separada en:
- Caché de datos
- Caché de instrucciones

---

## 21. Conceptos Importantes de Rendimiento

| Concepto | Definición |
|----------|-----------|
| **Hit Rate (HR)** | Porcentaje de aciertos |
| **Miss Rate (MR)** | Porcentaje de fallas (1 - HR) |
| **Tiempo efectivo** | Tiempo promedio real de acceso |

---

# PARTE 6: MEMORIA INTERNA

## 1. Memoria Principal

La memoria principal utiliza **tecnología semiconductora**.

Su elemento básico es la **celda de memoria**.

---

## 2. Celda de Memoria

Cada celda:

- Representa **0 o 1** (dos estados estables)
- Puede **escribirse** (almacenar un bit)
- Puede **leerse** (obtener el bit almacenado)

---

## 3. Funcionamiento de una Celda

El ciclo de operación incluye:

| Fase | Descripción |
|------|-------------|
| **Selección** | Elige la celda a usar |
| **Control** | Indica si será lectura o escritura |
| **Escritura** | Coloca un 0 o 1 en la celda |
| **Lectura** | Obtiene el valor almacenado |

---

## 4. Memoria RAM

**RAM** significa: **Random Access Memory** (Acceso Aleatorio)

Se puede acceder directamente a **cualquier posición** de memoria sin pasar por las anteriores.

---

## 5. Características de la RAM

| Característica | Valor |
|---|---|
| Lectura | Sí |
| Escritura | Sí |
| Volatilidad | Volátil (pierde datos sin energía) |
| Tipo de almacenamiento | Temporal |
| Velocidad | Rápida |
| Tecnología | Señales eléctricas |

### Contenido

Guarda:
- Programas en ejecución
- Datos usados actualmente

---

## 6. Tipos de RAM

### SRAM (RAM Estática)

- Basada en **flip-flops** (circuitos lógicos)
- No necesita refrescos
- Más rápida pero más cara
- Usada en caché

### DRAM (RAM Dinámica)

- Basada en **transistores y capacitores**
- Necesita refrescos periódicos
- Más barata pero más lenta
- Usada como memoria principal

---

## 7. Características de DRAM

- Almacena **cargas eléctricas**
- Usa **capacitores**
- Necesita **refrescos periódicos** (recargar capacitores)
- La carga se pierde con el tiempo aunque esté encendida

---

## 8. Características de SRAM

- Usa **biestables** (flip-flops)
- **Más rápida**
- **No necesita refrescos**
- Mantiene datos mientras tenga energía

---

## 9. Comparación DRAM vs SRAM

| Aspecto | DRAM | SRAM |
|--------|------|------|
| Costo | Más barata | Más cara |
| Densidad | Más densa | Menos densa |
| Velocidad | Más lenta | Más rápida |
| Refresco | Necesario | No necesario |
| Uso | Memoria principal | Caché |

---

## 10. Memoria ROM

**ROM** significa: **Read Only Memory** (Memoria de Solo Lectura)

Contiene datos permanentes y no volátiles. No pueden modificarse fácilmente.

---

## 11. Funciones de la ROM

La ROM:

- Almacena configuraciones básicas (BIOS)
- Ayuda al arranque de la PC
- Activa periféricos
- Guarda programas permanentes

---

## 12. Tipos de ROM Reprogramable

### PROM (Programmable ROM)

- Programable una sola vez
- No volátil
- Escritura eléctrica

### EPROM (Erasable PROM)

- Puede borrarse con **luz ultravioleta**
- Puede reprogramarse
- El borrado afecta **todo el chip**

### EEPROM (Electrically EPROM)

- Borrado **eléctrico** (no UV)
- Permite actualizar **bytes específicos**
- Más flexible que EPROM

### Flash

- Usa borrado eléctrico
- **Muy rápida**
- Puede borrar **bloques completos**
- Muy usada en USB, SSD, etc.

---

## 13. Comparación RAM vs ROM

| Aspecto | RAM | ROM |
|--------|-----|-----|
| Lectura | Sí | Sí |
| Escritura | Sí | No |
| Volatilidad | Volátil | No volátil |
| Tipo | Temporal | Permanente |
| Uso | Programas activos | Configuración BIOS |

---

## 14. Errores en Memoria

### Fallo Permanente

- Daño físico en la memoria
- Bits "pegados" en 0 o 1
- Requiere reemplazo

### Error Transitorio

- Error temporal sin daño físico
- Puede deberse a problemas eléctricos
- Puede corregirse con refresco

---

## 15. Corrección de Errores

Se agregan **bits extra** llamados códigos de error (ECC).

Sirven para:
- **Detectar errores**
- **Corregir algunos errores**

**Proceso:**
1. Se recalcula el código al leer
2. Se compara con el código almacenado
3. Se detectan o corrigen diferencias

### Resultados Posibles

| Resultado | Acción |
|-----------|--------|
| **Sin errores** | Los datos se usan normalmente |
| **Error corregible** | El sistema corrige el dato automáticamente |
| **Error no corregible** | El sistema reporta el problema |

---

## 16. SDRAM (Synchronous DRAM)

- Funciona **sincronizada con el reloj**
- Trabaja a la **velocidad del bus**
- Reduce tiempos de espera

---

## 17. DDR SDRAM (Double Data Rate)

- Envía datos **dos veces por ciclo**
- Más rápida que SDRAM
- Más económica

Versiones: DDR, DDR2, DDR3, DDR4, DDR5

---

## 18. RDRAM (Rambus DRAM)

- Muy rápida
- Muy costosa
- Reemplazada por DDR

---

## 19. CDRAM (Cached DRAM)

- Puede funcionar como caché
- Sirve como buffer de datos

---

# PARTE 7: MEMORIA EXTERNA

## 1. Definición

La memoria externa incluye todos los dispositivos de almacenamiento **fuera de la computadora**.

Se usa para:
- Almacenamiento masivo
- Almacenamiento permanente
- Guardar datos e información

### Características

- No volátil (mantiene datos sin energía)
- Gran capacidad
- Más lenta que memoria principal
- No fundamental para funcionamiento

### Ejemplos

- Discos duros (HDD)
- Discos de estado sólido (SSD)
- Pendrives
- CDs y DVDs
- Cintas magnéticas

---

## 2. Tecnologías de Almacenamiento

Existen distintos tipos según la tecnología física.

---

## 3. Almacenamiento Magnético

Utiliza **propiedades magnéticas** para guardar datos.

### Ejemplos

- Disquete
- Disco duro (HDD)
- Cinta magnética

### Características

- Gran capacidad
- Almacenamiento tradicional
- Usa magnetismo para leer y escribir
- Más lento que semiconductores

---

## 4. Almacenamiento Óptico

Usa **rayos láser** para leer y escribir información.

La información se almacena en **surcos microscópicos** sobre discos.

### Ejemplos

- CD (Compact Disc)
- DVD (Digital Versatile Disc)
- Blu-ray

### Características

- Tecnología digital
- Lectura óptica mediante láser
- Capacidad media

---

## 5. Almacenamiento Magneto-Óptico

Combina:
- Magnetismo
- Tecnología óptica

Permite:
- Escribir datos
- Reescribir datos (borrar y grabar)

### Ejemplos

- Disco Zip
- Floptical
- Minidisc

---

## 6. Almacenamiento de Estado Sólido (SSD)

**SSD** significa: **Solid State Drive** (Unidad de Estado Sólido)

Usa **memoria no volátil** (Flash) para almacenar datos sin partes móviles.

### Características

- Más rápido que discos mecánicos
- Silencioso (sin partes móviles)
- Resistente a golpes
- Menor tiempo de acceso
- Menor latencia

### Ejemplos

- Memorias USB
- Tarjetas de memoria
- Discos SSD

---

## 7. RAID (Redundant Array of Independent Disks)

Sistema que usa **varios discos trabajando juntos** como una sola unidad lógica.

Puede usar:
- Discos duros (HDD)
- Discos sólidos (SSD)

### Objetivos

- Mejorar rendimiento
- Aumentar capacidad
- Tolerar fallos (redundancia)
- Mejorar integridad de datos

Se usa principalmente en **servidores**.

---

## 8. Beneficios de RAID

- Mayor integridad de datos
- Tolerancia a fallos
- Mejor velocidad de transferencia
- Mayor capacidad total

---

## 9. Tipos de RAID

### RAID 0 - Striping (Conjunto Dividido)

- Datos se dividen entre discos
- **Mejora velocidad**
- **Sin tolerancia a fallos** (si falla un disco, se pierden datos)

### RAID 1 - Mirroring (Conjunto en Espejo)

- Duplica los datos en varios discos
- **Mayor seguridad**
- Usa doble capacidad para redundancia

### RAID 5 - Striping with Parity

- Conjunto dividido con paridad distribuida
- Combina:
  - Rendimiento (striping)
  - Tolerancia a fallos (paridad)
- Puede tolerar fallo de 1 disco

---

## 10. Estado Actual de Tecnologías

### HDD (Discos Duros)

Siguen siendo importantes por su **capacidad y costo**.

### SSD (Discos Sólidos)

Cada vez reemplazan más a HDD porque:
- Son más rápidos
- Tienen menor latencia
- Son más resistentes

### RAID

Muy utilizado en **servidores y sistemas grandes** para confiabilidad.

### Medios Ópticos

**Perdieron popularidad** frente al almacenamiento sólido (USB, SSD).

### Disquetes

**Prácticamente desaparecieron** con la llegada de las memorias USB.

---

# PARTE 6: DIRECCIONAMIENTO, FORMATO DE INSTRUCCIONES Y ENSAMBLADOR

## 1. Modos de Direccionamiento

Los modos de direccionamiento especifican **cómo obtener el operando** dentro de una instrucción.

### Clasificación General

- **Con datos:** El operando está en la instrucción o en un registro
  - Inmediato
  - Directo
  - Indirecto
- **Sin datos:** Dato implícito o en operación

### Principales Modos

| Modo | Descripción | Ejemplo |
|------|-------------|---------|
| **Inmediato** | El operando está en la instrucción | `LDA #5` |
| **Directo/Absoluto** | Dirección completa en instrucción | `LDA $2000` |
| **Indirecto** | La instrucción tiene la dirección de la dirección | `LDA ($2000)` |
| **Registro** | Operando en un registro | `ADD A,B` |
| **Registro Indirecto** | Registro contiene la dirección | `LDA (X)` |
| **Indexado** | Dirección = base + índice | `LDA $1000,X` |
| **Relativo** | Dirección = PC + desplazamiento (para saltos) | `BRA ETIQUETA` |
| **Implícito** | No lleva operando explícito | `NOP`, `RTS` |

---

## 2. Formato de Instrucción

Las instrucciones tienen estructura:

```
┌─────────────────────┬──────────────────────┐
│ Código de Operación │ Datos/Operandos      │
│ (Codop)             │ (0, 1 o 2 bytes)     │
└─────────────────────┴──────────────────────┘
```

### Ejemplo M6800

| Modo | Tamaño |
|------|--------|
| Inherente | 1 byte |
| Inmediato | 2 bytes |
| Extendido | 3 bytes |

---

## 3. Lenguaje Ensamblador

El lenguaje ensamblador es un **lenguaje de bajo nivel** que expresa instrucciones en forma cercana al procesador.

### Características

- Cada instrucción corresponde a **una operación de CPU**
- Usa **nemotécnicos** (palabras clave) que representan código máquina
- Más legible que código binario pero muy cercano al hardware

### Elementos

| Elemento | Función | Ejemplo |
|----------|---------|---------|
| **Etiquetas** | Identifican direcciones en el programa | `INICIO:` |
| **Mnemónicos** | Representan instrucciones máquina | `ADD`, `LDA`, `STA` |
| **Operandos** | Especifican datos o direcciones | `#5` (inmediato), `$2000` (directo) |
| **Directivas** | Instrucciones para el ensamblador | `ORG`, `END`, `EQU` |

### Proceso de Ensamblaje

1. **Ensamblador** traduce nemotécnicos a código máquina
2. Realiza **dos pasadas:**
   - Primera: construye tabla de símbolos
   - Segunda: genera código máquina

### Ejemplo de Programa

```asm
        ORG $1000          ; Origen en dirección 0x1000

INICIO  LDA #10            ; Carga 10 en acumulador
        STA $2000          ; Almacena en memoria 0x2000
        JMP INICIO         ; Salta a INICIO (bucle infinito)

        END                ; Fin del programa
```

---

# PARTE 7: PROCESADORES MODERNOS

## 1. Organización del Procesador

### Requisitos Fundamentales

Para ejecutar programas, el procesador debe:

1. **Captar instrucción** → Leer instrucción de memoria
2. **Interpretar instrucción** → Decodificar para saber qué hacer
3. **Captar datos** → Leer operandos de memoria o registros
4. **Procesar datos** → Operaciones aritméticas o lógicas
5. **Escribir datos** → Almacenar resultados

### Estructura Interna del Procesador

```
┌──────────────────────────────────────┐
│     UNIDAD DE CONTROL                │
├──────────────────────────────────────┤
│                                      │
│  ┌─────────────────────────────────┐ │
│  │   UNIDAD ARITMÉTICO LÓGICA      │ │
│  │  ┌──────────────┐               │ │
│  │  │ Lógica A/L   │               │ │
│  │  │ Desplazador  │               │ │
│  │  │ Complementador│              │ │
│  │  └──────────────┘               │ │
│  │                                 │ │
│  │  Indicadores de estado          │ │
│  └─────────────────────────────────┘ │
│                                      │
│  ┌─────────────────────────────────┐ │
│  │    REGISTROS                    │ │
│  │  (PC, IR, AC, etc.)             │ │
│  └─────────────────────────────────┘ │
│                                      │
│      BUS INTERNO DEL PROCESADOR      │
│                                      │
└──────────────────────────────────────┘
```

---

## 2. Organización de Registros

### Registros Visibles por el Usuario

Tipos que el programador puede referenciar:

- **Registro de uso general** → Asignación flexible
- **Registro de datos** → Almacenamiento temporal
- **Registro de direcciones** → Direcciones de memoria
- **Registro de códigos de condición** → Flags (Z, C, V, etc.)

### Registros de Control y Estado

Utilizados por:
- Unidad de control (operación del procesador)
- Sistema operativo (control de programas)

**Ejemplo:** PC (contador de programa) es crítico pero no siempre visible al usuario.

---

## 3. Coherencia de Caché

En sistemas multiprocesador, pueden existir **varias copias del mismo dato** en cachés diferentes.

### El Problema

Si un procesador actualiza su copia, se produce **inconsistencia**.

### Políticas de Escritura

| Política | Descripción |
|----------|-------------|
| **Write-Back** | Escribe solo en caché, memoria se actualiza al reemplazar línea |
| **Write-Through** | Escribe en caché y memoria simultáneamente |

---

## 4. Soluciones de Coherencia

### Snooping

Cada caché **observa el bus** para detectar escrituras de otros procesadores.

### Directorio

**Tabla centralizada** de estados que registra dónde están las copias.

### Protocolo MESI

Estados para cada línea de caché: **Modified, Exclusive, Shared, Invalid**

---

## 5. RISC vs CISC

Dos filosofías de diseño de procesadores.

### CISC (Complex Instruction Set Computer)

**Características:**
- Conjunto **muy amplio** de instrucciones
- Instrucciones **complejas** (pueden hacer muchas cosas)
- Operaciones en memoria
- Múltiples formatos de instrucción

**Ejemplos:** Intel x86, AMD x86-64, Motorola 68000

**Ventajas:**
- Código compacto
- Menos instrucciones para tareas complejas

**Desventajas:**
- Unidad de control compleja
- Dificulta el paralelismo

---

### RISC (Reduced Instruction Set Computer)

**Características:**
- Conjunto **pequeño y simple** de instrucciones
- Cada instrucción ejecuta en **1 ciclo de máquina**
- Formato fijo (32 bits generalmente)
- Arquitectura **load/store** (solo carga/almacenamiento acceden a memoria)
- **Muchos registros** de propósito general

**Ejemplos:** SPARC, MIPS, ARM, PowerPC

**Ventajas:**
- Unidad de control simple
- Facilita pipeline profundo
- Compilador optimiza fácilmente
- Mejor paralelismo

---

### Características Clave de RISC

#### 1. Una Instrucción por Ciclo

Un ciclo máquina es el tiempo para:
- Captar dos operandos desde registros
- Realizar operación ALU
- Almacenar resultado en registro

Las instrucciones RISC ejecutan en ~1 ciclo.

#### 2. Operaciones Registro a Registro

Simplifica repertorio de instrucciones y unidad de control.

**Ejemplo:** RISC puede tener 1-2 instrucciones ADD, mientras CISC (VAX) tiene 25.

#### 3. Modos de Direccionamiento Sencillos

Casi todos usan direccionamiento simple a registro.

Modos más complejos se sintetizan por software.

#### 4. Formatos de Instrucción Sencillos

Generalmente solo 1-2 formatos.

- Longitud **fija** (alineada en límites de palabra)
- Posiciones de campos **fijas**
- Decodificación y acceso a operandos **simultáneos**

---

### Comparación RISC vs CISC

| Aspecto | RISC | CISC |
|--------|------|------|
| **Aplicación** | Entornos de red, servidor | Computadores domésticos |
| **Instrucciones** | Tamaño fijo, pocas | Amplias y variadas |
| **Acceso memoria** | Solo load/store | Memoria y registros |
| **Objetivo** | Segmentación y paralelismo | Operaciones complejas |
| **Ciclos por instrucción** | ~1 | Variable (2-10+) |
| **Compilador** | Más simple | Más complejo |

---

# PARTE 8: ARQUITECTURA DE COMPUTADORAS PARALELAS

## 1. Introducción

Tradicionalmente, los computadores se han visto como **máquinas secuenciales**:

- El programador especifica algoritmos mediante **secuencia de instrucciones**
- Los procesadores ejecutan **una instrucción por vez**

Sin embargo, a niveles más bajos existe paralelismo:
- **Nivel de microoperación:** múltiples señales de control simultáneas
- **Segmentación (Pipeline):** solapamiento de captación y ejecución
- **Superescalar:** múltiples unidades de ejecución en paralelo

---

## 2. Taxonomía de Flynn

Clasificación de sistemas según capacidades de procesamiento paralelo.

### SISD (Single Instruction, Single Data)

**Una secuencia de instrucciones, una secuencia de datos**

- Único procesador interpreta única secuencia de instrucciones
- Computadores monoprocesador tradicionales

---

### SIMD (Single Instruction, Multiple Data)

**Una secuencia de instrucciones, múltiples secuencias de datos**

- Una instrucción controla paso a paso ejecución simultánea
- Cada elemento de proceso tiene memoria asociada
- Misma instrucción ejecutada con conjuntos de datos diferentes

**Ejemplos:**
- Procesadores vectoriales
- Procesadores matriciales

---

### MISD (Multiple Instruction, Single Data)

**Múltiples secuencias de instrucciones, una secuencia de datos**

- Secuencia de datos transmitida a conjunto de procesadores
- Cada procesador ejecuta instrucciones diferentes

**Nota:** Nunca ha sido implementada en la práctica.

---

### MIMD (Multiple Instruction, Multiple Data)

**Múltiples secuencias de instrucciones, múltiples secuencias de datos**

- Conjunto de procesadores ejecuta **simultáneamente**
- Instrucciones diferentes con **datos diferentes**

**Ejemplos:**
- SMP (Multiprocesadores Simétricos)
- Clusters
- Sistemas NUMA

---

## 3. Multiprocesadores Simétricos (SMP)

### Definición

Un SMP es computador con:

1. **Dos o más procesadores** similares de capacidades comparables
2. Procesadores **comparten memoria principal y E/S**
3. Interconexión mediante **bus u otro sistema de interconexión**
4. Tiempo de acceso a memoria **aproximadamente igual** para todos
5. Todos procesadores comparten **dispositivos de E/S**
6. Todos pueden desempeñar **mismas funciones** (simetría)
7. Controlados por **único sistema operativo integrado**

---

### Ventajas de SMP

**Prestaciones:** Si trabajo se organiza en paralelo, varios procesadores proporcionan mejor rendimiento.

**Disponibilidad:** Fallo en un procesador no detiene computador (otros continúan).

**Crecimiento incremental:** Se pueden agregar más procesadores.

**Escalado:** Fabricantes ofrecen rango de productos.

---

### Diferencia con Clusters

En clusters, la **unidad de interacción es mensaje o archivo completo**.

En SMP, la **interacción se produce a nivel de elementos de datos individuales**, permitiendo **elevado nivel de cooperación**.

---

## 4. Organización de SMP

```
┌────────────┐  ┌────────────┐  ┌────────────┐
│   CPU 1    │  │   CPU 2    │  │   CPU N    │
│ (Control + │  │ (Control + │  │ (Control + │
│   ALU)     │  │   ALU)     │  │   ALU)     │
└─────┬──────┘  └─────┬──────┘  └─────┬──────┘
      │               │               │
      └───────────────┼───────────────┘
                      │
              ┌───────┴────────┐
              │  BUS COMPARTIDO│
              └───────┬────────┘
                      │
         ┌────────────┼────────────┐
         │            │            │
    ┌────────┐  ┌─────────┐  ┌────────┐
    │Memoria │  │Memoria  │  │Módulos │
    │Principal│  │Caché L2 │  │ E/S   │
    └────────┘  └─────────┘  └────────┘
```

---

## 5. Bus de Tiempo Compartido

### Características

El mecanismo más simple para construir SMP.

- Estructura similar a computador de un procesador
- Bus consta de líneas: **control, dirección y datos**

### Funciones Necesarias

**Direccionamiento:**
- Distinguir módulos del bus
- Determinar fuente y destino de datos

**Arbitraje:**
- Múltiples módulos compiten por control del bus
- Esquema de prioridad para arbitrar

**Tiempo Compartido:**
- Módulo controla bus → otros deben esperar
- Permite únicamente un operador por vez

---

## 6. Ventajas del Bus Compartido

**Simplicidad:**
- Interfaz física igual que sistema monoprocesador
- Lógica de direccionamiento y arbitraje standard

**Flexibilidad:**
- Fácil agregar procesadores al bus

**Fiabilidad:**
- Bus es medio pasivo
- Fallo de dispositivo no causa fallo del sistema

---

## 7. Desventaja Principal: Prestaciones

**Cuello de botella:**
- Todas referencias a memoria pasan por bus
- Velocidad sistema limitada por tiempo de ciclo

**Solución: Cachés**
- Cada procesador con caché **reduce dramáticamente** accesos a bus
- Típicamente: L1 interna + L2 externa
- Algunos sistemas usan L3

---

## 8. Coherencia de Caché en Multiprocesadores

### El Problema

Si cada caché local tiene copia de parte de memoria:
- Alteración en una caché invalida copia en otra
- Se produce **inconsistencia**

### Protocolos de Coherencia

Dos aproximaciones principales:

**Software:**
- Compilador marca datos problemáticos
- Sistema operativo previene cacheo de datos compartidos

**Hardware:**
- Protocolo de **snooping** (espionaje de bus)
- Protocolo de **directorio** (tabla centralizada)

Típicamente resuelta por hardware, no sistema operativo.

---

## 9. Protocolo MESI

Estados para cada línea de caché en multiprocesador:

| Estado | Significado | Descripción |
|--------|-------------|-------------|
| **M** | Modified | Línea ha sido modificada, solo en esta caché |
| **E** | Exclusive | Igual a memoria principal, no en otra caché |
| **S** | Shared | Igual a memoria, pero puede estar en otra caché |
| **I** | Invalid | Línea no contiene datos válidos |

---

### Fallo de Lectura en MESI

Cuando procesador necesita dato no en caché:

1. **Si otra caché tiene copia EXCLUSIVA:**
   - La devuelve y cambia a SHARED
   - Procesador recibe dato

2. **Si otras cachés tienen copia SHARED:**
   - Leen y pasan a SHARED

3. **Si otra caché tiene copia MODIFIED:**
   - Bloquea lectura de memoria
   - Proporciona línea, cambia a SHARED

4. **Si ninguna tiene copia:**
   - Lee de memoria, estado = EXCLUSIVE

---

### Acierto de Lectura en MESI

Dato ya en caché local:
- CPU simplemente lee
- **Sin cambio de estado**

---

### Fallo de Escritura en MESI

Cuando procesador escribe en dato no en caché:
- Envía RWITM (Read-With-Intent-To-Modify)
- Línea se marca como MODIFIED inmediatamente

---

### Acierto de Escritura en MESI

Efecto depende del estado:

**Si SHARED:**
- Obtiene acceso exclusivo
- Otras cachés invalidan su copia (I)
- Cambia a MODIFIED

**Si EXCLUSIVE:**
- Simplemente actualiza
- Cambia a MODIFIED

**Si MODIFIED:**
- Simplemente actualiza
- Mantiene MODIFIED

---

## Fin del Documento

Apuntes completos de Arquitectura II cubriendo teoría fundamental, ejercicios resueltos, conceptos de procesadores modernos y arquitecturas paralelas.

---

## Apéndice: Respuestas rápidas (no repetir)

- Coherencia de caché: políticas (write-through / post-escritura), protocolos (snooping / directorio), aproximaciones (hardware suele resolver por latencia).
- MESI: suele usarse con write-back (post-escritura) y un protocolo de snooping en buses; si la línea está modificada no se escribe a MP hasta reemplazo y las caches se interrogan/coordina para mantener coherencia.
- Post-escritura (write-back): la línea modificada permanece en caché y no se escribe inmediatamente a memoria principal; otras caches/lecturas consultan caches y se realizan invalidaciones/transferencias según el protocolo.
- RISC vs CISC: RISC = instrucciones simples, pipeline y decodificación sencilla; CISC = instrucciones complejas y microcódigo más pesado.
- Modos de direccionamiento / Pentium: la dirección lineal se forma como dirección efectiva + registro de segmento (segundo nivel en Pentium); el opcode (CODOP) siempre está presente.
- Paralelismo vs segmentación (pipelining): paralelismo ejecuta instrucciones simultáneamente en distintos procesadores; segmentación divide una instrucción en etapas que se solapan en pipeline.
- NUMA vs SMP: NUMA tiene memoria distribuida con latencias no uniformes; SMP tiene memoria compartida de acceso uniforme.
- Acoplamiento: débilmente acoplado vs fuertemente acoplado — cuánto intercambio/comunicación requieren los nodos.
- Transparente: comportamiento invisible para procesos vecinos (p. ej. migración o replicación transparente).
- Formas de DMA: "storm" (bus mastering y transferencia de bloques grandes), "robo de ciclos" (cycle stealing, toma breves ventanas), "transparente" (espera breves ventanas sin bloquear CPU).
- Módulos: dispositivos externos gestionados por controladores (I/O, buses, periféricos).
- Pipelining: precarga y solapamiento de etapas para reducir tiempo total; practicar la fórmula de speedup/latencia del pipeline.

**Última actualización:** 2026-06-13