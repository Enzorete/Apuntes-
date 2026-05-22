---
title: "Arquitectura II"
subtitle: "Verdadero / Falso (1 al 8) y Ejercicios de Caché"
author: "Apuntes de cátedra"
date: "2026-05-06"
lang: "es-AR"
---

# Arquitectura II

> Resumen completo con teoría, verdadero/falso y ejercicios resueltos de memoria caché.

## Índice
- [Parte 0 - Teoría esencial](#parte-0---teoría-esencial)
- [Parte 1 - Verdadero / Falso](#parte-1---verdadero--falso)
- [Parte 2 - Ejercicios de Memoria Caché](#parte-2---ejercicios-de-memoria-caché)

---

## Parte 0 - Teoría esencial

### Interrupciones
- **Enmascarables (IRQ):** la CPU puede ignorarlas con la bandera IF.
- **No enmascarables (NMI):** no se pueden deshabilitar. Para errores críticos (fallo de alimentación, paridad de memoria).

### DMA (Acceso Directo a Memoria)
Permite que periféricos transfieran datos a RAM sin pasar por la CPU.
1. **Ráfaga (burst):** CPU cede el bus completo hasta terminar.
2. **Robo de ciclo:** toma un ciclo de bus entre instrucciones de CPU.
3. **Transparente:** usa ciclos donde CPU no accede a bus.

### Complemento a dos (C2)
Rango con n bits: $[-2^{n-1}, 2^{n-1}-1]$
- Negativo: invertir bits y sumar 1.
- Ejemplo 4 bits: 1001 → invertir 0110 +1 = 0111 = 7 → entonces 1001 = -7

### IEEE 754 (1985)
Formato coma flotante estándar:
- Simple precisión: 1 bit signo, 8 exponente, 23 mantisa
- Doble precisión: 1, 11, 52
- Problemas: overflow/underflow de exponente, redondeo.

### Memoria Caché
Principio de localidad temporal y espacial.
- **Hit rate H:** probabilidad de encontrar dato en caché.
- **Tiempo medio:** $T_s = T_1 + (1-H) \cdot T_2$
- **Mapeo directo:** dirección = etiqueta + línea + offset
- **Asociativo:** dirección = etiqueta + offset
- **Por conjuntos:** dirección = etiqueta + conjunto + offset

---

## Parte 1 - Verdadero / Falso

### 1) Las interrupciones NMI son interrupciones que no pueden aplazarse o anularse.
**Respuesta: ✅ VERDADERO**  
NMI = Non-Maskable Interrupt. Se usan para fallos críticos y la CPU no las puede enmascarar.

### 2) El método DMA es administración de E/S programada donde pregunta en secuencia si un periférico necesita atención.
**Respuesta: ❌ FALSO**  
Eso es **polling**. DMA transfiere directo a memoria sin intervención continua de la CPU.

### 3) El método DMA puede operar de una sola manera, la cual es detención de CPU.
**Respuesta: ❌ FALSO**  
Tres modos clásicos: **detención de CPU (ráfaga)**, **robo de ciclo** y **DMA transparente**.

### 4) En DMA, en la técnica de robo de ciclos, tiene la restricción de poder transmitir una palabra usando los semiciclos de reloj que no utiliza la CPU.
**Respuesta: ✅ VERDADERO**  
Roba un ciclo de bus por vez. En los apuntes se explica como "semiciclo".

### 5) En complemento a dos, el binario 1001 representa el número 9.
**Respuesta: ❌ FALSO**  
Con 4 bits, MSB=1 → negativo. 1001 = **-7 en C2**. Como sin signo sí sería 9.

### 6) El proceso de negación en complemento a dos es realizar el complemento a uno y luego sumar 1.
**Respuesta: ✅ VERDADERO**

### 7) En coma flotante, el método adoptado desde 1985 es el mecanismo de punto fijo.
**Respuesta: ❌ FALSO**  
Desde 1985 rige **IEEE 754** para punto flotante.

### 8) En operaciones con números en coma flotante, puede ocurrir el desbordamiento del exponente.
**Respuesta: ✅ VERDADERO**  
Overflow y underflow de exponente son errores típicos.

---

## Parte 2 - Ejercicios de Memoria Caché

### Ejercicio 1 - Tiempo promedio
**Datos:** $T_1 = 1$ ns, $T_2 = 10$ ns, $H = 0,90$, línea 256 palabras

$$ T_s = T_1 + (1-H) \cdot T_2 $$
$$ T_s = 1 + (1-0,9) \times 10 = 2\ \text{ns} $$

### Ejercicio 2 - Variante
**Datos:** $T_1 = 1$ ns, $T_2 = 10$ ns, $H = 0,975$

$$ T_s = 1 + (1-0,975) \times 10 = 1,25\ \text{ns} $$

### Ejercicio 3 - Mapeo directo
**Datos:** MP = 256M palabras de 16 bits, Caché = 1M palabras, línea = 256 palabras

- MP: $256\text{M} = 2^{28}$ → **28 bits**
- Offset palabra: $\log_2(256) = 8$ bits
- Líneas caché: $2^{20} / 2^8 = 2^{12} = 4096$ → **12 bits**
- Etiqueta: $28 - 12 - 8 = 8$ bits

**Formato:** `| Etiqueta 8 | Línea 12 | Palabra 8 |`

**Bloques en MP:** $2^{28} / 2^8 = 2^{20} = 1.048.576$

### Ejercicio 4 - Mapeo asociativo
**Datos:** MP = 256M palabras, Caché = 1M palabras, línea = 256 palabras

En asociativo no hay campo de línea.

- Offset: **8 bits**
- Etiqueta: $28 - 8 = 20$ bits

**Formato:** `| Etiqueta 20 | Palabra 8 |`

**Bloques en MP:** $2^{20} = 1.048.576$

### Ejercicio 5 - Bloque y tiempo promedio
**Datos:** 32 bits, caché 256 KB, línea 64 bytes, $T_1 = 5$ ns, $T_2 = 200$ ns, $T_s$ deseado = 20 ns, 4 vías LRU

**a) Tamaño de bloque**
$$ \text{bloque} = \text{línea} = 64\ \text{bytes} $$

**b) Tasa de aciertos necesaria**
$$ 20 = 5 + (1-H) \cdot 200 $$
$$ 1-H = \frac{15}{200} = 0,075 $$
$$ H = 0,925 = 92,5\% $$

> El bloque es la unidad de transferencia. La CPU trae 64 bytes juntos, no uno solo.

### Ejercicio 6 - Asociativa por conjuntos
**Datos:** Direcciones 32 bits, byte direccionable, caché 64 KB, 4 vías, línea = 4 palabras, $T_c = 2$ ns, $T_f = 80$ ns

**a) Memoria direccionable**
$$ 2^{32}\ \text{bytes} = 4096\ \text{MB} $$

**b) Palabras en caché**
- 64 KB = 65536 bytes
- Asumiendo palabra = 4 bytes → línea = 16 bytes
- Líneas = 65536 / 16 = 4096
- Palabras totales = 4096 × 4 = 16384

**c) Líneas por conjunto:** 4  
**d) Número de líneas:** 4096  
**e) Número de conjuntos:** $4096 / 4 = 1024$

**f) H para $T_s = 10$ ns**
$$ 10 = 2 + (1-H) \cdot 80 $$
$$ H = 0,9 = 90\% $$

### Ejercicio 7 - Mapeo directo completo
**Datos:** MP 8 MB, $T_{mp}=1260$ ns, caché 4 KB, $T_c=120$ ns, línea 256 B, accesos 1.200.000, fallos 600.000

**1) Tiempo medio**
$$ H = \frac{600000}{1200000} = 0,5 $$
$$ T_s = 120 + 0,5 \times 1260 = 750\ \text{ns} $$

**2) Campos de dirección**
- MP 8 MB = $2^{23}$ bytes → 23 bits
- Offset: $\log_2(256) = 8$ bits
- Líneas: $4096 / 256 = 16 = 2^4$ → 4 bits
- Etiqueta: $23 - 4 - 8 = 11$ bits

**Formato:** `| Etiqueta 11 | Línea 4 | Offset 8 |`
