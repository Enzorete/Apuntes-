---
title: "Arquitectura II"
subtitle: "Verdadero / Falso (1 al 8)"
author: "Apuntes de cátedra"
date: "2026-05-06"
lang: "es-AR"
---

# Arquitectura II

## Verdadero / Falso (1 al 8)

### 1) Las interrupciones NMI son interrupciones que no pueden aplazarse o anularse.
**Respuesta: Verdadero**

NMI = *Non-Maskable Interrupt*. Se crearon para fallos críticos (alimentación, error de paridad) y la CPU no las puede enmascarar.

---

### 2) El método DMA es administración de E/S programada donde pregunta en secuencia si un periférico necesita atención.
**Respuesta: Falso**

Eso describe *polling* (E/S programada). DMA es lo contrario: el controlador toma el bus y mueve datos directo a memoria sin que la CPU pregunte.

---

### 3) El método DMA puede operar de una sola manera, la cual es detención de CPU.
**Respuesta: Falso**

Hay tres formas clásicas: detención de CPU (ráfaga), robo de ciclo y DMA transparente. Detención es solo una.

---

### 4) En DMA, en la técnica de robo de ciclos, tiene la restricción de poder transmitir una palabra usando los semiciclos de reloj que no utiliza la CPU.
**Respuesta: Verdadero**

En los apuntes de la materia lo toman así. La idea clave es que roba un ciclo de bus por vez y mueve una palabra. Algunos libros lo explican con "semiciclos", otros solo "cuando la CPU no usa el bus".

---

### 5) En complemento a dos, el binario 1001 representa el número 9.
**Respuesta: Falso**

Con 4 bits, MSB=1 indica negativo. 1001 → inviertes (0110) +1 = 0111 = 7 → es **-7**. Como entero sin signo sí sería 9, pero en C2 no.

---

### 6) El proceso de negación en complemento a dos es realizar el complemento a uno y luego sumar 1.
**Respuesta: Verdadero**

Esa es la definición exacta.

---

### 7) En coma flotante, el método adoptado desde 1985 es el mecanismo de punto fijo.
**Respuesta: Falso**

Desde 1985 rige **IEEE 754** para punto flotante, no punto fijo.

---

### 8) En operaciones con números en coma flotante, puede ocurrir el desbordamiento del exponente.
**Respuesta: Verdadero**

Overflow y underflow del exponente son los dos errores típicos.

---

## Ejercicios de Memoria Caché

### 1) Tiempo promedio de acceso
**Enunciado:** Memoria caché $T_1 = 1$ ns/palabra, memoria principal $T_2 = 10$ ns/palabra, tasa de aciertos $H = 0{,}90$, líneas de 256 palabras.

**Paso 1: Identificar qué piden**
- "Tiempo promedio de acceso" → usar $T_s = T_1 + (1-H) \cdot T_2$

**Paso 2: Sacar los datos**
- $T_1 = 1$ ns
- $T_2 = 10$ ns
- $H = 0{,}90$

**Solución:**
$$
T_s = 1 + (1-0{,}9) \times 10 = 1 + 1 = 2\ \text{ns}
$$

---

### 2) Tiempo promedio de acceso (variante)
**Enunciado:** $T_1 = 1$ ns/palabra, $T_2 = 10$ ns/palabra, $H = 0{,}975$, líneas de 1024 palabras.

**Solución:**
$$
T_s = 1 + (1-0{,}975) \times 10 = 1 + 0{,}25 = 1{,}25\ \text{ns}
$$

---

### 3) Mapeo directo
**Enunciado:** Memoria principal de 256M palabras de 16 bits. Caché de 1M palabras, mapeo directo, líneas de 256 palabras.

**a) Bits de etiqueta, línea y palabra**

**Paso 1: Pasar todo a potencia de 2**
- Memoria principal: $256\text{M} = 256 \cdot 2^{20} = 2^8 \cdot 2^{20} = 2^{28}$
- Caché: $1\text{M} = 2^{20}$
- Tamaño de línea: $256 = 2^8$

**Paso 2: Bits de dirección total**
- $2^{28} \Rightarrow 28$ bits

**Paso 3: Bits de palabra (offset)**
- $\log_2(256) = 8 \Rightarrow 8$ bits

**Paso 4: Cantidad de líneas de caché**
- $\frac{2^{20}}{2^8} = 2^{12}$
- Cantidad de líneas = $2^{12} = 4096$
- Bits de línea = $12$ bits

**Paso 5: Bits de etiqueta**
- $\text{Etiqueta} = 28 - 12 - 8 = 8$ bits

**Formato de dirección:** | Etiqueta (8) | Línea (12) | Palabra (8) |

**b) Cantidad de bloques de memoria principal**

**Paso 6: Cantidad de bloques**
- $\frac{2^{28}}{2^8} = 2^{20}$
- Bloques = $2^{20} = 1.048.576$

# Ejercicio 4: Mapeo Asociativo

**Enunciado:** Se tiene una unidad de memoria de 256M palabras de 16 bits, y una memoria caché de 1M palabras. La caché utiliza mapeo asociativo y está dividida en líneas de 256 palabras cada una.

**Calcular:**
- a) ¿Cuántos bits hay en los campos de etiqueta y palabra?
- b) Cantidad de bloques de memoria principal.

# ¿Qué es mapeo asociativo?

Es una forma de organizar la caché donde:
- cualquier bloque de memoria puede ir a **cualquier línea de caché**
- **NO SE CALCULA LA LÍNEA**

---

## Datos

**Memoria principal:**
$$
256\text{M} = 256 \cdot 2^{20} = 2^8 \cdot 2^{20} = 2^{28}
$$

### a) Campos de dirección

- **Palabra (offset):**
$$
\log_2(256) = 8 \Rightarrow 8\ \text{bits}
$$

- **Etiqueta:**
$$
\text{etiqueta} = 28\ \text{bits} - 8\ \text{bits} = 20\ \text{bits}
$$

### b) Cantidad de bloques
$$
\text{bloques} = \frac{2^{28}}{2^8} = 2^{20}
$$

### Paso 5: Bits de etiqueta
En mapeo asociativo no hay campo de línea, por lo tanto:
$$
\text{Etiqueta} = 28 - 8 = 20 \text{ bits}
$$

**Formato de dirección:** | Etiqueta (20) | Palabra (8) |

### Paso 6: Cantidad de bloques de memoria principal
$$
\frac{2^{28}}{2^8} = 2^{20}
$$
$$
\text{Bloques} = 2^{20} = 1.048.576
$$

# Ejercicio de caché: bloque y tiempo promedio

# Ejercicio 5

**Enunciado:** Sea un computador de 32 bits con una memoria caché de 256 KB, líneas de 64 bytes y un tiempo de acceso de 5 ns. La caché es asociativa por conjuntos de 4 vías y se emplea la política de reemplazo LRU.

**Calcular:**

### a) ¿Cuál es el tamaño de los bloques que se transfieren entre la memoria caché y la memoria principal?

El bloque es la unidad de transferencia y coincide con la línea de caché.

$$
\text{bloque} = \text{línea} = 64\ \text{bytes}
$$

### b) Si el tiempo para transferir un bloque de memoria principal a caché es de 200 ns, indique la tasa de aciertos a caché necesaria, de forma que el tiempo medio de acceso al sistema de memoria sea de 20 ns.

**Datos:**
- $T_1 = 5\ \text{ns}$ (caché)
- $T_2 = 200\ \text{ns}$ (fallo)
- $T_s = 20\ \text{ns}$ (deseado)

**Fórmula:**
$$
T_s = T_1 + (1-H) \cdot T_2
$$

**Resolución:**
$$
20 = 5 + (1-H) \cdot 200
$$
$$
15 = (1-H) \cdot 200
$$
$$
1-H = \frac{15}{200} = \frac{3}{40}
$$
$$
H = 1 - \frac{3}{40} = \frac{37}{40} = 0{,}925
$$

**Respuesta:** $H = 92{,}5\%$


## Conceptos clave

> **Bloque = pedazo de memoria que se copia completo desde memoria principal a caché**

> El bloque es la **unidad de transferencia** entre memoria principal y caché, y tiene el **mismo tamaño que la línea de caché**.

**Pensalo así:** la CPU no trae 1 dato solo, trae un grupo de datos juntos.

- Ese grupo = bloque
- En tu ejercicio te dicen: *línea de caché = 64 bytes*

**Entonces:** cada línea puede guardar 64 bytes, y lo que se copia desde memoria también es de 64 bytes.

---

**Conclusión:** Para que el tiempo promedio de acceso sea de 20 ns, la caché debe acertar al menos 37 de cada 40 accesos (92,5%). De esa forma, el costo de los fallos (200 ns) se diluye lo suficiente como para compensar los 5 ns del acierto.

# Ejercicio 6

**Enunciado:** Se dispone de un computador con direcciones de memoria de 32 bits, que direcciona la memoria por bytes. El computador dispone de una memoria caché asociativa por conjuntos de 4 vías, con un tamaño de línea de 4 palabras. Dicha caché tiene un tamaño de 64 KB. El tiempo de acceso a la memoria caché es de 2 ns y el tiempo necesario para tratar un fallo de caché es de 80 ns.

**Calcular:**

### a) Tamaño en MB de la memoria que se puede direccionar en este computador
- 32 bits → $2^{32}$ bytes
$$
\frac{2^{32}}{2^{20}} = 2^{12} = 4096\ \text{MB}
$$

### b) Número de palabras que se pueden almacenar en la memoria caché
- 64 KB = 65536 bytes
- tamaño de línea = 4 palabras = 4 bytes
- cantidad de líneas = $65536 / 4 = 16384$
- cantidad de palabras (según líneas) = 16384 palabras

### c) Número de líneas que se pueden almacenar en el mismo conjunto
$$
4\ \text{líneas}
$$

### d) Número de líneas de la caché
- 64 KB = 65536 bytes
- tamaño de línea = 4 palabras = 4 bytes
$$
\text{cantidad de líneas} = 65536 / 4 = 16384\ \text{líneas}
$$
- caché de 4 vías
- cantidad de conjuntos = $16384 / 4 = 4096$

### e) Número de conjuntos de la caché
$$
4096 / 4 = 1024\ \text{conjuntos}
$$

### f) Tasa de aciertos necesaria para $T_s = 10$ ns
$$
10\text{ns} = 2\text{ns} + (1-H) \cdot 80\text{ns}
$$
$$
8\text{ns} = (1-H) \cdot 80\text{ns}
$$
$$
\frac{1}{10} = 1-H
$$
$$
H = 1 - \frac{1}{10} = 0{,}9
$$

**Respuesta:** 90% tasa de aciertos

# Ejercicio 7

**Enunciado:**  
Dada las especificaciones de una computadora de 32 bits cuenta con una memoria ppal. de 8MB con tiempo de acceso de 1 260ns y una memoria cache de 4KB con un tiempo de acceso de 120ns con correspondencia directa. Se registran 600 000 fallas en cache con un total de 1 200 000 accesos y el tamaño de linea es de 256 bytes.

### Indicar el tiempo medio de acceso
Ts = Tcaché + (1 - H) * Terror  
H = aciertos/totales = (1 200 000 - 600 000)/1 200 000 = 0.5  
Ts = 120ns + (1 - 0.5) * 1 260ns  
Ts = 750ns  

### Calcular los bits de cada uno de los campos de la dirección
MP = 8MB → 2³ * 2²⁰ = 2²³ → **23 bits**

1. **Offset de palabras:**  
   palabra = log2(tamaño de linea) → log2(256) = **8 bits**

2. **Bits de linea:**  
   linea = cache/linea → 2²*2¹⁰ / 256 = 2⁴ → **4 bits linea**

3. **Bits de etiqueta:**  
   etiqueta = bits direccion - linea - palabra  
   etiqueta = 23 - 4 - 8 = **11 bits**

---

### b)
MP = 2^20 * 2^3 = 2^23

TC = tamaño lineas * cantidad lineas  
2^12 = 2^8 * cantidad lineas  
2^4 = cantidad lineas → **4 bits**

palabra = log2(256) = 2^8 = **8 bits**

etiqueta = 23 - 4 - 8 = **11 bits**

### c) 
bloques = MP/bloque = 2^23/2^8 = **2^15**

---

## 12) Coherencia de caché

**a) ¿Cómo se origina un problema de coherencia de caché?**  
Pasa en sistemas multiprocesador. Cada CPU tiene su propia caché. Si el CPU 1 modifica un dato en su caché, el CPU 2 puede tener una copia vieja de ese mismo dato en su caché. Entonces los dos ven valores distintos para la misma dirección de memoria. Ahí tenés el problema de coherencia.

**b) Detallar el método transparencia de hardware para resolver el problema**  
La "transparencia de hardware" se refiere a protocolos que el hardware maneja automáticamente sin que el programador haga nada. Los dos más conocidos:

| Método | Cómo funciona |
| --- | --- |
| **Snooping/Bus watching** | Cada caché "espía" el bus. Si detecta que otro CPU escribió en una dirección que él tiene cacheada, invalida su copia o la actualiza. Protocolos tipo MSI, MESI. |
| **Directorios** | Hay un directorio central que sabe qué cachés tienen copia de cada bloque. Cuando alguien escribe, el directorio avisa solo a las cachés involucradas para invalidar/actualizar. |
