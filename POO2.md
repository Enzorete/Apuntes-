# POO2 - Apunte 1er Parcial

> Resumen compacto de UML, complejidad, ordenamiento y árboles. Pensado para repasar rápido antes del parcial.

## Índice

1. [UML](#uml-lenguaje-de-modelado-unificado)
2. [Complejidad Computacional](#complejidad-computacional)
3. [Métodos de Ordenamiento](#métodos-de-ordenamiento-elementales)
4. [Árboles](#árboles-estructura-de-datos)

---

## UML (Lenguaje de Modelado Unificado)

### Diagrama de clases

Vista general de las clases y sus relaciones.

- **Nombre**: identifica a la clase.
- **Atributos**: propiedades. Se escriben como texto, sin tipo obligatorio en el diagrama conceptual.
- **Métodos**: acciones que la clase puede realizar.
- **Responsabilidades**: contrato informal, qué debe garantizar la clase.

### Relaciones entre clases

Tres relaciones base en diseño orientado a objetos:

1. **Dependencia**: uso temporal. Ej: un método recibe otra clase como parámetro.
2. **Generalización (herencia)**: clase hija hereda de padre. Relación "es un".
3. **Asociación**: conexión estructural.
   - **Agregación**: "tiene un", vida independiente.
   - **Composición**: "parte de", vida dependiente.

---

## Complejidad Computacional

Relación entre tamaño de entrada `N` y tiempo `T`.

| Notación          | Nombre                  | Crecimiento          | Ejemplo típico                   |
| :---------------- | :---------------------- | :------------------- | :------------------------------- |
| `O(1)`            | Constante               | No depende de N      | Acceso por índice en array       |
| `O(log n)`        | Logarítmica             | Divide el problema   | Búsqueda binaria                 |
| `O(n)`            | Lineal                  | Proporcional a N     | Recorrer lista                   |
| `O(n²)`           | Cuadrática              | Dos bucles anidados  | Bubble Sort, Insertion Sort      |
| `O(n³)`           | Cúbica                  | Tres bucles anidados | Multiplicación de matrices naive |
| `O(2ⁿ)` / `O(n!)` | Exponencial / Factorial | Explota rápido       | Fuerza bruta, permutaciones      |

> A mayor N, mayor T. La pendiente la define la notación.

---

## Métodos de Ordenamiento Elementales

**Conceptos clave**

- **Registro**: conjunto de datos (ej: alumno).
- **Clave**: valor por el cual se ordena (ej: nota).
- **Estabilidad**: mantiene orden relativo con claves iguales.
- **Sensibilidad**: rendimiento depende del orden inicial.

| Algoritmo     | Idea central                 | Estable | Sensible | Complejidad |
| :------------ | :--------------------------- | :-----: | :------: | :---------: |
| **Selección** | Busca el mínimo y lo coloca  |   No    |    No    |   `O(n²)`   |
| **Burbujeo**  | Intercambia adyacentes       |   Sí    |    Sí    |   `O(n²)`   |
| **Inserción** | Inserta en posición correcta |   Sí    |    Sí    |   `O(n²)`   |

**Conclusión práctica**: los tres son `O(n²)`. Inserción suele rendir mejor en datos casi ordenados. Si hay claves repetidas y te importa el orden original, elegí uno estable.

---

## Árboles (Estructura de Datos)

Estructura **dinámica**, **jerárquica** y **no lineal**.

### Elementos

- **Nodo**: elemento.
- **Raíz**: primer nodo, nivel 0.
- **Padre / Hijo**: relación directa.
- **Hoja**: sin hijos.
- **Rama**: camino entre nodos.
- **Nivel / Profundidad**: cantidad de aristas desde la raíz.
- **Árbol vacío**: sin nodos.

### Árbol binario

Cada nodo tiene máximo dos hijos: izquierdo y derecho.

### Árbol Binario de Búsqueda (BST)

Propiedad: **izq < raíz < der**

- Izquierda: menores.
- Derecha: mayores.
- Permite búsqueda eficiente si está balanceado.

### Recorridos (clave de parcial)

- **Preorden**: Raíz → Izq → Der
- **Inorden**: Izq → Raíz → Der → en BST devuelve ordenado
- **Postorden**: Izq → Der → Raíz

### Complejidad

- Recorrer: `O(n)`
- Buscar en BST:
  - Balanceado: `O(log n)`
  - Desbalanceado (lista): `O(n)`

### Claves para el examen

- Identificar raíz, hoja, padre, hijo sin dudar.
- Preorden empieza con raíz, inorden la pone en el medio, postorden al final.
- Inorden en BST = orden ascendente.
- No confundir subárbol izquierdo con derecho.

> **Resumen final**: un árbol organiza datos en jerarquía. En un binario cada nodo tiene hasta dos hijos. Según cómo visites raíz, izquierda y derecha, obtenés preorden, inorden o postorden.

# **FIN PRIMER PARCIAL**

# Apuntes POO2 - Cola de Prioridad, Montículos y Grafos

> Resumen ampliado con teoría completa para repaso.

## Índice

- [1. Cola de Prioridad](#1-cola-de-prioridad)
- [2. Montículos](#2-montículos-heaps)
- [3. Grafos](#3-grafos)
- [4. Algoritmo de Dijkstra](#4-algoritmo-de-dijkstra)
- [5. Coloreo de Grafos](#5-coloreo-de-grafos)

---

## 1. Cola de Prioridad

### 1.1 ¿Qué es un TDA?

Un Tipo de Dato Abstracto define QUÉ operaciones se pueden hacer, no CÓMO. La interfaz es un contrato.

Ventajas:

- Encapsulamiento
- Cambiar implementación sin tocar el código cliente
- Reutilización

### 1.2 Definición

Estructura donde cada elemento tiene prioridad. Siempre se extrae el de mayor prioridad (max) o menor (min).

No es FIFO. El orden de salida depende de la prioridad, no del orden de llegada.

### 1.3 Operaciones principales

- `crear()`: O(1)
- `insertar(x, p)`: agrega con prioridad p
- `extraer()`: saca y devuelve el de mejor prioridad
- `consultar()`: peek sin sacar
- `estaVacia()`, `tamano()`

### 1.4 Implementaciones comparadas

| Implementación        | insertar     | extraer      | consultar | Uso de memoria |
| --------------------- | ------------ | ------------ | --------- | -------------- |
| Lista ordenada        | O(n)         | O(1)         | O(1)      | O(n)           |
| Lista desordenada     | O(1)         | O(n)         | O(n)      | O(n)           |
| Árbol BST balanceado  | O(log n)     | O(log n)     | O(log n)  | O(n)           |
| **Montículo binario** | **O(log n)** | **O(log n)** | **O(1)**  | **O(n)**       |

### 1.5 Aplicaciones reales

- Planificador de CPU (procesos con prioridad)
- Algoritmo de Dijkstra (cola de distancias mínimas)
- Compresión Huffman
- Simulación de eventos discretos
- A\* en videojuegos

---

## 2. Montículos (Heaps)

### 2.1 Propiedades

1. Árbol binario **completo**: todos los niveles llenos excepto quizás el último, que se llena de izquierda a derecha
2. Propiedad de heap:
   - Min-heap: padre <= hijos
   - Max-heap: padre >= hijos

No está ordenado totalmente, solo garantiza el extremo en la raíz.

### 2.2 Representación con array

Se evita punteros. Para índice base 0:

- padre(i) = (i-1)//2
- hijo_izq(i) = 2\*i + 1
- hijo_der(i) = 2\*i + 2

Ejemplo min-heap [5,7,9,15,18,20,14]:

```
índice: 0 1 2 3  4  5  6
valor:  5 7 9 15 18 20 14
```

### 2.3 Operaciones

**insertar(x)**

1. Poner x al final
2. Flotar: mientras x < padre, intercambiar
   Complejidad: O(log n)

**extraerMin()**

1. Guardar raíz
2. Mover último a raíz
3. Hundir: intercambiar con hijo menor hasta cumplir propiedad
   Complejidad: O(log n)

**construirHeap(array)**

- Método ingenuo: n inserciones → O(n log n)
- Método óptimo (Floyd): hundir desde n/2 hacia 0 → O(n)

### 2.4 Variantes

- **d-ario**: cada nodo tiene d hijos, reduce altura
- **Binomial**: unión en O(log n)
- **Fibonacci**: decrementar clave en O(1) amortizado, usado en Dijkstra teórico

---

## 3. Grafos

### 3.1 Definición formal

G = (V, E) donde V es conjunto de vértices, E ⊆ V×V es conjunto de aristas.

### 3.2 Terminología

- **Adyacencia**: u y v son adyacentes si existe arista (u,v)
- **Incidencia**: arista incide en sus extremos
- **Camino**: secuencia v0,v1,...,vk con aristas entre consecutivos
- **Camino simple**: sin vértices repetidos
- **Ciclo**: camino que empieza y termina igual, con al menos una arista
- **Distancia**: longitud del camino más corto

### 3.3 Tipos

- **No dirigido**: arista {u,v} = {v,u}
- **Dirigido (digrafo)**: arista (u,v) ≠ (v,u)
- **Ponderado**: w: E → ℝ
- **Simple**: sin lazos ni aristas múltiples
- **Completo Kn**: n vértices, todas las aristas posibles, |E| = n(n-1)/2
- **Bipartito**: V = A ∪ B, aristas solo entre A y B
- **Conexo**: existe camino entre todo par (no dirigido)
- **Fuertemente conexo**: en dirigido, camino en ambos sentidos
- **Árbol**: grafo conexo sin ciclos, |E| = |V|-1
- **DAG**: grafo dirigido acíclico

### 3.4 Grados

- No dirigido: grado(v) = número de aristas incidentes
- Dirigido: grado_entrada + grado_salida
- Suma de grados = 2|E| (handshaking lemma)

### 3.5 Representaciones

**Matriz de adyacencia**

- M[i][j] = peso o 0/∞
- Espacio O(V²)
- Consultar arista O(1)
- Ideal para grafos densos

**Lista de adyacencia**

- Array de listas de vecinos
- Espacio O(V+E)
- Recorrer vecinos O(grado)
- Ideal para grafos dispersos

### 3.6 Ejemplo del PDF

V = {0,1,2,3,4,5,6}
Aristas dirigidas con peso:
0→1(2), 0→3(1), 1→3(3), 1→4(10), 3→4(2), 3→6(4), 3→5(8), 3→2(2), 2→0(4), 2→5(5), 4→6(6), 6→5(1)

### 3.7 Algoritmos fundamentales

- **BFS**: recorrido por niveles, O(V+E), caminos mínimos en no ponderado
- **DFS**: profundidad, O(V+E), detección de ciclos, orden topológico
- **Dijkstra**: caminos mínimos con pesos ≥0, usa cola de prioridad, O((V+E)logV)
- **Bellman-Ford**: pesos negativos, O(VE)
- **Kruskal/Prim**: árbol de expansión mínima

### 3.8 Ejercicio de implementación

Crear clases Vertice, Arista y Grafo con:

- agregarVertice(id)
- agregarArista(origen, destino, peso) // verificar duplicados
- obtenerAdyacentes(v)
- Implementar dos versiones: MatrizAdyacencia y ListaAdyacencia

# Apuntes - Dijkstra y Coloreo de Grafos

---

## 4. Algoritmo de Dijkstra

### 4.1 Objetivo

Dado un vértice origen, encontrar el camino de menor costo hacia todos los demás vértices en un grafo con pesos positivos.

### 4.2 Condiciones

- Grafo dirigido o no dirigido
- Todos los pesos > 0 (no funciona con negativos)
- Grafo conexo desde el origen

### 4.3 Idea clave

Mantener distancias tentativas. Siempre expandir el vértice no visitado con menor distancia actual (estrategia voraz). Una vez visitado, su distancia es definitiva.

### 4.4 Pseudocódigo

```
Dijkstra(G, origen):
  dist[v] = ∞ para todo v
  dist[origen] = 0
  Q = cola de prioridad con (0, origen)

  mientras Q no vacía:
    u = extraerMin(Q)
    para cada vecino v de u:
      si dist[v] > dist[u] + peso(u,v):
        dist[v] = dist[u] + peso(u,v)
        previo[v] = u
        actualizar Q
```

### 4.5 Ejemplo del PDF

Grafo con vértices A,B,C,D,E,F,G
Paso a paso (origen A):

- Inicial: dist[A]=0, resto ∞
- Visita B (5): actualiza C=9, E=13
- Visita C (9): actualiza D=12, F=31, G=17
- Visita D (12): actualiza F=23
- Visita E (13): sin mejoras
- Visita G (17): sin mejoras
- Visita F (23): fin

Resultado final:
A=0, B=5, C=9, D=12, E=13, F=23, G=17

### 4.6 Complejidad

- Con array: O(V²)
- Con heap binario: O((V+E) log V)
- Con Fibonacci heap: O(E + V log V)

### 4.7 Limitaciones y variantes

- No sirve con pesos negativos → usar Bellman-Ford
- A\* agrega heurística para búsqueda dirigida
- Dijkstra bidireccional para origen-destino único

---

## 5. Coloreo de Grafos

### 5.1 Definición

Asignar un color a cada vértice tal que vértices adyacentes tengan colores distintos.

### 5.2 Número cromático χ(G)

Mínimo número de colores necesarios.

Ejemplos:

- Grafo bipartito: χ=2
- Ciclo impar: χ=3
- Grafo completo Kn: χ=n
- Árbol: χ=2

### 5.3 Aplicaciones

- Asignación de frecuencias (celulares)
- Horarios de exámenes (materias = vértices, conflicto = arista)
- Registros en compiladores
- Sudoku

### 5.4 Complejidad

Encontrar χ(G) es NP-completo. No hay algoritmo polinomial conocido para el óptimo.

### 5.5 Algoritmos heurísticos

**Secuencial (greedy)**

1. Ordenar vértices (cualquier orden)
2. Para cada vértice, asignar el menor color no usado por vecinos
   Complejidad: O(V+E)
   Resultado depende del orden. En el PDF con orden alfabético da 4 colores.

**Welsh-Powell**

1. Ordenar vértices por grado decreciente
2. Aplicar greedy
   Suele mejorar. En el ejemplo del PDF logra χ=3.

**Matula (Smallest Last)**

1. Ordenar por grado creciente
2. Aplicar greedy
   En el PDF también logra 3 colores.

**DSATUR**
Elige el vértice con mayor saturación (colores distintos en vecinos). Muy efectivo en la práctica.

### 5.6 Cotas

- χ(G) ≤ Δ+1 donde Δ es grado máximo
- χ(G) ≥ ω(G) donde ω es tamaño de la clique máxima
- Teorema de Brooks: χ ≤ Δ excepto para completos y ciclos impares

### 5.7 Ejemplo del PDF

Grafo con 10 vértices (A-J).

- Solución trivial: 10 colores (uno por vértice)
- Greedy mal ordenado: 4 colores
- Welsh-Powell y Matula: 3 colores (óptimo para ese grafo)

Algoritmos de Prim y Kruskal
Árbol Recubridor Mínimo (ARM / MST)

Índice
[1. Definición](#1-definición)
[2. Kruskal](#2-algoritmo-de-kruskal)
[3. Prim](#3-algoritmo-de-prim)
[4. Ejemplo del PDF](#4-ejemplo-del-pdf)

---

Definición
Grafo conexo y no dirigido con pesos.

Árbol recubridor mínimo: conecta todos los vértices con la suma mínima de pesos.
Número de aristas = V - 1
Puede haber más de uno con mismo peso total.

Algoritmo de Kruskal
Ordenar todas las aristas por peso ascendente
Tomar la menor que no forme ciclo
Repetir hasta tener V-1 aristas

Complejidad: O(E log E) por el ordenamiento.
Estructura: Union-Find.

Algoritmo de Prim
Empezar en un vértice cualquiera
Tomar la arista de menor peso que conecte el árbol con un vértice fuera
Repetir hasta cubrir todos

Complejidad: O(E log V) con heap.
Ideal para grafos densos.

Ejemplo del PDF
Vértices: A, B, C, D, E, F, G, H, I, J (10)

Aristas:
E-B 3
J-G 7
H-I 8
E-I 9
I-J 9
D-E 10
B-A 11
D-H 15
I-F 19
A-F 21
F-C 25
F-G 28
F-J 30
C-G 32

Kruskal paso a paso
E-B (3) → toma
J-G (7) → toma
H-I (8) → toma
E-I (9) → toma
I-J (9) → toma (une componentes)
D-E (10) → toma
B-A (11) → toma
D-H (15) → rechaza (forma ciclo)
I-F (19) → toma
F-C (25) → toma → ¡listo! 9 aristas

Peso total = 3+7+8+9+9+10+11+19+25 = 101

Prim (empezando en E)
E-B 3
E-I 9
I-H 8
I-J 9
J-G 7
E-D 10
B-A 11
I-F 19
F-C 25
Mismo total: 101
