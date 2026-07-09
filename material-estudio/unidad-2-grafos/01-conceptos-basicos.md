# U2 · Módulo 1 — Grafos no ponderados: conceptos básicos

> Basado en la clase U2C1 (*Teoría de grafos no ponderados*).

## 1.1 Motivación e historia

En 1736, **Leonhard Euler** publica el primer análisis formal de un problema de
grafos: los **7 puentes de Königsberg** (Prusia Oriental, hoy Kaliningrado). El
problema: encontrar una ruta que cruce cada uno de los 7 puentes **sin repetir
ninguno**. La genialidad de Euler fue **abstraer**: quedarse solo con los
elementos esenciales (zonas de tierra = puntos, puentes = líneas) y descartar
todo lo demás (distancias, formas, el río).

Muchas cosas cotidianas son grafos: una red de metro, una malla PERT, un juego
infantil de "unir puntos".

## 1.2 Definición formal

```
G = (V, E) es un grafo  ⟺  V es un conjunto de vértices y
                            E ⊆ 2ᵛ con elementos de la forma {v, w} (aristas)
```

- `n = |V|` es el **orden** de G (cantidad de vértices).
- `m = |E|` es el **tamaño** de G (cantidad de aristas).

**Lo que NO importa en un grafo** (a diferencia de la geometría):

- Cómo se **dibuja**, mientras recoja las relaciones relevantes.
- Las **longitudes** de las aristas.
- Los **ángulos**.

Dos dibujos muy distintos pueden ser **el mismo grafo** (por ejemplo, un
triángulo equilátero, uno isósceles y uno escaleno son grafos idénticos:
3 vértices, 3 aristas). Las aristas son "elásticas".

## 1.3 Tipos de grafos

| Tipo | Característica | Ejemplo |
|---|---|---|
| **Digrafo** (grafo dirigido) | Las aristas son **flechas** (tienen dirección) | Malla PERT |
| **Multigrafo** | Entre un mismo par de vértices hay **2 o más** aristas | Los puentes de Königsberg |
| **Pseudografo** | Hay aristas que parten y terminan en el **mismo** vértice (lazos) | ¡Un autómata finito! (es pseudografo y digrafo) |
| **Grafo simple** | Sin dirección, sin lazos, sin aristas múltiples | Red de metro |

En esta unidad el objeto de estudio son los **grafos simples**.

## 1.4 Clasificaciones importantes

- **Conexo:** todas sus aristas/vértices están, de una forma u otra, conectados
  entre sí (hay camino entre cualquier par de vértices). **No conexo** en caso
  contrario.
- **Plano:** sus aristas no se cruzan en el dibujo, **o es posible redibujarlo**
  (sin romperlo) de modo que no se crucen. Ojo: que un dibujo tenga cruces no
  significa que el grafo no sea plano — recuerda que las aristas son elásticas.
- **Euleriano:** todas y cada una de sus **aristas** pueden recorrerse
  exactamente **una** vez. El grafo de Königsberg es el primer ejemplo de grafo
  **no** euleriano de la historia.
- **Hamiltoniano:** es posible recorrer todos sus **vértices** sin repetir
  ninguno (camino hamiltoniano). Si el último vértice es adyacente al primero,
  hay un **ciclo hamiltoniano**.

> Truco memorioso: **E**uleriano ↔ **a**ristas (recorrer todas las aristas);
> **H**amiltoniano ↔ vértices (visitar todos los vértices).

## 1.5 Ejercicio de la clase

Con 6 palitos de fósforo (sin romperlos), dibuja **todas** las figuras (grafos)
posibles: los lineales (árboles), los que incluyen formas geométricas
(triángulos, cuadriláteros, pentágonos), etc. Luego clasifícalos: ¿cuáles son
conexos?, ¿cuáles planos?, ¿cuáles eulerianos o hamiltonianos?

## Autoevaluación del módulo

1. Define orden y tamaño de un grafo. ¿Cuáles son los del grafo de Königsberg?
2. ¿Por qué un autómata finito es un pseudografo dirigido?
3. Da un ejemplo de grafo euleriano pero no hamiltoniano (o viceversa).
4. ¿Puede un grafo dibujado con cruces ser plano? Justifica.
