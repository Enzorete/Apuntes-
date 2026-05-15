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

| Notación | Nombre | Crecimiento | Ejemplo típico |
| :--- | :--- | :--- | :--- |
| `O(1)` | Constante | No depende de N | Acceso por índice en array |
| `O(log n)` | Logarítmica | Divide el problema | Búsqueda binaria |
| `O(n)` | Lineal | Proporcional a N | Recorrer lista |
| `O(n²)` | Cuadrática | Dos bucles anidados | Bubble Sort, Insertion Sort |
| `O(n³)` | Cúbica | Tres bucles anidados | Multiplicación de matrices naive |
| `O(2ⁿ)` / `O(n!)` | Exponencial / Factorial | Explota rápido | Fuerza bruta, permutaciones |

> A mayor N, mayor T. La pendiente la define la notación.

---

## Métodos de Ordenamiento Elementales

**Conceptos clave**
- **Registro**: conjunto de datos (ej: alumno).
- **Clave**: valor por el cual se ordena (ej: nota).
- **Estabilidad**: mantiene orden relativo con claves iguales.
- **Sensibilidad**: rendimiento depende del orden inicial.

| Algoritmo | Idea central | Estable | Sensible | Complejidad |
| :--- | :--- | :---: | :---: | :---: |
| **Selección** | Busca el mínimo y lo coloca | No | No | `O(n²)` |
| **Burbujeo** | Intercambia adyacentes | Sí | Sí | `O(n²)` |
| **Inserción** | Inserta en posición correcta | Sí | Sí | `O(n²)` |

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
