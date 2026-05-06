# POO2 - Apunte 1er Parcial

## UML (Lenguaje de Modelado Unificado)

### Diagrama de clases
Panorama general de las clases de un proyecto software y sus relaciones (atributos, métodos, etc).

- **Nombre**: identifica a la clase.
- **Atributos**: propiedades de la clase. Son cadenas de texto que representan el dato, independientemente de su tipo.
- **Métodos**: acciones que la clase puede realizar.
- **Responsabilidades**: contrato u obligaciones que la clase debe cumplir. Se redactan en lenguaje informal para que todos las entiendan.

### Relaciones entre clases
Tres relaciones fundamentales en el Diseño Orientado a Objetos:

1. **Dependencia**: una clase usa temporalmente a otra.
2. **Generalización (herencia)**: una clase hija hereda de una clase padre.
3. **Asociación**: conexión estructural entre clases. La **agregación** y la **composición** son casos particulares.

---

## Complejidad Computacional

Relación entre tamaño de entrada (N) y tiempo de ejecución (T).

| Notación | Nombre | Cómo crece | Ejemplo típico |
| --- | --- | --- | --- |
| O(1) | Constante | No crece, siempre igual | Acceder a un array por índice |
| O(log n) | Logarítmica | Crece muy lento, divide el problema (ej: a la mitad) | Búsqueda binaria |
| O(n) | Lineal | Crece proporcional a N | Recorrer una lista |
| O(n²) | Cuadrática | Dos bucles anidados | Bubble Sort, Insertion Sort |
| O(n³) | Cúbica | Tres bucles anidados | Multiplicación de matrices naive |
| O(nⁿ) / O(2ⁿ) | Exponencial / Factorial | Crece extremadamente rápido | Fuerza bruta, permutaciones |

> A mayor N, mayor T, pero la pendiente depende de la complejidad.

---

## Métodos de Ordenamiento Elementales

Algoritmos básicos para ordenar datos.

**Conceptos importantes**
- **Registro**: conjunto de datos (ej: alumno).
- **Clave**: valor por el cual se ordena (ej: nota).
- **Estabilidad**: mantiene el orden original de elementos con clave igual.
- **Sensibilidad**: el rendimiento depende del orden inicial (mejor si está ordenado, peor si está inverso).

| Algoritmo | Idea | Estable | Sensible | Complejidad |
| --- | --- | --- | --- | --- |
| **Selección (Selection Sort)** | Busca el menor y lo coloca en su posición | No | No | O(n²) |
| **Burbujeo (Bubble Sort)** | Compara adyacentes e intercambia | Sí | Sí | O(n²) |
| **Inserción (Insertion Sort)** | Inserta cada elemento en su posición correcta | Sí | Sí | O(n²) |

**Conclusión**: todos son O(n²). En la práctica, Inserción suele ser el más eficiente. La estabilidad importa cuando hay claves repetidas.

---

## Árboles (Estructura de Datos)

Estructura **dinámica**, **jerárquica** y **no lineal**. Se usa para organizar y buscar datos eficientemente.

### Elementos
- **Nodo**: cada elemento.
- **Raíz**: primer nodo (nivel 0).
- **Padre**: nodo con hijos.
- **Hijo**: nodo dependiente.
- **Hoja**: nodo sin hijos.
- **Rama**: camino entre nodos.
- **Árbol vacío**: sin nodos.
- **Nivel / Profundidad**: cantidad de niveles.

### Árbol binario
Cada nodo tiene como máximo 2 hijos: izquierdo y derecho.

### Árbol Binario de Búsqueda (BST)
Cumple: **izq < raíz < der**
- Subárbol izquierdo: valores menores.
- Subárbol derecho: valores mayores.
- Permite búsquedas eficientes.

### Recorridos (MUY IMPORTANTE)
- **Preorden**: Raíz → Izq → Der
- **Inorden (simétrico)**: Izq → Raíz → Der → en BST da valores ordenados
- **Postorden**: Izq → Der → Raíz

### Complejidad
- Recorrer árbol: O(n)
- Buscar en BST:
  - Mejor caso (balanceado): O(log n)
  - Peor caso (desbalanceado): O(n)

### Claves para el examen
- Identificar raíz, hoja, padre, hijo.
- Reconocer recorridos: pre (raíz primero), in (raíz en medio), post (raíz al final).
- Inorden en BST ordena.
- No confundirse con los subárboles.

> **Frase resumen**: Un árbol es una estructura jerárquica no lineal compuesta por nodos; en un árbol binario cada nodo tiene hasta dos hijos, y puede recorrerse en preorden, inorden o postorden según el orden de visita.
