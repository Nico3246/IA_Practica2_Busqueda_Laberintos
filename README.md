# IA - Práctica 2: Algoritmos de Búsqueda en Laberintos

Práctica universitaria de **Inteligencia Artificial** desarrollada en **Python**, centrada en la implementación y comparación de algoritmos de búsqueda aplicados a la resolución de laberintos.

El programa permite generar o cargar laberintos y resolverlos mediante distintos algoritmos de búsqueda no informada e informada, mostrando métricas básicas como nodos expandidos, profundidad alcanzada, tamaño máximo de la estructura de datos utilizada y tiempo de ejecución.

---

## Objetivos de la práctica

El proyecto está orientado a trabajar conceptos fundamentales de búsqueda en Inteligencia Artificial:

- representación de estados;
- generación de sucesores;
- búsqueda no informada;
- búsqueda informada;
- uso de heurísticas;
- comparación entre estrategias;
- reconstrucción de caminos;
- medición del coste computacional de cada algoritmo.

---

## Algoritmos implementados

### Búsqueda en anchura

Archivo:

```text
modulos/BusquedaAnchura.py
```

Implementa una búsqueda en anchura utilizando una cola FIFO.

Permite obtener información como:

- camino encontrado;
- número de nodos expandidos;
- máximo número de elementos almacenados en la cola;
- profundidad máxima alcanzada.

### Búsqueda en profundidad

Archivo:

```text
modulos/BusquedaProfundidad.py
```

Implementa una búsqueda en profundidad mediante una pila.

El algoritmo avanza por caminos no visitados y retrocede cuando alcanza un punto sin sucesores disponibles.

### Búsqueda en profundidad limitada

Archivo:

```text
modulos/ProfLimite.py
```

Variante de búsqueda en profundidad en la que el usuario establece un límite máximo de profundidad.

### Búsqueda en profundidad iterativa

Archivo:

```text
modulos/ProfIterativa.py
```

Ejecuta búsquedas sucesivas aumentando progresivamente el límite de profundidad hasta encontrar la solución.

### Búsqueda bidireccional

Archivo:

```text
modulos/ProfBidireccional.py
```

Realiza la exploración simultáneamente desde:

- la entrada del laberinto;
- la salida.

La búsqueda finaliza cuando ambas exploraciones se encuentran.

### Greedy Best-First Search

Archivo:

```text
modulos/GBFS.py
```

Implementa **GBFS (Greedy Best-First Search)** utilizando una cola de prioridad.

La prioridad depende únicamente de la estimación heurística hacia la meta.

### A*

Archivo:

```text
modulos/A.py
```

Implementa el algoritmo **A*** utilizando:

```text
f(n) = g(n) + h(n)
```

donde:

- `g(n)` representa el coste acumulado desde el origen;
- `h(n)` representa la estimación heurística hasta la salida.

### IDA*

Archivo:

```text
modulos/IDA.py
```

Implementa **IDA*** mediante búsqueda en profundidad iterativa guiada por un umbral sobre:

```text
f(n) = g(n) + h(n)
```

El umbral se incrementa progresivamente hasta localizar la solución.

---

## Heurísticas

Las heurísticas se encuentran en:

```text
modulos/Heuristicas.py
```

El menú permite seleccionar entre tres opciones.

### Manhattan

```text
|x1 - x2| + |y1 - y2|
```

### Euclídea

```text
sqrt((x1 - x2)^2 + (y1 - y2)^2)
```

### Heurística personal

El proyecto incluye además una función heurística propia basada en la distancia Manhattan con una corrección relacionada con la mayor diferencia entre coordenadas.

---

## Gestión de laberintos

La clase principal para representar los laberintos se encuentra en:

```text
modulos/Laberinto.py
```

Permite:

- crear laberintos de tamaño aleatorio;
- generar una entrada y una salida;
- introducir obstáculos;
- guardar un laberinto;
- cargar laberintos desde archivos de texto;
- mostrar el laberinto en consola;
- localizar las posiciones de entrada y salida.

Los símbolos principales utilizados son:

| Símbolo | Significado |
|---|---|
| `#` | Obstáculo |
| `E` | Entrada |
| `S` | Salida |
| espacio | Casilla transitable |
| `.` | Camino marcado por el algoritmo |

---

## Laberintos incluidos

El repositorio incluye varios ejemplos:

```text
modulos/maze1.txt
modulos/maze2.txt
modulos/maze3.txt
modulos/Laberinto.txt
```

También puede generarse un nuevo laberinto desde el menú del programa.

---

## Menú principal

El punto de entrada es:

```text
modulos/main.py
```

Al ejecutar el programa se puede:

1. crear un laberinto nuevo;
2. cargar `maze1.txt`;
3. cargar `maze2.txt`;
4. cargar `maze3.txt`;
5. cargar un laberinto guardado;
6. seleccionar una heurística;
7. ejecutar cualquiera de los algoritmos disponibles.

El menú de algoritmos incluye:

```text
1. A*
2. IDA*
3. GBFS
4. Búsqueda en profundidad
5. Búsqueda en anchura
6. Búsqueda bidireccional
7. Búsqueda en profundidad iterativa
8. Búsqueda en profundidad con límite
```

---

## Métricas mostradas

Dependiendo del algoritmo, el programa muestra varias métricas de ejecución:

- tiempo empleado;
- nodos expandidos;
- profundidad máxima;
- tamaño máximo de la cola o pila;
- camino recorrido;
- solución encontrada sobre el propio laberinto.

Estas medidas permiten comparar de forma práctica el comportamiento de distintas estrategias de búsqueda.

---

## Estructura del proyecto

```text
IA_Practica_2/
├── modulos/
│   ├── A.py
│   ├── BusquedaAnchura.py
│   ├── BusquedaProfundidad.py
│   ├── GBFS.py
│   ├── Heuristicas.py
│   ├── IDA.py
│   ├── Laberinto.py
│   ├── ProfBidireccional.py
│   ├── ProfIterativa.py
│   ├── ProfLimite.py
│   ├── main.py
│   ├── maze1.txt
│   ├── maze2.txt
│   ├── maze3.txt
│   └── Laberinto.txt
├── .gitignore
└── README.md
```

---

## Tecnologías

- **Python**
- Biblioteca estándar de Python:
  - `queue`
  - `random`
  - `math`
  - `time`

El código no depende de bibliotecas externas para su ejecución.

---

## Ejecución

Debido a que los módulos utilizan importaciones locales y los archivos de laberinto se cargan mediante rutas relativas, la forma más sencilla de ejecutar el proyecto es entrar en la carpeta `modulos`:

```bash
cd modulos
python main.py
```

En Windows también puede utilizarse:

```powershell
cd modulos
py main.py
```

---

## Flujo de uso

Un flujo típico es:

1. ejecutar `main.py`;
2. crear o cargar un laberinto;
3. seleccionar una heurística;
4. elegir un algoritmo;
5. observar el camino encontrado;
6. comparar las métricas obtenidas;
7. reiniciar el laberinto antes de ejecutar otro algoritmo si es necesario.

---

## Estado del proyecto

El repositorio contiene una implementación académica orientada a experimentar con algoritmos de búsqueda.

Algunas características del código responden al objetivo didáctico de la práctica:

- interfaz únicamente por consola;
- representación matricial del laberinto;
- movimientos ortogonales;
- costes unitarios;
- métricas calculadas directamente durante cada búsqueda;
- implementación independiente de cada algoritmo para facilitar su estudio y comparación.

No está planteado como una librería genérica de pathfinding ni como una aplicación final de producción.

---

## Conceptos trabajados

La práctica permite trabajar directamente con:

- espacio de estados;
- frontera y conjunto de visitados;
- búsqueda en anchura;
- búsqueda en profundidad;
- profundidad limitada;
- profundización iterativa;
- búsqueda bidireccional;
- búsqueda voraz;
- A*;
- IDA*;
- funciones heurísticas;
- reconstrucción de caminos;
- análisis comparativo de algoritmos.

---

## Contexto académico

Proyecto desarrollado como **Práctica 2 de Inteligencia Artificial**.

Su finalidad principal es estudiar y comparar diferentes estrategias de búsqueda mediante un problema de navegación en laberintos.
