# Control Formativo 2 — Teoría de Grafos (Unidad 2)

> Transcripción del control formativo oficial de la Unidad 2
> (`Crtl_formativo_2_20263.docx`). **Nota:** los grafos G1, G2 y G3 del
> documento original son figuras que no se pudieron extraer como texto; los
> enunciados que dependen de ellos se transcriben igualmente como referencia
> del **tipo de ejercicio**, y deben resolverse mirando la figura en el
> documento original.

---

## Ítem 1 — Fórmulas de valencias (algoritmo de la clase U2C2)

Para las siguientes `Fv` (fórmulas de valencias) determina si son o no
**gráficas** — es decir, si es posible dibujar un grafo sin aristas duplicadas
ni auto-incidentes — utilizando el **algoritmo de las valencias**. Para un par
de ellas, dibuja un grafo con dichas fórmulas.

a) `Fv = 2:3:4:3:1:4:3`
b) `Fv = 4:3:5:1:5:3:1`
c) `Fv = 1:3:4:3:2:6:5`
d) `Fv = 5:2:5:2:5:1:4`

### Pauta del ítem 1 (verificada con el algoritmo)

**a) `2:3:4:3:1:4:3` → SÍ es gráfica.**
```
ordenar: 4:4:3:3:3:2:1 → quitar 4, restar a las 4 sig. → 3:2:2:2:2:1
ordenar y quitar 3 → 1:1:1:2:1 → ordenar: 2:1:1:1:1 → quitar 2 → 0:0:1:1
ordenar: 1:1:0:0 → quitar 1 → 0:0:0 → solo ceros ⇒ SÍ ✓
```

**b) `4:3:5:1:5:3:1` → SÍ es gráfica.**
```
ordenar: 5:5:4:3:3:1:1 → quitar 5 → 4:3:2:2:0:1
ordenar: 4:3:2:2:1:0 → quitar 4 → 2:1:1:0:0 → quitar 2 → 0:0:0:0 ⇒ SÍ ✓
```

**c) `1:3:4:3:2:6:5` → SÍ es gráfica.**
```
ordenar: 6:5:4:3:3:2:1 → quitar 6 → 4:3:2:2:1:0 → quitar 4 → 2:1:1:0:0
→ quitar 2 → 0:0:0:0 ⇒ SÍ ✓
```

**d) `5:2:5:2:5:1:4` → NO es gráfica.**
```
ordenar: 5:5:5:4:2:2:1 → quitar 5 → 4:4:3:1:1:1 → quitar 4 → 3:2:0:0:1
ordenar: 3:2:1:0:0 → quitar 3 → 1:0:−1:0 → ¡negativo! ⇒ NO ✗
```

---

## Ítem 2 — Caminos de largo n (grafo G1 de la figura)

Para el grafo no ponderado **G1** (vértices 1–6, ver figura del documento
original):

a) Determina (genera la lista) el **total de caminos de largo 5** del vértice 2
al vértice 4. Puedes utilizar su **matriz de adyacencias** (registrar la matriz
final) o los **subárboles de salida y llegada**.
b) Del total anterior, lista los caminos que **no repiten** vértices.
c) Del total anterior, lista los caminos que **sí repiten** vértices.

*(Técnica: Módulo 3 de la Unidad 2 — potencias de MA + árboles de salida/llegada.)*

---

## Ítem 3 — Rutas óptimas y AEM (grafo G2 de la figura)

Para el grafo ponderado **G2**:

a) Encuentra el **camino óptimo** (secuencia de vértices) entre **B y G**, y su
costo. *(Dijkstra)*
b) Encuentra el **camino óptimo** entre **A y H**, y su costo. *(Dijkstra)*
c) Genera el **árbol de expansión mínima** con **Kruskal**; registra la
secuencia de aristas elegidas.
d) Genera el AEM con **Prim**; registra la secuencia de aristas elegidas.

*(Técnica: Módulo 4 de la Unidad 2 — método tabular de Dijkstra; Kruskal ordena
aristas globalmente, Prim hace crecer el árbol.)*

---

## Ítem 4 — Flujo máximo (digrafo G3 de la figura)

Para el **digrafo ponderado** (capacidades) **G3** (vértices A–K, con
capacidades 2, 4, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16 según la figura),
determina el **flujo máximo** que es posible enviar desde el vértice **A** al
vértice **K**. Deja **registro explícito** del proceso (rutas elegidas, cuellos
de botella, capacidades actualizadas en cada ronda).

*(Técnica: Módulo 4 de la Unidad 2 — Ford-Fulkerson.)*

---

## Mapa control ↔ material de estudio

| Ítem | Tema | Módulo U2 |
|---|---|---|
| 1 | Fv gráfica (Havel-Hakimi) | `02-valencias-formula-grafica.md` |
| 2 | Caminos de largo n (MA + árboles) | `03-matriz-adyacencia-caminos.md` |
| 3 | Dijkstra + Kruskal + Prim | `04-grafos-ponderados.md` |
| 4 | Ford-Fulkerson | `04-grafos-ponderados.md` |
