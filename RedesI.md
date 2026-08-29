# Resumen de Comunicaciones: Electricidad, Magnetismo y Ondas Electromagnéticas

## Índice

- [Clase 2](#clase-2)
- [Clase 3](#clase-3)

---

<a id="clase-2"></a>
# Clase 2

## Índice de la Clase 2

- [1. Antecedentes históricos y conceptos base](#1-antecedentes-historicos-y-conceptos-base)
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

<a id="clase-3"></a>
# Clase 3: Series de Fourier y señales periódicas

## Índice de la Clase 3

- [1. ¿Por qué importa en telecom?](#1-por-que-importa-en-telecom)
- [2. Condiciones de Dirichlet](#2-condiciones-de-dirichlet)
- [3. Forma trigonométrica de Fourier](#3-forma-trigonometrica-de-fourier)
- [4. Onda cuadrada impar](#4-onda-cuadrada-impar)
- [5. Forma compleja de Fourier](#5-forma-compleja-de-fourier)
- [6. Tiempo vs frecuencia](#6-tiempo-vs-frecuencia)
- [7. Ejercicio resuelto](#7-ejercicio-resuelto)
- [8. Velocidad de modulación y transmisión](#8-velocidad-de-modulacion-y-transmision)
- [9. BER y rendimiento](#9-ber-y-rendimiento)
- [10. Cierre con GeoGebra](#10-cierre-con-geogebra)

---

## 1. ¿Por qué importa en telecom?
La Serie de Fourier es fundamental porque permite estudiar una señal compleja como combinación de senoidales simples. En telecomunicaciones esto sirve para:

- transmisión eficiente
- filtrado de ruido e interferencias
- análisis del ancho de banda
- estudio de modulación y demodulación
- mejora tecnológica y diagnóstico de señales

Idea clave: la dualidad tiempo-frecuencia.
- En el dominio del tiempo se observa la forma de la señal.
- En el dominio de la frecuencia se observan las senoides que la componen.

---

## 2. Condiciones de Dirichlet
Una función $f(t)$ puede desarrollarse en serie de Fourier si cumple:

1. $f(t)$ es periódica, con período $T$
2. está definida salvo en un número finito de puntos
3. tiene un número finito de máximos y mínimos en un período
4. $f(t)$ y $f'(t)$ son continuas por partes

Estas condiciones aseguran que la serie converja en casi todos los puntos.

---

## 3. Forma trigonométrica de Fourier
La forma general es:

$$
f(t)=a_0+
\sum_{n=1}^{\infty}\left[a_n\cos(n\omega_0 t)+b_n\sin(n\omega_0 t)\right]
$$

donde:

$$
\omega_0=\frac{2\pi}{T}=2\pi f_0
$$

y los coeficientes son:

$$
a_0=\frac{1}{T}\int_{-T/2}^{T/2} f(t)\,dt
$$

$$
a_n=\frac{2}{T}\int_{-T/2}^{T/2} f(t)\cos(n\omega_0 t)\,dt
$$

$$
b_n=\frac{2}{T}\int_{-T/2}^{T/2} f(t)\sin(n\omega_0 t)\,dt
$$

### Paridad útil
- Si $f(t)$ es par:
  $$
  \int_{-a}^{a} f(t)\,dt = 2\int_0^a f(t)\,dt
  $$
- Si $f(t)$ es impar:
  $$
  \int_{-a}^{a} f(t)\,dt = 0
  $$

Esto simplifica mucho los cálculos.

---

## 4. Ejemplo: onda cuadrada impar
Una onda cuadrada impar cumple:

$$
f(t)=-f(-t)
$$

Entonces:

$$
a_0=0, \qquad a_n=0
$$

y solo aparecen términos en seno:

$$
f(t)=\sum_{n\text{ impar}} \frac{4}{n\pi}\sin(n\omega_0 t)
$$

Desarrollando:

$$
f(t)\approx \frac{4}{\pi}\sin(\omega_0 t)+\frac{4}{3\pi}\sin(3\omega_0 t)+\frac{4}{5\pi}\sin(5\omega_0 t)+\cdots
$$

Esto muestra que una onda cuadrada está formada por infinitas armónicas impares.

### Fenómeno de Gibbs
En las discontinuidades aparece un sobrepico aproximado del 9%, aunque agreguemos más armónicas. Esto se conoce como fenómeno de Gibbs.

---

## 5. Forma compleja de Fourier
Usando la identidad de Euler,

$$
e^{jt} = \cos t + j\sin t
$$

la señal puede escribirse como

$$
f(t) = \sum_{n=-\infty}^{+\infty} C_n e^{j n \omega_0 t}
$$

donde

$$
C_n = \frac{1}{T}\int_{-T/2}^{T/2} f(t)e^{-j n \omega_0 t}\,dt
$$

Esta forma es muy útil porque expresa la amplitud y la fase de cada componente armónica.

### Tren rectangular
Para un pulso rectangular de amplitud $A$, ancho $\tau$ y período $T$,

$$
|C_n| = A\frac{\tau}{T}
\left|\frac{\sin\left(n\omega_0\tau/2\right)}{n\omega_0\tau/2}\right|
$$

o equivalentemente,

$$
|C_n| = A\frac{\tau}{T}\left|\operatorname{sinc}\left(\frac{n\omega_0\tau}{2}\right)\right|
$$

con

$$
\operatorname{sinc}(x)=\frac{\sin x}{x}
$$

### Fórmulas útiles
- Número de armónicas relevantes:

  $$
  N = \frac{T}{\tau}
  $$

- Amplitud máxima del espectro:

  $$
  |C_0| = A\frac{\tau}{T}
  $$

Si $\tau$ es pequeño, el espectro es ancho; si $\tau$ es grande, el espectro es más estrecho.

---

## 6. Tiempo vs frecuencia
- En el tiempo: vemos pulsos, forma de onda, amplitud versus $t$
- En la frecuencia: vemos rayas o componentes armónicas separadas por $f_0$
- El espectro de un tren de pulsos tiene una envolvente sinc

La separación entre líneas del espectro es:

$$
\Delta f = f_0 = \frac{1}{T}
$$

Esto es clave en telecomunicaciones porque determina el ancho de banda y la capacidad de transmisión.

---

## 7. Ejercicio resuelto (pág. 22)
Datos:
- $FRP=1000\ \text{pps}$
- $T=\frac{1}{1000}=0.001\ \text{s}$
- $V_m=2000\ \text{baudios}$
- $\tau=\frac{1}{V_m}=0.5\times10^{-4}\ \text{s}$
- $A=1\ \text{V}$

### 1) Período
$$
T=0.001\ \text{s}
$$

### 2) Duración del pulso
$$
\tau=0.5\times10^{-4}\ \text{s}
$$

### 3) Número de armónicas
$$
N=\frac{T}{\tau}=\frac{0.001}{0.5\times10^{-4}}=20
$$

### 4) Frecuencia fundamental
$$
f_0=\frac{1}{T}=\frac{1}{0.001}=1000\ \text{Hz}
$$

### 5) Ancho de banda
$$
BW\approx N\cdot f_0 = 20\cdot1000 = 20000\ \text{Hz}=20\ \text{kHz}
$$

### 6) Amplitud máxima
$$
|C_0|=A\frac{\tau}{T}=1\cdot\frac{0.5\times10^{-4}}{0.001}=0.05\ \text{V}
$$

Conclusión: el espectro es sinc y el primer cero aparece en la armónica 20.

---

## 8. Velocidad de modulación y transmisión
La velocidad de símbolos es:

$$
V_m=\frac{\text{número de cambios}}{\text{tiempo}}\quad [\text{baudios}]
$$

La velocidad de transmisión en bits es:

$$
V_t=\frac{1}{\tau}\log_2(n)\quad [\text{bps}]
$$

donde $n$ es el número de niveles.

### Importante
- más niveles $\Rightarrow$ más bits por cambio
- mayor eficiencia espectral
- pero también mayor complejidad y sensibilidad al ruido

---

## 9. BER y rendimiento
### BER
$$
BER=\frac{\text{bits con errores}}{\text{bits transmitidos}}
$$

Valores típicos:
- muy bueno: $10^{-9}$ a $10^{-10}$
- bueno: $10^{-6}$
- degradado: $10^{-3}$ a $10^{-5}$
- dañado: $>10^{-3}$

### Rendimiento
$$
\text{Rendimiento}=\frac{\text{bits útiles}}{\text{bits totales}}
$$

---

## 10. Cierre con GeoGebra
Una señal sinusoidal general es:

$$
f(t)=A\sin(\omega t+\phi)
$$

donde:
- $A$ = amplitud
- $\omega$ = frecuencia angular
- $\phi$ = fase

En Fourier:
- $A$ representa la amplitud del armónico $|C_n|$
- $\omega=n\omega_0$
- $\phi$ representa la fase del coeficiente complejo

### Interpretación visual
- aumentar $A$ → estiramiento vertical
- aumentar $\omega$ → más ciclos por unidad de tiempo
- aumentar $\phi$ → desplazamiento horizontal (adelanto o retraso)

---

## Resumen final
- La serie de Fourier descompone una señal periódica en armónicas.
- La frecuencia fundamental es

  $$
  f_0 = \frac{1}{T}
  $$

- La forma trigonométrica es

  $$
  f(t) = a_0 + \sum_{n=1}^{\infty}\left[a_n\cos(n\omega_0 t)+b_n\sin(n\omega_0 t)\right]
  $$

- La forma compleja es

  $$
  f(t) = \sum_{n=-\infty}^{+\infty} C_n e^{j n \omega_0 t}
  $$

- Un tren rectangular tiene un espectro con envolvente sinc.
- El ancho de banda depende del ancho del pulso $\tau$ y del período $T$.
- Este análisis es fundamental para la transmisión, el filtrado y el diagnóstico en telecomunicaciones.

