# U1 · Módulo 2 — Ecuaciones de recurrencia y algoritmos recursivos

> Basado en la clase U1C3 (*Ecuaciones de recurrencia y algoritmos recursivos*).

## 2.1 Motivación

Las funciones con **dos o más llamadas recursivas** (recursividad doble) tienen
un costo temporal/espacial muy alto. Si logramos extraer del código su
**ecuación de recurrencia**, podemos resolverla con los métodos del Módulo 1 y
obtener una **fórmula directa** que calcula el mismo valor sin recursión ni
iteración.

## 2.2 Del código a la ecuación (ruteo)

El procedimiento es un "ruteo" del código con cambio de nombres:

```
Función Fibonacci(n entero): entero
    Si (n < 2) entonces
        Fibonacci = 1                              ← de aquí salen a₀ y a₁
    Si no
        Fibonacci = Fibonacci(n-1) + Fibonacci(n-2) ← de aquí sale la recurrencia
    Fin si
Fin Función
```

Identificación:

| En el código | En la ecuación |
|---|---|
| `Fibonacci(0)` (caso base) | `a₀ = 1` |
| `Fibonacci(1)` (caso base) | `a₁ = 1` |
| `Fibonacci(n)` | `aₙ` |
| `Fibonacci(n-1) + Fibonacci(n-2)` | `aₙ₋₁ + aₙ₋₂` |

Resultado: `aₙ = aₙ₋₁ + aₙ₋₂`, o en formato homogéneo `aₙ − aₙ₋₁ − aₙ₋₂ = 0`,
con `C₀ = 1, C₁ = C₂ = −1`. Desde aquí se resuelve exactamente igual que en el
Módulo 1 (ecuación característica → raíces → α, β → término general).

## 2.3 Receta general

Para cualquier algoritmo con recursividad doble:

1. **Casos base** → condiciones iniciales `a₀` y `a₁` (evaluar la rama `n < 2`
   en `n = 0` y `n = 1`).
2. **Rama recursiva** → la recurrencia `aₙ = k₁·aₙ₋₁ + k₂·aₙ₋₂` (los
   coeficientes que multiplican a cada llamada).
3. Resolver con el método del Módulo 1: `r₁, r₂, α, β, aₙ`.

## 2.4 Ejercicios de la clase

Para cada función: encuentra su ecuación de recurrencia, determina las
condiciones iniciales, resuélvela (`r₁, r₂, α, β, aₙ`) y evalúa para `n = 100`.

**Función UNO:**
```
Función UNO(n: entero): entero
    Si (n < 2) entonces UNO = (n+1)² + 1
    Si no UNO = 3·UNO(n-1) − 2·UNO(n-2)
```
*(Condiciones iniciales: `a₀ = (0+1)²+1 = 2`, `a₁ = (1+1)²+1 = 5`.)*

**Función DOS:**
```
Función DOS(n: entero): entero
    Si (n < 2) entonces Retornar 2 − (2n − 1)
    Si no Retornar 3·DOS(n-1) − 2·DOS(n-2)
```
*(Condiciones iniciales: `a₀ = 2−(−1) = 3`, `a₁ = 2−1 = 1`.)*

**Función TRES:**
```
Función TRES(n: entero): entero
    Si (n < 2) entonces TRES = ((n+1)·(n−1))²
    Si no TRES = 3·TRES(n-1) − 2·TRES(n-2)
```
*(Condiciones iniciales: `a₀ = (1·(−1))² = 1`, `a₁ = (2·0)² = 0`.)*

**Función CUATRO:**
```
Función CUATRO(n: entero): TIPO
    Si (n < 2) entonces CUATRO = (n/(n+1))²
    Si no CUATRO = 6·CUATRO(n-1) − CUATRO(n-2)
```
Pregunta extra de la clase: ¿de qué **TIPO** debería ser la función CUATRO y
por qué? *(Pista: mira los casos base `a₀ = 0`, `a₁ = (1/2)² = 1/4` — el
resultado no es entero.)*

## 2.5 Enunciados en texto → ecuación de recurrencia

Cuando la recurrencia viene descrita en palabras:

1. Identificar en el texto las **condiciones iniciales** (`a₀`, `a₁`).
2. Si hace falta, **cambiar la escala** para manejar números cómodos
   (p. ej. trabajar en miles).
3. Buscar la **relación** entre el término `n` y los dos anteriores:
   `aₙ = k₁·aₙ₋₁ + k₂·aₙ₋₂`.

**Ejemplo de la clase (ventas de televisores, Mundial 2026):**
"La primera semana se vendieron 3 (miles), la segunda 4 (miles), y para una
semana `n` cualquiera las ventas son **menos cuatro veces** las de la semana
anterior **más 21 veces** las de la semana ante-anterior."

```
a₀ = 3,   a₁ = 4,   aₙ = −4·aₙ₋₁ + 21·aₙ₋₂
```

De aquí en adelante se procede de la forma conocida (ecuación característica
`r² + 4r − 21 = 0`, raíces `r₁ = 3`, `r₂ = −7`, etc.).

## Autoevaluación del módulo

1. Extrae la ecuación de recurrencia (con condiciones iniciales) de la función
   UNO y resuélvela por completo.
2. ¿Por qué los casos base del código corresponden a las condiciones iniciales
   de la ecuación?
3. Inventa un enunciado "en texto" cuya recurrencia sea `aₙ = 5aₙ₋₁ − 6aₙ₋₂`
   con `a₀ = 1, a₁ = 2`, y resuélvela.
