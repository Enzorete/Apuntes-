---
title: "Arquitectura II"
subtitle: "Verdadero / Falso (1 al 8) y Ejercicios de Caché"
author: "Apuntes de cátedra"
date: "2026-05-06"
lang: "es-AR"
---

# Arquitectura II

> Resumen de verdadero/falso y ejercicios resueltos de memoria caché.

## Índice
- [Parte 1 - Verdadero / Falso](#parte-1---verdadero--falso)
  - [1. NMI](#1-las-interrupciones-nmi-son-interrupciones-que-no-pueden-aplazarse-o-anularse)
  - [2. DMA polling](#2-el-método-dma-es-administración-de-es-programada-donde-pregunta-en-secuencia-si-un-periférico-necesita-atención)
  - [3. Modos DMA](#3-el-método-dma-puede-operar-de-una-sola-manera-la-cual-es-detención-de-cpu)
  - [4. Robo de ciclos](#4-en-dma-en-la-técnica-de-robo-de-ciclos-tiene-la-restricción-de-poder-transmitir-una-palabra-usando-los-semiciclos-de-reloj-que-no-utiliza-la-cpu)
  - [5. Complemento a 2](#5-en-complemento-a-dos-el-binario-1001-representa-el-número-9)
  - [6. Negación C2](#6-el-proceso-de-negación-en-complemento-a-dos-es-realizar-el-complemento-a-uno-y-luego-sumar-1)
  - [7. IEEE 754](#7-en-coma-flotante-el-método-adoptado-desde-1985-es-el-mecanismo-de-punto-fijo)
  - [8. Overflow exponente](#8-en-operaciones-con-números-en-coma-flotante-puede-ocurrir-el-desbordamiento-del-exponente)
- [Parte 2 - Ejercicios](#parte-2---ejercicios-de-memoria-caché)
  - [Ejercicio 1](#ejercicio-1---tiempo-promedio)
  - [Ejercicio 2](#ejercicio-2---variante)
  - [Ejercicio 3](#ejercicio-3---mapeo-directo)
  - [Ejercicio 4](#ejercicio-4---mapeo-asociativo)
  - [Ejercicio 5](#ejercicio-5---bloque-y-tiempo-promedio)
  - [Ejercicio 6](#ejercicio-6---asociativa-por-conjuntos)
  - [Ejercicio 7](#ejercicio-7---mapeo-directo-completo)

---

## Parte 1 - Verdadero / Falso

### 1) Las interrupciones NMI son interrupciones que no pueden aplazarse o anularse.
**Respuesta:** <span style="background:#10b981;color:white;padding:2px 8px;border-radius:6px;font-weight:700">VERDADERO</span>  
NMI = Non-Maskable Interrupt. Se usan para fallos críticos y la CPU no las puede enmascarar.

### 2) El método DMA es administración de E/S programada donde pregunta en secuencia si un periférico necesita atención.
**Respuesta:** <span style="background:#ef4444;color:white;padding:2px 8px;border-radius:6px;font-weight:700">FALSO</span>  
Eso es <span style="color:#ef4444">polling</span>. DMA transfiere directo a memoria sin intervención continua de la CPU.

### 3) El método DMA puede operar de una sola manera, la cual es detención de CPU.
**Respuesta:** <span style="background:#ef4444;color:white;padding:2px 8px;border-radius:6px;font-weight:700">FALSO</span>  
Tres modos clásicos: <span style="color:#2563eb">detención de CPU (ráfaga)</span>, <span style="color:#2563eb">robo de ciclo</span> y <span style="color:#2563eb">DMA transparente</span>.

### 4) En DMA, en la técnica de robo de ciclos, tiene la restricción de poder transmitir una palabra usando los semiciclos de reloj que no utiliza la CPU.
**Respuesta:** <span style="background:#10b981;color:white;padding:2px 8px;border-radius:6px;font-weight:700">VERDADERO</span>  
Roba un ciclo de bus por vez. En los apuntes se explica como "semiciclo".

### 5) En complemento a dos, el binario 1001 representa el número 9.
**Respuesta:** <span style="background:#ef4444;color:white;padding:2px 8px;border-radius:6px;font-weight:700">FALSO</span>  
Con 4 bits, MSB=1 → negativo. 1001 = <span style="color:#7c3aed">-7 en C2</span>. Como sin signo sí sería 9.

### 6) El proceso de negación en complemento a dos es realizar el complemento a uno y luego sumar 1.
**Respuesta:** <span style="background:#10b981;color:white;padding:2px 8px;border-radius:6px;font-weight:700">VERDADERO</span>

### 7) En coma flotante, el método adoptado desde 1985 es el mecanismo de punto fijo.
**Respuesta:** <span style="background:#ef4444;color:white;padding:2px 8px;border-radius:6px;font-weight:700">FALSO</span>  
Desde 1985 rige <span style="color:#2563eb">IEEE 754</span> para punto flotante.

### 8) En operaciones con números en coma flotante, puede ocurrir el desbordamiento del exponente.
**Respuesta:** <span style="background:#10b981;color:white;padding:2px 8px;border-radius:6px;font-weight:700">VERDADERO</span>  
Overflow y underflow de exponente son errores típicos.

---

## Parte 2 - Ejercicios de Memoria Caché

### Ejercicio 1 - Tiempo promedio
**Datos:** $T_1 = 1$ ns, $T_2 = 10$ ns, $H = 0,90$, línea 256 palabras

**Fórmula:**
$$ T_s = T_1 + (1-H) \cdot T_2 $$

$$ T_s = 1 + (1-0,9) 	 10 = 2\ 	{ns} $$

### Ejercicio 2 - Variante
**Datos:** $T_1 = 1$ ns, $T_2 = 10$ ns, $H = 0,975$

$$ T_s = 1 + (1-0,975) 	 10 = 1,25\ 	{ns} $$

### Ejercicio 3 - Mapeo directo
**Datos:** MP = 256M palabras de 16 bits, Caché = 1M palabras, línea = 256 palabras

- MP: $256	{M} = 2^{28}$ → <span style="color:#2563eb">28 bits</span>
- Offset palabra: $\log_2(256) = 8$ bits
- Líneas caché: $2^{20} / 2^8 = 2^{12} = 4096$ → <span style="color:#2563eb">12 bits</span>
- Etiqueta: $28 - 12 - 8 = 8$ bits

**Formato:** <code style="background:#eef2ff;color:#3730a3;padding:2px 6px;border-radius:4px">Etiqueta 8</code> <code style="background:#eef2ff;color:#3730a3;padding:2px 6px;border-radius:4px">Línea 12</code> <code style="background:#eef2ff;color:#3730a3;padding:2px 6px;border-radius:4px">Palabra 8</code>

**Bloques en MP:** $2^{28} / 2^8 = 2^{20} = 1.048.576$

### Ejercicio 4 - Mapeo asociativo
**Datos:** MP = 256M palabras, Caché = 1M palabras, línea = 256 palabras

En asociativo no hay campo de línea.

- Offset: <span style="color:#7c3aed">8 bits</span>
- Etiqueta: $28 - 8 = 20$ bits

**Formato:** <code style="background:#f5f3ff;color:#5b21b6;padding:2px 6px;border-radius:4px">Etiqueta 20</code> <code style="background:#f5f3ff;color:#5b21b6;padding:2px 6px;border-radius:4px">Palabra 8</code>

**Bloques en MP:** $2^{20} = 1.048.576$

### Ejercicio 5 - Bloque y tiempo promedio
**Datos:** 32 bits, caché 256 KB, línea 64 bytes, $T_1 = 5$ ns, $T_2 = 200$ ns, $T_s$ deseado = 20 ns, 4 vías LRU

**a) Tamaño de bloque**
$$ 	{bloque} = 	{línea} = 64\ 	{bytes} $$

**b) Tasa de aciertos necesaria**
$$ 20 = 5 + (1-H) \cdot 200 $$
$$ 1-H = 15/200 = 0,075 $$
$$ H = 0,925 = 92,5\% $$

> <span style="color:#92400e">El bloque es la unidad de transferencia. La CPU trae 64 bytes juntos, no uno solo.</span>

### Ejercicio 6 - Asociativa por conjuntos
**Datos:** Direcciones 32 bits, byte direccionable, caché 64 KB, 4 vías, línea = 4 palabras, $T_c = 2$ ns, $T_f = 80$ ns

**a) Memoria direccionable**
$$ 2^{32}\ 	{bytes} = 4096\ 	{MB} $$

**b) Palabras en caché**
- 64 KB = 65536 bytes
- Asumiendo palabra = 4 bytes → línea = 16 bytes
- Líneas = 65536 / 16 = 4096
- Palabras totales = 4096 × 4 = 16384

**c) Líneas por conjunto**
$$ 4 $$

**d) Número de líneas**
$$ 4096 $$

**e) Número de conjuntos**
$$ 4096 / 4 = 1024 $$

**f) H para $T_s = 10$ ns**
$$ 10 = 2 + (1-H) \cdot 80 $$
$$ H = 0,9 = 90\% $$

### Ejercicio 7 - Mapeo directo completo
**Datos:** MP 8 MB, $T_{mp}=1260$ ns, caché 4 KB, $T_c=120$ ns, línea 256 B, accesos 1.200.000, fallos 600.000

**1) Tiempo medio**
$$ H = 600.000 / 1.200.000 = 0,5 $$
$$ T_s = 120 + 0,5 	* 1260 = 750\ 	{ns} $$

**2) Campos de dirección**
- MP 8 MB = $2^{23}$ bytes → 23 bits
- Offset: $\log_2(256) = 8$ bits
- Líneas: $4096 / 256 = 16 = 2^4$ → 4 bits
- Etiqueta: $23 - 4 - 8 = 11$ bits

**Formato:** <code style="background:#dbeafe;color:#1e40af;padding:2px 6px;border-radius:4px">Etiqueta 11</code> <code style="background:#dbeafe;color:#1e40af;padding:2px 6px;border-radius:4px">Línea 4</code> <code style="background:#dbeafe;color:#1e40af;padding:2px 6px;border-radius:4px">Offset 8</code>
