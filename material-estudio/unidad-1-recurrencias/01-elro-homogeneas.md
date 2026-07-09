# U1 · Módulo 1 — Ecuaciones lineales de recurrencia (ELRO-1 y ELRO-2 homogéneas)

> Basado en la clase U1C1 (*Ecuaciones de recurrencia homogéneas de orden 2*).

## 1.1 Sucesiones y progresiones (preliminares)

- **Sucesión:** toda función de `ℕ₀` en un conjunto `S` (numérico o no). Cada
  elemento del recorrido se llama **término**: `f(n) = aₙ`.
- **Progresión aritmética:** cada término *equidista* del anterior y del
  siguiente (hay una **distancia** constante). Ej.: `1, 4, 7, 10, …` (distancia 3).
- **Progresión geométrica:** existe una **razón** constante entre términos
  consecutivos. Ej.: `1, 2, 4, 8, 16, …` (razón 2).

## 1.2 ELRO-1 (orden 1)

La fórmula general depende **solo del término anterior**:

```
aₙ = k₂ + aₙ₋₁   (aritmética)      aₙ = r·aₙ₋₁   (geométrica)
a₀ = k₁                            a₀ = k₁
```

El objetivo siempre es el mismo: encontrar una **expresión directa** para `aₙ`
en función de `n` y las constantes, sin calcular los `n−1` términos anteriores.

Ej.: `a₀ = 1, aₙ = aₙ₋₁ + 3` (término general recursivo) tiene como mejor
solución `aₙ = a₀ + 3n` (término general directo).

## 1.3 ELRO-2 (orden 2): definición

La fórmula general depende de los **dos términos inmediatamente anteriores**:

```
a₀ = k₀ ,  a₁ = k₁                     (condiciones iniciales, k₀,k₁ ∈ ℝ)
C₀·aₙ + C₁·aₙ₋₁ + C₂·aₙ₋₂ = bₙ         (C₀, C₂ ≠ 0)
```

- Si `bₙ = 0` la ELRO-2 es **homogénea**; si no, **no homogénea**.
- **Fibonacci** es el ejemplo canónico de ELRO-2 homogénea:
  `a₀=0, a₁=1, aₙ = aₙ₋₁ + aₙ₋₂` (o sea `1·aₙ − 1·aₙ₋₁ − 1·aₙ₋₂ = 0`).

## 1.4 Herramientas de solución

Para una ELRO-2 homogénea `C₀·aₙ + C₁·aₙ₋₁ + C₂·aₙ₋₂ = 0`:

| Elemento | Expresión |
|---|---|
| **Polinomio característico** | `P(r) = C₀r² + C₁r + C₂` |
| **Ecuación característica** | `C₀r² + C₁r + C₂ = 0` |
| **Solución particular** | `aₙ = rⁿ` |
| **Solución general (raíces reales distintas `r₁ ≠ r₂`)** | `aₙ = α·r₁ⁿ + β·r₂ⁿ` |
| **Solución general (raíces reales iguales `r₁ = r₂ = r`)** | `aₙ = α·rⁿ + β·n·rⁿ` |

**De dónde sale la ecuación característica:** al proponer `aₙ = rⁿ` se obtiene
`C₀rⁿ + C₁rⁿ⁻¹ + C₂rⁿ⁻² = 0`, y dividiendo por `rⁿ⁻²` queda
`C₀r² + C₁r + C₂ = 0`.

## 1.5 Método paso a paso (receta)

1. Escribir la ecuación en forma homogénea e identificar `C₀, C₁, C₂`.
2. Plantear y resolver la **ecuación característica** → raíces `r₁, r₂`.
3. Elegir la **solución general** según si las raíces son distintas o iguales.
4. Usar las **condiciones iniciales** `a₀, a₁` para armar un sistema 2×2 en `α, β`.
5. Resolver el sistema y escribir el **término general** `aₙ`.

## 1.6 Ejemplo 1 — raíces distintas

`2aₙ + 3aₙ₋₁ − 2aₙ₋₂ = 0`, con `a₀ = 0, a₁ = 1`.

1. Ecuación característica: `2r² + 3r − 2 = 0`.
2. Raíces: `r₁ = 1/2`, `r₂ = −2` (distintas).
3. Solución general: `aₙ = α·(1/2)ⁿ + β·(−2)ⁿ`.
4. Sistema con las condiciones iniciales:
   ```
   a₀ = 0 = α + β
   a₁ = 1 = α/2 − 2β
   ```
5. Resolviendo: `α = 2/5`, `β = −2/5`. **Término general:**
   ```
   aₙ = (2/5)·((1/2)ⁿ − (−2)ⁿ)
   ```

## 1.7 Ejemplo 2 — raíces iguales

`4aₙ − 12aₙ₋₁ + 9aₙ₋₂ = 0`, con `a₀ = −1, a₁ = 1`.

1. Ecuación característica: `4r² − 12r + 9 = 0`.
2. Raíces: `r₁ = r₂ = 3/2` (¡iguales! discriminante 0).
3. Solución general (segunda forma): `aₙ = α·(3/2)ⁿ + β·n·(3/2)ⁿ`.
4. Sistema:
   ```
   a₀ = −1 = α
   a₁ =  1 = α·(3/2) + β·(3/2)
   ```
5. `α = −1`, `β = 5/3`. **Término general:**
   ```
   aₙ = ((5/3)·n − 1)·(3/2)ⁿ
   ```

## 1.8 Fibonacci en forma cerrada

Con `a₀ = 0, a₁ = 1` y ecuación característica `r² − r − 1 = 0`:

```
r₁ = (1+√5)/2        r₂ = (1−√5)/2
```

Del sistema `α + β = 0` y `α·r₁ + β·r₂ = 1` se obtiene `α = 1/√5`, `β = −1/√5`:

```
Fib(n) = (1/√5)·((1+√5)/2)ⁿ − (1/√5)·((1−√5)/2)ⁿ
```

Esta es la **fórmula de Binet**: calcula el n-ésimo Fibonacci **sin** iterar ni
recursar.

## 1.9 Ejercicios propuestos de la clase

Encuentra el término general y evalúa para el `n` dado:

1. `aₙ − 6aₙ₋₁ + 9aₙ₋₂ = 0`; `a₀=1, a₁=1`; `n=100`
2. `9aₙ + 3aₙ₋₁ − 2aₙ₋₂ = 0`; `a₀=2, a₁=0`; `n=200`
3. `aₙ + 2aₙ₋₁ − 8aₙ₋₂ = 0`; `a₀=1, a₁=2`; `n=125`
4. `4aₙ + 2aₙ₋₁ − 6aₙ₋₂ = 0`; `a₀=2, a₁=1`; `n=1000`
5. `aₙ − 7aₙ₋₁ + 10aₙ₋₂ = 0`; `a₀=3, a₁=1`; `n=250`
6. `aₙ + 4aₙ₋₁ + 4aₙ₋₂ = 0`; `a₀=1, a₁=3`; `n=199`
7. `aₙ + (3/4)aₙ₋₁ − (9/8)aₙ₋₂ = 0`; `a₀=0, a₁=1`; `n=150`
8. `aₙ − (5/6)aₙ₋₁ + (1/6)aₙ₋₂ = 0`; `a₀=1, a₁=2`; `n=10000`

Y solo el término general para:

9. `aₙ − 5aₙ₋₁ + 4aₙ₋₂ = 0`; `a₀=2, a₁=3`
10. `aₙ + 8aₙ₋₁ + 16aₙ₋₂ = 0`; `a₀=1, a₁=2`
11. `2aₙ − 6aₙ₋₁ − 20aₙ₋₂ = 0`; `a₀=2, a₁=1`
12. `9aₙ + 3aₙ₋₁ + (1/4)aₙ₋₂ = 0`; `a₀=1, a₁=1`
13. `aₙ − 2aₙ₋₁ − 15aₙ₋₂ = 0`; `a₀=2, a₁=1`
14. `3aₙ − 4aₙ₋₁ + aₙ₋₂ = 0`; `a₀=1, a₁=1`
15. `−2aₙ − 3aₙ₋₁ + 4aₙ₋₂ = 0`; `a₀=0, a₁=1`
16. `aₙ − 10aₙ₋₁ + 25aₙ₋₂ = 0`; `a₀=−1, a₁=2`

> **Nota:** la clase U1C2 (ELRO-2 **no homogéneas**) no está entre los archivos
> disponibles; cuando la tengas, este módulo puede extenderse con ese caso.
