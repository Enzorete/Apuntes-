# Resumen de Comunicaciones: Electricidad, Magnetismo y Ondas Electromagnéticas

## Índice

- [Clase 2](#clase-2)
- [Clase 3](#clase-3)
- [Clase 4](#clase-4)
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

---

<a id="clase-4"></a>
# Clase 4: Espectro de pulsos, enlaces y espectro electromagnético

## Índice de la Clase 4

- [1. Espectro de pulsos](#1-espectro-de-pulsos)
- [2. Cálculo de enlaces y decibelios](#2-calculo-de-enlaces-y-decibelios)
- [3. Unidades con referencia fija](#3-unidades-con-referencia-fija)
- [4. Balance de potencia](#4-balance-de-potencia)
- [5. Ejercicio resuelto](#5-ejercicio-resuelto)
- [6. Espectro electromagnético](#6-espectro-electromagnetico)

---

<a id="1-espectro-de-pulsos"></a>
## 1. Espectro de pulsos

### 1.1 Parámetros básicos

El ancho del pulso es la inversa de la velocidad de modulación:

$$
\mathit{tau} = V_m^{-1} = \frac{1}{V_m}\quad [s]
$$

El período de repetición es la inversa de la frecuencia de repetición de pulsos:

$$
T = FRP^{-1} = \frac{1}{FRP}\quad [s]
$$

### 1.2 Ancho de banda y armónicas

El ancho de banda aproximado depende del ancho del pulso:

$$
AB = \tau^{-1} = \frac{1}{\tau} = V_m\quad [Hz]
$$

Cuanto más angosto es el pulso, mayor ancho de banda se necesita.

La cantidad aproximada de armónicas dentro del lóbulo principal es:

$$
N_{\text{armónicas}} = \frac{T}{\tau}
$$

Para una amplitud de pulso $A$, la amplitud de cada línea espectral se aproxima mediante:

$$
C_n = A\frac{\tau}{T}
$$

En el caso particular de $A=1\,V$:

$$
C_n = \frac{\tau}{T}\quad [V]
$$

### 1.3 Relación clave

Cuando $A=1$:

$$
C_n\,N_{\text{armónicas}}
= \left(\frac{\tau}{T}\right)\left(\frac{T}{\tau}\right)=1
$$

---

<a id="2-calculo-de-enlaces-y-decibelios"></a>
## 2. Cálculo de enlaces y decibelios

### 2.1 Atenuación y ganancia

La relación lineal entre la potencia de salida y la de entrada es:

$$
R = \frac{P_s}{P_e}
$$

- **Atenuación:** $P_s<P_e$, por lo tanto $0<R<1$.
- **Ganancia:** $P_s>P_e$, por lo tanto $R>1$.

Un atenuador reduce la potencia. Algunos ejemplos son una resistencia, un cable largo o el espacio libre.

### 2.2 Elementos en cascada

Las ganancias y pérdidas lineales se multiplican:

$$
G_{\text{tot}} = \prod_{i=1}^{n}G_i
$$

Por ejemplo:

$$
G_{\text{tot}}=G_1\,G_2\,G_3
$$

Si hay pérdidas y ganancias mezcladas, se aplica la misma regla.

### 2.3 Decibelios

Para potencia, la relación se expresa como:

$$
G_{\text{dB}}=10\log_{10}\left(\frac{P_s}{P_e}\right)
$$

- Si $P_s>P_e$, el resultado es positivo y representa una ganancia.
- Si $P_s<P_e$, el resultado es negativo y representa una pérdida.

En lineal las relaciones se multiplican; en decibelios se suman:

$$
G_{\text{tot,dB}}=\sum_{i=1}^{n}G_{i,\text{dB}}
$$

La conversión inversa es:

$$
P_s=P_e\,10^{G_{\text{dB}}/10}
$$

---

<a id="3-unidades-con-referencia-fija"></a>
## 3. Unidades con referencia fija

Estas unidades comparan una potencia o tensión con un valor de referencia fijo.

### 3.1 dBm

La referencia es $1\,mW$:

$$
P_{\text{dBm}}=10\log_{10}\left(\frac{P[mW]}{1\,mW}\right)
$$

$$
0\,\text{dBm}=1\,mW
$$

### 3.2 dBW

La referencia es $1\,W$:

$$
P_{\text{dBW}}=10\log_{10}\left(\frac{P[W]}{1\,W}\right)
$$

$$
0\,\text{dBW}=1\,W=30\,\text{dBm}
$$

### 3.3 dBu

La referencia de tensión es $0.775\,V_{\text{RMS}}$:

$$
V_{\text{dBu}}=20\log_{10}\left(\frac{V[V]}{0.775\,V}\right)
$$

Ese valor genera $1\,mW$ sobre una resistencia de $600\,\Omega$:

$$
0\,\text{dBu}=0.775\,V_{\text{RMS}}=0\,\text{dBm}=1\,mW
$$

### 3.4 dBmV

La referencia es $1\,mV$ y se utiliza principalmente en televisión y cable coaxial:

$$
V_{\text{dBmV}}=20\log_{10}\left(\frac{V[mV]}{1\,mV}\right)
$$

### 3.5 Regla de oro

- Para **potencia**: $10\log_{10}$.
- Para **tensión**: $20\log_{10}$.

La razón es que $P=V^2/R$:

$$
10\log_{10}\left(\frac{P_s}{P_e}\right)
=10\log_{10}\left[\left(\frac{V_s}{V_e}\right)^2\right]
=20\log_{10}\left(\frac{V_s}{V_e}\right)
$$

### 3.6 Conversión rápida

| Relación lineal | Ganancia o pérdida |
| :---: | :---: |
| $\times 0.001$ | $-30\,\text{dB}$ |
| $\times 0.01$ | $-20\,\text{dB}$ |
| $\times 0.1$ | $-10\,\text{dB}$ |
| $\times 0.5$ | $-3\,\text{dB}$ |
| $\times 1$ | $0\,\text{dB}$ |
| $\times 2$ | $+3\,\text{dB}$ |
| $\times 4$ | $+6\,\text{dB}$ |
| $\times 10$ | $+10\,\text{dB}$ |
| $\times 100$ | $+20\,\text{dB}$ |
| $\times 1000$ | $+30\,\text{dB}$ |

---

<a id="4-balance-de-potencia"></a>
## 4. Balance de potencia

### 4.1 Enlace por cable o fibra

Esquema:

$$
Tx\longrightarrow\text{cable}\longrightarrow Amp
\longrightarrow\text{cable}\longrightarrow Rx
$$

La potencia recibida se calcula en dB como la suma de ganancias menos la suma de pérdidas:

$$
P_{Rx}=P_{Tx}+Amp-
\left(At_{\text{cable}}+At_{\text{empalmes}}+At_{\text{conectores}}+FD\right)
$$

La condición para que el enlace funcione es:

$$
P_{Rx}\geq S_{Rx}
$$

Donde:

$$
\begin{aligned}
At_{\text{cable}}&=\alpha L \\
At_{\text{empalmes}}&=N_{\text{empalmes}}At_{\text{empalme}} \\
At_{\text{conectores}}&=N_{\text{conectores}}At_{\text{conector}}
\end{aligned}
$$

- $P_{Tx}$: potencia transmitida, en dBm.
- $Amp$: ganancia del amplificador, en dB.
- $FD$: factor de diseño o margen de seguridad, normalmente entre $3$ y $6\,dB$.
- $S_{Rx}$: sensibilidad del receptor, en dBm.

Si $P_{Rx}<S_{Rx}$, el enlace no funciona. Las alternativas son aumentar la ganancia, reducir la distancia o agregar un repetidor.

### 4.2 Enlace satelital

Esquema:

$$
\mathrm{Tierra}\xrightarrow{\text{Up-Link}}\text{Satélite}
\xrightarrow{\text{Down-Link}}\text{Tierra}
$$

La ecuación incorpora las ganancias de las antenas y la ganancia del satélite:

$$
P_{Rx}=P_{Tx}+Amp_{\text{sat}}+G_{\text{antenas}}
-\left(At_{\text{atmósfera}}+At_{\text{cables}}+At_{\text{empalmes}}
+At_{\text{conectores}}+FD\right)
$$

La ganancia total de las antenas es:

$$
G_{\text{antenas}}=G_{Tx}+G_{Rx}
$$

Y la condición de enlace sigue siendo:

$$
P_{Rx}\geq S_{Rx}
$$

La atenuación atmosférica incluye el espacio libre, la lluvia y el aire. El satélite actúa como repetidor, mientras que las antenas parabólicas concentran energía y aportan ganancia.

> **Regla general:** todo lo que ayuda menos todo lo que frena debe superar la sensibilidad del receptor.

---

<a id="5-ejercicio-resuelto"></a>
## 5. Ejercicio resuelto: balance de potencia

### 5.1 Enunciado

Un enlace de $1800\,m$ utiliza un coaxial con una atenuación de $0.5\,dB/100\,m$ y transmite $P_{Tx}=2\,W$. ¿Qué sensibilidad máxima, expresada en mW, puede admitir el receptor?

Datos:

$$
L=1800\,m,\qquad \alpha=0.5\,\frac{dB}{100\,m},\qquad P_{Tx}=2\,W
$$

Se consideran nulas las pérdidas de empalmes, conectores y el factor de diseño, y no hay amplificador.

### 5.2 Resolución

**1. Atenuación del cable**

$$
At_{\text{cable}}=1800\,m\left(\frac{0.5\,dB}{100\,m}\right)=9\,dB
$$

**2. Conversión de la potencia transmitida**

$$
P_{Tx}=2\,W=2000\,mW
$$

$$
P_{Tx}=10\log_{10}(2000)=33.01\,dBm
$$

**3. Potencia que llega al receptor**

$$
P_{Rx}=33.01-9=24.01\,dBm
$$

**4. Conversión a mW**

$$
P_{Rx}=10^{24.01/10}=251.7\,mW
$$

Por lo tanto, la sensibilidad debe cumplir:

$$
S_{Rx}\leq251.7\,mW
$$

Por ejemplo, un receptor con sensibilidad de $200\,mW$ funciona; uno de $500\,mW$ no alcanza el nivel recibido.

### 5.3 Atajo sin dBm

Una pérdida de $9\,dB$ equivale a una relación lineal de:

$$
10^{-9/10}=0.1259
$$

Entonces:

$$
P_{Rx}=2\,W\times0.1259=0.2517\,W=251.7\,mW
$$

---

<a id="6-espectro-electromagnetico"></a>
## 6. Espectro electromagnético

### 6.1 Longitud de onda

La longitud de onda es la distancia que avanza una onda durante un período, o la distancia entre dos puntos equivalentes consecutivos.

$$
\lambda=vT=\frac{v}{f}
$$

En el vacío, $v=c$:

$$
c=3\times10^8\,m/s,\qquad \lambda=\frac{c}{f}
$$

Para calcular rápidamente con $f$ en MHz:

$$
\lambda[m]\approx\frac{300}{f[MHz]}
$$

Ejemplos:

$$
\begin{aligned}
100\,MHz&\Rightarrow\lambda=3\,m \\
300\,MHz&\Rightarrow\lambda=1\,m \\
900\,MHz&\Rightarrow\lambda\approx0.33\,m=33\,cm \\
2.4\,GHz&=2400\,MHz\Rightarrow\lambda=12.5\,cm
\end{aligned}
$$

Regla clave:

$$
f\uparrow\Rightarrow\lambda\downarrow\Rightarrow\text{antena más pequeña}
$$

### 6.2 Bandas de frecuencia

| Banda | Abreviatura | Frecuencia | Longitud de onda aproximada |
| :--- | :---: | :--- | :--- |
| Por debajo de ELF | -- | $<3\,Hz$ | $>100000\,km$ |
| Extra baja frecuencia | ELF | $3$--$30\,Hz$ | $100000$--$10000\,km$ |
| Super baja frecuencia | SLF | $30$--$300\,Hz$ | $10000$--$1000\,km$ |
| Ultra baja frecuencia | ULF | $300$--$3000\,Hz$ | $1000$--$100\,km$ |
| Muy baja frecuencia | VLF | $3$--$30\,kHz$ | $100$--$10\,km$ |
| Baja frecuencia | LF | $30$--$300\,kHz$ | $10$--$1\,km$ |
| Media frecuencia | MF | $300$--$3000\,kHz$ | $1\,km$--$100\,m$ |
| Alta frecuencia | HF | $3$--$30\,MHz$ | $100$--$10\,m$ |
| Muy alta frecuencia | VHF | $30$--$300\,MHz$ | $10$--$1\,m$ |
| Ultra alta frecuencia | UHF | $300$--$3000\,MHz$ | $1\,m$--$100\,mm$ |
| Super alta frecuencia | SHF | $3$--$30\,GHz$ | $100$--$10\,mm$ |
| Extra alta frecuencia | EHF | $30$--$300\,GHz$ | $10$--$1\,mm$ |
| Por encima de EHF | -- | $>300\,GHz$ | $<1\,mm$ |

### 6.3 Aplicaciones para recordar

| Banda | Aplicaciones frecuentes |
| :--- | :--- |
| VLF | Comunicaciones con submarinos |
| LF/MF | Radio AM |
| HF | Onda corta y radioaficionados |
| VHF | Radio FM, televisión aérea y aeronáutica |
| UHF | Televisión digital y celulares 4G |
| SHF/EHF | Microondas, WiFi de 5 GHz, satélite y radar |

Como referencia adicional:

| Aplicación o banda de uso | Frecuencia o longitud de onda aproximada |
| :--- | :--- |
| Comunicaciones submarinas | $<30\,kHz$, longitudes de onda mayores a $10\,km$ |
| Radio AM | Alrededor de MF, longitudes de onda menores a $650\,m$ |
| Radio de onda corta | HF, longitudes de onda menores a $180\,m$ |
| Radio FM | VHF, longitudes de onda menores a $10\,m$ |
| Radar y televisión | UHF, longitudes de onda menores a $1\,m$ |
| Microondas | Frecuencias mayores a $1\,GHz$ |
| Luz visible | Aproximadamente $384$--$750\,THz$ |
| Ultravioleta | Frecuencias mayores a aproximadamente $1.5\,PHz$ |
| Rayos X | Frecuencias mayores a aproximadamente $30\,PHz$ |
| Rayos gamma | Frecuencias mayores a aproximadamente $30\,EHz$ |

$$
2.4\,GHz\Rightarrow\lambda=12.5\,cm,\qquad
5\,GHz\Rightarrow\lambda=6\,cm
$$

> **Nota para el parcial:** el apunte del profesor ubica celular, microondas y satélite dentro de “infrarrojo cercano”. Técnicamente, las comunicaciones celulares se encuentran principalmente en UHF/SHF, aproximadamente entre $300\,MHz$ y $30\,GHz$.