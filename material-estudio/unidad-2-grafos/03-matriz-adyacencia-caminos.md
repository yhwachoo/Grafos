# U2 · Módulo 3 — Matriz de adyacencia y caminos de largo n

> Basado en la clase U2C3 (*Matriz de adyacencias de un grafo*).

## 3.1 La matriz de adyacencia (MA)

Es la estructura de datos que registra las adyacencias entre **todos** los
vértices de un grafo:

- `MA[i][j] = 1` si el vértice `i` es adyacente al vértice `j`; `0` si no.
- En un grafo simple es **binaria**, **simétrica** y con **0's en la diagonal
  principal** (sin lazos).

**Ejemplo (grafo de 5 vértices de la clase):**

```
        1 2 3 4 5
    1 [ 0 1 0 0 0 ]
    2 [ 1 0 1 1 1 ]
MA= 3 [ 0 1 0 1 0 ]
    4 [ 0 1 1 0 1 ]
    5 [ 0 1 0 1 0 ]
```

## 3.2 El teorema clave: MAⁿ cuenta caminos

```
[MAⁿ]ᵢⱼ  =  cantidad de caminos DIFERENTES de largo n entre los vértices i y j
```

Es decir: elevar la matriz a la potencia `n` (multiplicación matricial,
`MMULT` en una planilla) responde de una sola vez, para **todos** los pares de
vértices, cuántos caminos de exactamente `n` aristas existen.

**Ejemplo de la clase:** con el grafo anterior, `MA⁴` da:

```
         1  2  3  4  5
    1 [  4  4  6  6  6 ]
    2 [  4 22 10 16 10 ]
MA⁴=3 [  6 10 11 10 11 ]
    4 [  6 16 10 16 10 ]
    5 [  6 10 11 10 11 ]
```

`[MA⁴]₂₅ = 10` ⇒ hay **10 caminos de largo 4** del vértice 2 al vértice 5.

> Ojo: los caminos contados **pueden repetir vértices y aristas** (por ejemplo
> `2→4→2→4→5` cuenta). Es "caminos" en el sentido amplio (recorridos).

## 3.3 Método para ENUMERAR los caminos (árboles de salida y llegada)

La potencia dice **cuántos** son; para listar **cuáles** son, el método de la
clase:

1. Anotar las **adyacencias del vértice de inicio** y las del **de llegada**.
   (Ej.: para ir de 2 a 5: `v₂: v₁,v₃,v₄,v₅` y `v₅: v₂,v₄`.)
2. Construir el **árbol de salida** desde el inicio (expandiendo nivel a nivel,
   la mitad del largo) y el **árbol de llegada** hacia el destino (la otra
   mitad).
3. **Unir las coincidencias**: cada rama del árbol de salida que "empalma" con
   una rama del árbol de llegada forma un camino completo.

**Los 10 caminos de largo 4 de 2 a 5** (del ejemplo):

```
2→1→2→4→5    2→3→2→4→5    2→3→4→2→5    2→4→2→4→5    2→4→3→2→5
2→4→3→4→5    2→4→5→2→5    2→4→5→4→5    2→5→2→4→5    2→5→4→2→5
```

Verificación cruzada: la lista debe tener **exactamente** `[MA⁴]₂₅ = 10`
elementos — si enumeras más o menos, algo falló.

## 3.4 Segundo ejemplo de la clase

Con otro grafo de 5 vértices, `[MA³]₁₃ = 4` ⇒ hay 4 caminos de largo 3 entre
los vértices 1 y 3 (se enumeran con el mismo método de árboles).

Y en un grafo de 7 vértices: ¿caminos de largo 5 entre v₃ y v₅? La potencia
dice que son **14**; con las adyacencias `v₃: v₂, v₄` y `v₅: v₄, v₆, v₇` se
dibujan el árbol de salida, el de llegada, y se unen las coincidencias.

## 3.5 Resumen operativo (para prueba/control)

1. Escribir la MA del grafo (simétrica, diagonal 0).
2. Calcular `MAⁿ` (a mano encadenando productos, o con planilla `MMULT`).
3. Leer `[MAⁿ]ᵢⱼ` → **cuántos** caminos.
4. Enumerarlos con **árboles de salida/llegada** → **cuáles** son.
5. Chequear que la cantidad enumerada coincida con la leída en la matriz.

## Autoevaluación del módulo

1. ¿Por qué la MA de un grafo simple es simétrica y con diagonal nula?
2. Si `[MA³]₁₄ = 0`, ¿qué significa?
3. Enumera los caminos de largo 2 entre dos vértices de un grafo pequeño que tú
   dibujes y verifica contra `MA²`.
4. ¿En qué difiere un "camino que repite vértices" de uno que no los repite?
   ¿Cuáles cuenta `MAⁿ`?
