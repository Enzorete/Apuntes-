---
title: "POO2 - Apuntes de Cátedra"
subtitle: "UML, Complejidad, Estructuras de Datos y Algoritmos de Grafos"
author: "Apuntes compilados"
date: "2026-06-10"
lang: "es-AR"
---

# POO2 - Programación Orientada a Objetos 2

> Apuntes completos para primer y segundo parcial: modelado, complejidad, estructuras de datos y algoritmos.

## Tabla de Contenidos

- [Parte 1: Conceptos Fundamentales](#parte-1-conceptos-fundamentales)
- [Parte 2: Complejidad Computacional](#parte-2-complejidad-computacional)
- [Parte 3: Algoritmos de Ordenamiento](#parte-3-algoritmos-de-ordenamiento)
- [Parte 4: Árboles](#parte-4-árboles)
- [Parte 5: Colas de Prioridad y Montículos](#parte-5-colas-de-prioridad-y-montículos)
- [Parte 6: Grafos](#parte-6-grafos)
- [Parte 7: Algoritmos de Grafos](#parte-7-algoritmos-de-grafos)
- [Parte 8: Árbol Recubridor Mínimo](#parte-8-árbol-recubridor-mínimo)

---

# PARTE 1: CONCEPTOS FUNDAMENTALES

## 1. UML (Lenguaje de Modelado Unificado)

UML es un lenguaje estándar para visualizar el diseño de sistemas orientados a objetos.

---

## 2. Diagrama de Clases

Vista general que muestra las clases, atributos, métodos y relaciones.

### Componentes

| Componente | Descripción |
|-----------|-------------|
| **Nombre** | Identifica la clase |
| **Atributos** | Propiedades o campos. Se escriben como texto, sin tipo obligatorio en diagramas conceptuales |
| **Métodos** | Acciones que la clase puede realizar |
| **Responsabilidades** | Contrato informal, qué debe garantizar la clase |

---

## 3. Relaciones entre Clases

Tres relaciones fundamentales en diseño orientado a objetos:

### Dependencia

**Uso temporal.** Una clase utiliza otra de forma transitoria.

- Ejemplo: Un método recibe otra clase como parámetro
- La relación termina al finalizar el método

### Generalización (Herencia)

**Relación "es un"** entre clase padre e hijo.

- Clase hija hereda atributos y métodos
- Especializa el comportamiento
- La hija es más específica que la padre

### Asociación

**Conexión estructural** entre clases.

#### Agregación

- **"tiene un"** con vida independiente
- Los objetos pueden existir por separado
- Ejemplo: Universidad tiene Departamentos
- Los departamentos existen sin la universidad

#### Composición

- **"parte de"** con vida dependiente
- Los objetos no pueden existir separados
- Ejemplo: Casa tiene Habitaciones
- Las habitaciones no existen sin la casa

---

# PARTE 2: COMPLEJIDAD COMPUTACIONAL

## 1. Concepto

Relación entre el **tamaño de entrada N** y el **tiempo de ejecución T**.

Nos permite analizar qué algoritmo elegir y predecir rendimiento a escala.

---

## 2. Notaciones Principales

| Notación | Nombre | Crecimiento | Ejemplo Típico |
|----------|--------|-----------|----------------|
| `O(1)` | Constante | No depende de N | Acceso por índice en array |
| `O(log n)` | Logarítmica | Divide el problema | Búsqueda binaria |
| `O(n)` | Lineal | Proporcional a N | Recorrer lista |
| `O(n log n)` | Lineal-logarítmica | Divida y conquiste | Mergesort, Quicksort |
| `O(n²)` | Cuadrática | Dos bucles anidados | Bubble Sort, Insertion Sort |
| `O(n³)` | Cúbica | Tres bucles anidados | Multiplicación de matrices naive |
| `O(2ⁿ)` | Exponencial | Explota rápido | Fuerza bruta |
| `O(n!)` | Factorial | Peor explosión | Permutaciones |

### Regla Fundamental

**A mayor N, mayor T.** La pendiente de crecimiento la define la notación.

---

# PARTE 3: ALGORITMOS DE ORDENAMIENTO

## 1. Conceptos Clave

### Registro

Conjunto de datos que se ordena.

- Ejemplo: objeto Alumno

### Clave

Valor específico por el cual se ordena.

- Ejemplo: propiedad nota del alumno

### Estabilidad

Algoritmo es estable si **mantiene el orden relativo** entre elementos con claves iguales.

**Ejemplo:**
- Entrada: [(Ana, 8), (Bob, 8), (Carlos, 9)]
- Si ambos tienen 8, Ana debe quedar antes de Bob en salida

### Sensibilidad

El rendimiento depende del **orden inicial** de los datos.

- Sensible: rendimiento varía según si ya está parcialmente ordenado
- No sensible: siempre el mismo tiempo

---

## 2. Algoritmos Elementales

### Selection Sort (Ordenamiento por Selección)

**Idea:** Buscar el mínimo y colocarlo en posición.

**Proceso:**
1. Busca el elemento mínimo
2. Lo coloca en la primera posición
3. Repite para el resto

**Características:**
- **Estabilidad:** No es estable
- **Sensibilidad:** No es sensible
- **Complejidad:** O(n²)

---

### Bubble Sort (Ordenamiento por Burbujeo)

**Idea:** Intercambiar elementos adyacentes si están en orden incorrecto.

**Proceso:**
1. Compara pares adyacentes
2. Intercambia si es necesario
3. Repite hasta que no hay intercambios

**Características:**
- **Estabilidad:** Sí es estable
- **Sensibilidad:** Sí es sensible (funciona bien con datos casi ordenados)
- **Complejidad:** O(n²)

---

### Insertion Sort (Ordenamiento por Inserción)

**Idea:** Insertar cada elemento en su posición correcta.

**Proceso:**
1. Toma un elemento
2. Lo inserta en la posición correcta entre los ya ordenados
3. Repite para todos

**Características:**
- **Estabilidad:** Sí es estable
- **Sensibilidad:** Sí es sensible
- **Complejidad:** O(n²)
- **Nota:** Suele rendir mejor en datos casi ordenados

---

## 3. Comparación Práctica

| Algoritmo | Mejor en | Casos de Uso |
|-----------|----------|-------------|
| Selection | Ninguno particular | Casos educacionales |
| Bubble | Datos casi ordenados | Detección de orden |
| Insertion | Datos parcialmente ordenados | Conjuntos pequeños, inserción en línea |

### Conclusión

- Los tres tienen complejidad **O(n²)**
- **Insertion** suele rendir mejor en datos casi ordenados
- Si hay claves repetidas y importa el orden original, elegir uno **estable**

---

# PARTE 4: ÁRBOLES

## 1. Definición

Un árbol es una estructura **dinámica, jerárquica y no lineal** que organiza datos.

---

## 2. Elementos Fundamentales

| Elemento | Definición |
|----------|-----------|
| **Nodo** | Elemento que almacena un dato |
| **Raíz** | Primer nodo, sin padre (nivel 0) |
| **Padre** | Nodo que precede a otro |
| **Hijo** | Nodo que sucede a otro |
| **Hoja** | Nodo sin hijos (terminal) |
| **Rama** | Camino entre nodos |
| **Nivel/Profundidad** | Cantidad de aristas desde raíz |
| **Altura** | Máximo nivel del árbol |
| **Árbol vacío** | Sin nodos |

---

## 3. Árbol Binario

Un árbol donde **cada nodo tiene máximo dos hijos**: izquierdo y derecho.

### Propiedades

- Máximo 1 nodo en nivel 0 (raíz)
- Máximo 2 nodos en nivel 1
- Máximo 2^k nodos en nivel k
- Máximo 2^(h+1) - 1 nodos en árbol de altura h

---

## 4. Árbol Binario de Búsqueda (BST)

Un árbol binario con propiedad especial:

**Propiedad BST:**
```
Para cada nodo:
├─ Izquierda: todos < raíz
├─ Raíz: el valor actual
└─ Derecha: todos > raíz
```

### Ventajas

- Permite búsqueda eficiente
- Inserción y eliminación ordenadas

### Desventajas si no está balanceado

Puede degenerar en lista enlazada, perdiendo eficiencia.

---

## 5. Recorridos (Clave de Examen)

Formas de visitar todos los nodos del árbol.

### Preorden

**Orden:** Raíz → Izquierda → Derecha

**Uso:** Copiar árbol, pre-procesamiento

```
        1
       / \
      2   3

Resultado: 1, 2, 3
```

---

### Inorden

**Orden:** Izquierda → Raíz → Derecha

**Propiedad especial:** En un **BST, devuelve valores en orden ascendente**

```
        2
       / \
      1   3

Resultado: 1, 2, 3 (ordenado)
```

---

### Postorden

**Orden:** Izquierda → Derecha → Raíz

**Uso:** Eliminación de árbol, post-procesamiento

```
        3
       / \
      1   2

Resultado: 1, 2, 3
```

---

## 6. Complejidad de Operaciones

### Recorrido

- **Complejidad:** O(n)
- Visita cada nodo exactamente una vez

### Búsqueda en BST

| Caso | Complejidad |
|------|-------------|
| Balanceado | O(log n) |
| Desbalanceado (lista) | O(n) |

---

## 7. Claves para el Examen

- ✓ Identificar raíz, hoja, padre, hijo sin dudar
- ✓ Preorden empieza con raíz, inorden la pone en el medio, postorden al final
- ✓ Inorden en BST = orden ascendente
- ✓ No confundir subárbol izquierdo con derecho
- ✓ Recordar fórmula de máximo nodos: 2^(h+1) - 1

---

# PARTE 5: COLAS DE PRIORIDAD Y MONTÍCULOS

## 1. Tipos de Datos Abstractos (TDA)

### Definición

Un TDA especifica **QUÉ operaciones se pueden hacer**, no **CÓMO se implementan**.

La interfaz es un **contrato** entre usuario y implementación.

### Ventajas

- **Encapsulamiento:** Detalles internos ocultos
- **Flexibilidad:** Cambiar implementación sin afectar usuario
- **Reutilización:** Código cliente reutilizable

---

## 2. Cola de Prioridad

### Definición

Estructura donde cada elemento tiene una **prioridad asociada**.

**Siempre se extrae** el elemento de mayor prioridad (max) o menor (min).

### Diferencia con Cola FIFO

- **Cola normal (FIFO):** Orden de salida = orden de entrada
- **Cola de prioridad:** Orden de salida = prioridad, no importa entrada

---

## 3. Operaciones Principales

| Operación | Descripción | Ideal |
|-----------|-------------|-------|
| `crear()` | Inicializa cola vacía | O(1) |
| `insertar(x, p)` | Agrega elemento con prioridad | O(log n) |
| `extraer()` | Saca y devuelve mejor prioridad | O(log n) |
| `consultar()` | Peek sin sacar (solo ver) | O(1) |
| `estaVacia()` | Verifica si está vacía | O(1) |
| `tamaño()` | Devuelve cantidad | O(1) |

---

## 4. Comparación de Implementaciones

| Implementación | Insertar | Extraer | Consultar | Memoria |
|---|---|---|---|---|
| Lista ordenada | O(n) | O(1) | O(1) | O(n) |
| Lista desordenada | O(1) | O(n) | O(n) | O(n) |
| Árbol BST balanceado | O(log n) | O(log n) | O(log n) | O(n) |
| **Montículo binario** | **O(log n)** | **O(log n)** | **O(1)** | **O(n)** |

**Recomendación:** Montículo binario es la mejor opción general.

---

## 5. Aplicaciones Reales

- Planificador de CPU (procesos con prioridad)
- Algoritmo de Dijkstra (distancias mínimas)
- Compresión Huffman (construcción de árbol)
- Simulación de eventos discretos
- A* en videojuegos (búsqueda heurística)

---

## 6. Montículos (Heaps)

### Propiedades Fundamentales

**1. Árbol binario completo**

- Todos los niveles completamente llenos
- Excepto quizás el último nivel
- Último nivel se llena de **izquierda a derecha**

**2. Propiedad de Heap**

- **Min-heap:** padre ≤ hijos
- **Max-heap:** padre ≥ hijos

### Importante

No está ordenado totalmente, solo **garantiza el extremo en la raíz**.

---

## 7. Representación con Array

Se evita usar punteros. Con **índice base 0:**

```
padre(i) = (i - 1) // 2
hijo_izquierdo(i) = 2*i + 1
hijo_derecho(i) = 2*i + 2
```

### Ejemplo Min-Heap

```
Array: [5, 7, 9, 15, 18, 20, 14]

Árbol:
        5
       / \
      7   9
     /|  / \
   15 18 20 14
```

---

## 8. Operaciones de Montículo

### Insertar(x)

1. Poner x al final del array
2. **Flotar:** Mientras x < padre, intercambiar con padre
3. Repetir hasta cumplir propiedad

**Complejidad:** O(log n)

---

### ExtraerMin()

1. Guardar valor de raíz
2. Mover último elemento a raíz
3. **Hundir:** Intercambiar con hijo menor hasta cumplir propiedad
4. Repetir hasta que cumple

**Complejidad:** O(log n)

---

### Construir Montículo desde Array

**Método ingenuo:**
- Insertar todos → O(n log n)

**Método óptimo (Floyd):**
- Hundir desde n/2 hacia 0 → O(n)

---

## 9. Variantes de Montículos

| Variante | Característica | Uso |
|----------|---|---|
| **d-ario** | d hijos por nodo, reduce altura | Cuando acceso costoso |
| **Binomial** | Unión en O(log n) | Operaciones de fusión |
| **Fibonacci** | Decrementar clave O(1) amortizado | Dijkstra teórico |

---

# PARTE 6: GRAFOS

## 1. Definición Formal

```
G = (V, E)

donde:
- V = conjunto de vértices
- E ⊆ V × V = conjunto de aristas
```

Un grafo es una estructura que conecta elementos llamados vértices mediante aristas.

---

## 2. Terminología Fundamental

| Término | Definición |
|---------|-----------|
| **Adyacencia** | u y v son adyacentes si existe arista (u,v) |
| **Incidencia** | Una arista incide en sus dos extremos |
| **Camino** | Secuencia v₀,v₁,...,vₖ con aristas entre consecutivos |
| **Camino simple** | Camino sin vértices repetidos |
| **Ciclo** | Camino que empieza y termina en el mismo vértice |
| **Distancia** | Longitud del camino más corto entre dos vértices |

---

## 3. Tipos de Grafos

| Tipo | Descripción |
|------|-------------|
| **No dirigido** | Arista {u,v} = {v,u}, conexión bidireccional |
| **Dirigido (digrafo)** | Arista (u,v) ≠ (v,u), direccionada |
| **Ponderado** | Cada arista tiene peso w: E → ℝ |
| **Simple** | Sin lazos (u,u) ni aristas múltiples |
| **Completo Kₙ** | n vértices, todas las aristas posibles, \|E\| = n(n-1)/2 |
| **Bipartito** | V = A ∪ B, aristas solo entre A y B |
| **Conexo** | Existe camino entre todo par (no dirigido) |
| **Fuertemente conexo** | En dirigido, camino en ambos sentidos entre todo par |
| **Árbol** | Grafo conexo sin ciclos, \|E\| = \|V\|-1 |
| **DAG** | Grafo Dirigido Acíclico |

---

## 4. Grados en Grafos

### Grafo No Dirigido

```
grado(v) = número de aristas incidentes en v
```

### Grafo Dirigido

```
grado(v) = grado_entrada + grado_salida
```

### Handshaking Lemma

```
Suma de todos los grados = 2|E|
```

---

## 5. Representaciones

### Matriz de Adyacencia

```
M[i][j] = peso si existe arista (i,j), 0 o ∞ si no
```

**Características:**
- **Espacio:** O(V²)
- **Consultar arista:** O(1)
- **Recorrer vecinos:** O(V)
- **Ideal para:** Grafos densos

---

### Lista de Adyacencia

```
Array de listas, cada posición i contiene lista de vecinos de i
```

**Características:**
- **Espacio:** O(V+E)
- **Consultar arista:** O(grado)
- **Recorrer vecinos:** O(grado)
- **Ideal para:** Grafos dispersos

---

## 6. Algoritmos Fundamentales

| Algoritmo | Propósito | Complejidad |
|-----------|----------|-------------|
| **BFS** | Recorrido por niveles, caminos mínimos en no ponderado | O(V+E) |
| **DFS** | Profundidad, ciclos, orden topológico | O(V+E) |
| **Dijkstra** | Caminos mínimos con pesos ≥ 0 | O((V+E)log V) |
| **Bellman-Ford** | Caminos mínimos, permite pesos negativos | O(VE) |
| **Kruskal/Prim** | Árbol de expansión mínima | O(E log E) / O(E log V) |

---

## 7. Ejercicio de Implementación

Crear clases para un grafo:

**Clases necesarias:**
- `Vertice`: almacena identificador y datos
- `Arista`: almacena origen, destino, peso
- `Grafo`: contenedor, operaciones

**Métodos:**
```
- agregarVertice(id)
- agregarArista(origen, destino, peso)  // verificar duplicados
- obtenerAdyacentes(v)
```

**Implementaciones:**
- MatrizAdyacencia
- ListaAdyacencia

---

# PARTE 7: ALGORITMOS DE GRAFOS

## 1. Algoritmo de Dijkstra

### Objetivo

Dado un vértice **origen**, encontrar el camino de **menor costo** hacia todos los demás vértices.

---

### Condiciones de Aplicabilidad

- Grafo dirigido o no dirigido
- **Todos los pesos > 0** (no funciona con negativos)
- Grafo debe ser conexo desde el origen

---

### Idea Clave

Mantener distancias tentativas a cada vértice.

**Estrategia voraz:**
- Siempre expandir el vértice no visitado con menor distancia actual
- Una vez visitado, su distancia es definitiva (nunca mejora)

---

### Pseudocódigo

```
Dijkstra(G, origen):
  dist[v] = ∞ para todo vértice v
  dist[origen] = 0
  previo[v] = NULO para todo v
  Q = cola de prioridad con (0, origen)

  mientras Q no esté vacía:
    u = extraerMin(Q)  // mínima distancia
    
    para cada vecino v de u:
      si dist[v] > dist[u] + peso(u,v):
        dist[v] = dist[u] + peso(u,v)
        previo[v] = u
        insertar(Q, dist[v], v)
```

---

### Ejemplo Paso a Paso

**Vértices:** A, B, C, D, E, F, G

**Proceso (origen A):**

1. **Inicial:** dist[A]=0, resto ∞

2. **Visita B (dist=5):** 
   - Actualiza C=9, E=13

3. **Visita C (dist=9):** 
   - Actualiza D=12, F=31, G=17

4. **Visita D (dist=12):** 
   - Actualiza F=23

5. **Visita E (dist=13):** 
   - Sin mejoras

6. **Visita G (dist=17):** 
   - Sin mejoras

7. **Visita F (dist=23):** 
   - Fin

**Resultado final:**
```
A=0, B=5, C=9, D=12, E=13, F=23, G=17
```

---

### Complejidad

| Implementación | Complejidad |
|---|---|
| Con array | O(V²) |
| Con heap binario | O((V+E) log V) |
| Con Fibonacci heap | O(E + V log V) |

---

### Limitaciones y Variantes

**Problemas:**
- No sirve con pesos negativos
- Solución: usar **Bellman-Ford**

**Variantes:**
- **A*:** Agrega heurística para búsqueda dirigida
- **Dijkstra bidireccional:** Para origen-destino específico

---

## 2. Coloreo de Grafos

### Definición

Asignar un color a cada vértice tal que **vértices adyacentes tengan colores distintos**.

---

### Número Cromático χ(G)

Mínimo número de colores necesarios.

**Ejemplos:**

| Tipo de Grafo | χ(G) |
|---|---|
| Bipartito | 2 |
| Ciclo par | 2 |
| Ciclo impar | 3 |
| Completo Kₙ | n |
| Árbol | 2 |

---

### Aplicaciones Prácticas

- Asignación de frecuencias (celulares, WiFi)
- Horarios de exámenes (materias sin conflictos)
- Registros en compiladores
- Sudoku
- Mapas geográficos

---

### Complejidad

**Encontrar χ(G) es NP-completo.**

No hay algoritmo polinomial conocido para el óptimo.

---

### Algoritmos Heurísticos

#### Secuencial (Greedy Simple)

1. Ordenar vértices (cualquier orden)
2. Para cada vértice: asignar el menor color no usado por vecinos

**Complejidad:** O(V+E)

**Nota:** Resultado depende del orden. Puede no ser óptimo.

---

#### Welsh-Powell

1. Ordenar vértices por **grado decreciente**
2. Aplicar greedy

**Ventaja:** Suele mejorar el resultado

---

#### Matula (Smallest Last)

1. Ordenar vértices por **grado creciente**
2. Aplicar greedy

**Ventaja:** Otro enfoque que suele funcionar bien

---

#### DSATUR

Elige el vértice con **mayor saturación** (colores distintos en vecinos).

**Ventaja:** Muy efectivo en la práctica

---

### Cotas Teóricas

```
χ(G) ≤ Δ + 1       donde Δ = grado máximo

χ(G) ≥ ω(G)        donde ω = tamaño de clique máxima

Teorema de Brooks: χ(G) ≤ Δ
                   (excepto grafos completos y ciclos impares)
```

---

# PARTE 8: ÁRBOL RECUBRIDOR MÍNIMO

## 1. Definición

**Árbol Recubridor (Spanning Tree):** Árbol que conecta todos los vértices de un grafo conexo, usando aristas del grafo.

**Árbol Recubridor Mínimo (MST/ARM):** Árbol recubridor donde la **suma de pesos es mínima**.

### Propiedades

- Número de aristas = V - 1
- Puede haber múltiples ARM con mismo peso total
- Aplicable a grafos no dirigidos

---

## 2. Algoritmo de Kruskal

### Estrategia

Enfoque **greedy** basado en aristas.

### Pseudocódigo

```
Kruskal(G):
  Ordenar todas las aristas por peso (ascendente)
  
  ARM = conjunto vacío
  
  para cada arista (u,v) ordenadas por peso:
    si agregar (u,v) NO forma ciclo:
      agregar (u,v) a ARM
  
  devolver ARM
```

---

### Proceso Paso a Paso

1. Ordenar aristas por peso ascendente
2. Tomar la menor arista
3. Verificar si forma ciclo (usar Union-Find)
4. Si NO forma ciclo → agregar a ARM
5. Repetir hasta tener V-1 aristas

---

### Detección de Ciclos

Usar estructura **Union-Find**:

- `Find(v)`: encuentra el componente de v
- `Union(u,v)`: une componentes de u y v

Si u y v están en mismo componente → formaría ciclo

---

### Complejidad

```
O(E log E)

Dominado por el ordenamiento de aristas.
Con Union-Find optimizado: casi O(E α(E,V)) donde α es inversa de Ackermann
```

---

## 3. Algoritmo de Prim

### Estrategia

Enfoque **greedy** basado en vértices.

### Pseudocódigo

```
Prim(G, inicio):
  ARM = conjunto vacío
  visitados = {inicio}
  aristas_candidatas = aristas adyacentes a inicio
  
  mientras ARM tenga < V-1 aristas:
    arista = mínima de aristas_candidatas
    (u, v) = arista
    
    si v NO está visitado:
      agregar (u,v) a ARM
      visitados.agregar(v)
      agregar aristas de v a candidatas
```

---

### Proceso Paso a Paso

1. Empezar en un vértice cualquiera
2. Tomar la arista de **menor peso que conecte**:
   - Un vértice ya en ARM
   - Con un vértice fuera de ARM
3. Agregar esa arista y el nuevo vértice
4. Repetir hasta cubrir todos

---

### Complejidad

| Implementación | Complejidad |
|---|---|
| Array simple | O(V²) |
| Con heap binario | O(E log V) |
| Con Fibonacci heap | O(E + V log V) |

**Ideal para:** Grafos densos

---

## 4. Ejemplo Comparativo: Kruskal vs Prim

### Grafo Ejemplo

**Vértices:** A, B, C, D, E, F, G, H, I, J (10 vértices)

**Aristas ordenadas por peso:**

```
E-B (3)    B-A (11)   F-J (30)
J-G (7)    D-H (15)   C-G (32)
H-I (8)    I-F (19)   
E-I (9)    F-C (25)
I-J (9)
D-E (10)
```

---

### Kruskal Paso a Paso

| Paso | Arista | Acción | Razón |
|------|--------|--------|-------|
| 1 | E-B (3) | Toma | Primera |
| 2 | J-G (7) | Toma | Diferentes componentes |
| 3 | H-I (8) | Toma | Diferentes componentes |
| 4 | E-I (9) | Toma | Diferentes componentes |
| 5 | I-J (9) | Toma | Une componentes E y G |
| 6 | D-E (10) | Toma | Agrega nuevo vértice |
| 7 | B-A (11) | Toma | Agrega A |
| 8 | D-H (15) | **Rechaza** | **Formaría ciclo** |
| 9 | I-F (19) | Toma | Agrega F |
| 10 | F-C (25) | Toma | Completa (9 aristas) |

**Peso total:** 3+7+8+9+9+10+11+19+25 = **101**

---

### Prim Paso a Paso (Comenzando en E)

| Orden | Arista | Descripción |
|------|--------|-------------|
| 1 | E-B (3) | Conecta E con B |
| 2 | E-I (9) | Conecta E con I |
| 3 | I-H (8) | Conecta I con H |
| 4 | I-J (9) | Conecta I con J |
| 5 | J-G (7) | Conecta J con G |
| 6 | E-D (10) | Conecta E con D |
| 7 | B-A (11) | Conecta B con A |
| 8 | I-F (19) | Conecta I con F |
| 9 | F-C (25) | Conecta F con C |

**Peso total:** 3+7+8+9+9+10+11+19+25 = **101** (mismo)

---

### Comparación

| Aspecto | Kruskal | Prim |
|--------|---------|------|
| Enfoque | Aristas | Vértices |
| Ordenamiento | Previo | Durante |
| Mejor para | Grafos dispersos | Grafos densos |
| Implementación | Union-Find | Heap |
| Orden de aristas | Diferente | Diferente |

---

## 5. Conclusiones

- **Ambos algoritmos producen MST correcto**
- **Mismo peso total** pero diferente conjunto de aristas (en general)
- **Elegir según contexto:**
  - Grafo disperso → Kruskal
  - Grafo denso → Prim
  - Ya ordenado → Kruskal
  - Acceso dinámico → Prim

---

# Fin del Documento

Apuntes completos de POO2 cubriendo modelado, complejidad, estructuras de datos fundamentales y algoritmos de grafos para ambos parciales.

**Última actualización:** 2026-06-10
