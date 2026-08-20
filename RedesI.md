# Resumen de Comunicaciones: Electricidad, Magnetismo y Ondas Electromagnéticas

## Índice

- [1. Antecedentes históricos y conceptos base](#1-antecedentes-historicos-y-conceptos-base)
  - [1.1 Antecedentes históricos](#11-antecedentes-historicos)
  - [1.2 Conceptos base](#12-conceptos-base)
  - [1.3 Ecuaciones de Maxwell - forma de Heaviside](#13-ecuaciones-de-maxwell---forma-de-heaviside)
- [2. Electromagnetismo básico](#2-electromagnetismo-basico)
- [3. Espectro electromagnético](#3-espectro-electromagnetico)
- [4. Señales analógicas y digitales](#4-senales-analogicas-y-digitales)
- [5. Amplificación y regeneración](#5-amplificacion-y-regeneracion)
- [6. Amplitud, frecuencia y fase](#6-amplitud-frecuencia-y-fase)
- [7. Onda cuadrada y tren de pulsos](#7-onda-cuadrada-y-tren-de-pulsos)
- [8. Transmisión de datos y valores de señal](#8-transmision-de-datos-y-valores-de-senal)

---

<a id="1-antecedentes-historicos-y-conceptos-base"></a>
## 1. Antecedentes históricos y conceptos base

### 1.1 Antecedentes históricos

- **Oersted (1820):** la corriente eléctrica genera un campo magnético.
- **Faraday (1831):** un campo magnético variable genera corriente eléctrica (inducción).
- **Maxwell (1860):** unificó estos fenómenos en la teoría de campos electromagnéticos.

<a id="11-antecedentes-historicos"></a>
### 1.2 Conceptos base

- La electricidad está asociada a cargas eléctricas con signos positivo y negativo.
- El magnetismo siempre es bipolar; no existen monopolos magnéticos.
- Los campos eléctricos y magnéticos son vectoriales.

<a id="13-ecuaciones-de-maxwell---forma-de-heaviside"></a>
### 1.3 Ecuaciones de Maxwell - forma de Heaviside

1. Gauss para el campo eléctrico:  
   $\nabla \cdot \mathbf{E} = \frac{\rho}{\varepsilon_0}$
2. Gauss para el campo magnético:  
   $\nabla \cdot \mathbf{B} = 0$
3. Ley de Faraday:  
   $\nabla \times \mathbf{E} = -\frac{\partial \mathbf{B}}{\partial t}$
4. Ley de Ampère-Maxwell:  
   $\nabla \times \mathbf{B} = \mu_0 \mathbf{J} + \mu_0 \varepsilon_0 \frac{\partial \mathbf{E}}{\partial t}$

> En forma oral: “Las dos ecuaciones de Gauss indican de dónde nacen los campos; Faraday dice que un campo magnético variable genera un campo eléctrico; y Ampère-Maxwell indica que una corriente o un campo eléctrico variable genera un campo magnético. Con esto se explica la radio.”

---

<a id="2-electromagnetismo-basico"></a>
## 2. Electromagnetismo básico

- **Relación fundamental:** cargas en movimiento generan campo magnético; un campo magnético variable genera campo eléctrico. El resultado es un campo electromagnético que se propaga en el vacío.
- **Ley de Ohm:** $V = I \cdot R$
- **Onda electromagnética:** $\mathbf{E} \perp \mathbf{B} \perp$ dirección de propagación.
- **Vector de Poynting:** $\mathbf{S} = \frac{1}{\mu_0} \mathbf{E} \times \mathbf{B}$
- **Parámetros principales:**  
  $c = 3 \cdot 10^8\,\text{m/s}$,  
  $f = \frac{1}{T}$,  
  $\lambda = \frac{c}{f} = c \cdot T$

---

<a id="3-espectro-electromagnetico"></a>
## 3. Espectro electromagnético

El espectro electromagnético se ordena de mayor frecuencia a menor frecuencia, y por ende de menor longitud de onda a mayor longitud de onda.

| Tipo de onda | Longitud de onda $\lambda$ | Frecuencia $f$ | Observación |
| :--- | :--- | :--- | :--- |
| Rayos gamma | $<10^{-12}$ m | $>10^{20}$ Hz | Ionizantes |
| Rayos X | $10^{-12}$ a $10^{-8}$ m | $10^{16}$ a $10^{20}$ Hz | Ionizantes |
| Ultravioleta (UV) | $10^{-8}$ a $10^{-7}$ m | $10^{15}$ a $10^{16}$ Hz | Ionizantes |
| Luz visible | $4\cdot10^{-7}$ a $7\cdot10^{-7}$ m | $4.3\cdot10^{14}$ a $7.5\cdot10^{14}$ Hz | No ionizante |
| Infrarrojo (IR) | $10^{-6}$ a $10^{-3}$ m | $10^{11}$ a $10^{14}$ Hz | No ionizante |
| Microondas | $10^{-3}$ a $10^{-1}$ m | $10^{9}$ a $10^{11}$ Hz | No ionizante |
| Radio | $10^{-1}$ a $10^{4}$ m | $10^{4}$ a $10^{9}$ Hz | No ionizante |

- **Relación clave:** $\lambda = \frac{c}{f}$
- **A medida que aumenta la frecuencia, disminuye la longitud de onda.**
- **Ionizantes:** UV, rayos X y rayos gamma. Tienen energía suficiente para arrancar electrones y alterar moléculas, incluso el ADN.
- **No ionizantes:** luz visible, IR, microondas y radio. No tienen suficiente energía para ionizar.

---

<a id="4-senales-analogicas-y-digitales"></a>
## 4. Señales analógicas y digitales

### 4.1 Señal analógica

Una señal analógica varía en el tiempo de forma continua. Puede tomar infinitos valores dentro de un rango.

Ejemplo: una onda senoidal que representa la voz humana.

### 4.2 Señal digital

Una señal digital solo puede tomar un número finito de valores preestablecidos, normalmente 0 y 1.

Ejemplo: audio comprimido, datos de un archivo o señales lógica de un circuito digital.

### 4.3 Origen de las señales analógicas sobre redes digitales

Para llevar una señal analógica a una red digital se usa un **CODEC** (codificador-decodificador).

- **Ejemplo:** llamada telefónica
  - Teléfono analógico → CODEC → red digital → CODEC → teléfono analógico

### 4.4 Módem

Un **módem** modula y demodula la señal para que pueda viajar por un medio analógico.

- Se usa para transportar datos digitales sobre una portadora analógica.
- Ejemplo: internet por línea telefónica antigua.

### 4.5 Fenómenos que afectan la transmisión

| Fenómeno | ¿Qué es? | Ejemplo |
| :--- | :--- | :--- |
| Atenuación | Pérdida de potencia a medida que la señal recorre el medio | Un cable largo entrega menos nivel de señal |
| Distorsión | Las frecuencias no llegan iguales; la señal se deforma | Voz metálica o señal alterada |
| Ruido | Señales no deseadas que se superponen | Interferencia, ruido térmico |
| Retardo | Tiempo que tarda la señal en llegar | Retraso en una llamada o enlace satelital |
| Capacidad insuficiente | El canal no soporta la cantidad de información que se quiere enviar | Vídeo HD sobre un canal demasiado lento |
| Ancho de banda insuficiente | El canal no tiene rango de frecuencias suficiente | La señal se comprime o se pierde detalle |

> El ancho de banda es el rango de frecuencias que puede transmitir un canal. Cuanto mayor es el ancho de banda, mayor suele ser la capacidad de transmisión.

---

<a id="5-amplificacion-y-regeneracion"></a>
## 5. Amplificación y regeneración

- **Amplificador:** $V_{salida} = G \cdot V_{entrada}$  
  Amplifica la señal, pero también amplifica el ruido. Se usa en redes analógicas.
- **Repetidor regenerativo:**
  - Umbral: $V_1 = 1$, $V_0 = 0$
  - Regenera el pulso limpio y elimina ruido.
  - Se usa principalmente en redes digitales y fibra óptica.
- **Señal sinusoidal:**  
  $v(t) = A \cdot \sin(2\pi f t + \phi)$  
  Ejemplo: $v(t) = 311\sin(2\pi 50 t)$

---

<a id="6-amplitud-frecuencia-y-fase"></a>
## 6. Amplitud, frecuencia y fase

La forma general de una señal sinusoidal es:

$$
v(t) = A \sin(2\pi f t + \phi)
$$

Donde:

- **A:** amplitud, representa la intensidad o nivel de la señal en voltios.
- **f:** frecuencia, indica qué tan rápido varía la señal en Hz.
- **$\phi$:** fase, indica desde dónde comienza la señal, en radianes o grados.

| Parámetro | Analogía con una ola | Unidad |
| :--- | :--- | :--- |
| Amplitud | Altura de la onda | V |
| Frecuencia | Cada cuánto se repite la onda | Hz |
| Fase | Punto de inicio respecto al eje | rad |

---

<a id="7-onda-cuadrada-y-tren-de-pulsos"></a>
## 7. Onda cuadrada y tren de pulsos

- **Onda cuadrada:**  
  $v(t) = +A$ si $0 < t < T/2$, y $v(t) = -A$ si $T/2 < t < T$  
  Tiene un duty cycle del 50% y se usa como reloj digital.
- **Tren de pulsos:**  
  $\tau$ = ancho del pulso, $T$ = periodo, $D = \frac{\tau}{T} \cdot 100$  
  En general $\tau \ll T$, con un duty cycle típico del 1% al 10%. Se usa en radar.
- **Ancho de banda aproximado:**  
  $BW \approx \frac{1}{\tau}$

> Toda onda cuadrada es un tren de pulsos con duty cycle del 50%, pero no todo tren de pulsos es una onda cuadrada.

---

<a id="8-transmision-de-datos-y-valores-de-senal"></a>
## 8. Transmisión de datos y valores de señal

### 8.1 Comunicación serie vs paralela

| Característica | Comunicación serie | Comunicación paralela |
| :--- | :--- | :--- |
| Bits transmitidos | 1 por vez | N por vez |
| Cables necesarios | Pocos | Muchos |
| Costo | Bajo | Alto |
| Distancia | Larga | Corta |
| Complejidad | Mayor en electrónica | Más simple, pero difícil sincronizar |
| Ejemplos | USB, HDMI, Ethernet, Bluetooth, 4G/5G | IDE, LPT, buses antiguos |

**Resumen:** hoy casi toda la transmisión se hace en serie porque es más barata, más confiable y mejor para largas distancias.

### 8.2 Valor eficaz RMS

Es el valor equivalente en continua de una señal alterna: es la tensión que produciría el mismo efecto de potencia o calor que una corriente continua.

$$
V_{RMS} = \frac{V_{pico}}{\sqrt{2}} \approx 0.707 \cdot V_{pico}
$$

Ejemplo: los 220 V de la red eléctrica son RMS, por lo que el valor de pico real es:

$$
V_{pico} = 220 \cdot \sqrt{2} = 311\,V
$$

### 8.3 Valor medio $Y_m$

El valor medio es el promedio de la señal en un periodo completo. Para una senoidal pura, el valor medio total es cero porque la parte positiva y la negativa se cancelan.

Por eso se suele hablar del valor medio rectificado:

$$
Y_m = \frac{2 \cdot V_{pico}}{\pi} \approx 0.637 \cdot V_{pico}
$$

### 8.4 Factor de forma $FF$

El factor de forma mide qué tan distinta es una señal respecto a una onda continua; indica la forma de la onda y su "redondez" o "cuadratura".

$$
FF = \frac{V_{RMS}}{Y_m}
$$

Valores típicos:

- **Senoidal:** $FF = \frac{0.707}{0.637} \approx 1.11$
- **Cuadrada:** $FF = 1$
- **Triangular:** $FF \approx 1.15$

### 8.5 Resumen de fórmulas

$$
\begin{aligned}
V_{RMS} &= \frac{V_{pico}}{\sqrt{2}} \\
Y_m &= \frac{2 \cdot V_{pico}}{\pi} \\
FF &= \frac{V_{RMS}}{Y_m}
\end{aligned}
$$

---

