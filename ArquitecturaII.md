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
