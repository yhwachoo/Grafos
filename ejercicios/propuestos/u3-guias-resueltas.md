# Guías resueltas de referencia (Unidad 3) — índice comentado

> Resumen de las dos guías **ya resueltas** subidas al curso:
> `guia_automatas_turing_resueltos.pdf` y
> `Ejercicios_Resueltos_para_la_Prueba_2_de_Lenguajes_Formales.pdf`.
> Aquí se indexa qué trae cada una y **qué técnica enseña cada ejercicio**,
> para usarlas como banco de estudio dirigido (las soluciones completas, con
> diagramas, están en los PDF originales).

## Guía 1 — "Autómatas finitos, autómatas de pila y máquinas de Turing"

Convención de la guía para pilas: `$` = fondo de pila, `ε` = pop;
transición `x, y → z` (lee `x`, tope `y`, reemplaza por `z`).

| Ej. | Enunciado | Técnica que enseña |
|---|---|---|
| 1 | `L₁ = {#1(w) ≡ 0 mod 3}`, `L₂ = {termina en 01}`: AFD de cada uno, **complemento**, **unión**, **concatenación** | Complemento = intercambiar finales/no finales (AFD completo); unión = **producto cartesiano** `(qᵢ,pⱼ)`; concatenación = conectar finales de A1 al inicial de A2 **con ε** |
| 2 | RegEx `(a∪b)*abb(a∪ε)` → AFND-ε → AFD | Thompson y, alternativa "pedagógica": AFD directo que **recuerda el sufijo** más largo que es prefijo de `abba` |
| 3 | AP para `L = {a²ⁿbⁿ / n ≥ 1}` | Apilar **una X por cada par** de a's (estados q0⇄q1 cuentan el par); pop por cada b. Incluye traza de `aaaabb` y por qué rechaza `aaab` |
| 4 | APND para `L = {aⁱbʲcᵏdˡ : i=k} ∪ {… : j=ℓ}` | **No determinismo como unión**: al inicio el autómata "elige" con ε qué igualdad verificar (rama A o rama B); basta que una rama acepte |
| 5 | MT 1 cinta para `L = {w#w / w ∈ {0,1}⁺}` | Marcar a la izquierda (0→X, 1→Y), cruzar `#`, comparar y marcar a la derecha (0→A, 1→B), volver; chequeo final. Costo O(n²) |
| 6 | MT **3 cintas**: suma y multiplicación unaria (`1ᵐ#1ⁿ`) | Suma = copiar ambos bloques a la cinta 3; multiplicación = `m·n` copiando el bloque `1ᵐ` (cinta 2) una vez **por cada** 1 del bloque `1ⁿ` |

> Los ejercicios 3–6 calzan directo con las preguntas 3 y 4 del formato
> oficial de la Prueba 3 (`prueba/ensayo-formato-oficial.md`).

## Guía 2 — "Ejercicios resueltos para la Prueba 2" (12/11/2024)

| Ej. | Enunciado | Técnica que enseña |
|---|---|---|
| 1 | GR `P={S→bA|λ, A→bB|λ, B→aA}` → AFD | GR→autómata directo (no terminal = estado, `X` = basura) |
| 2 | AFDs: "comienza con `00` y termina con `11`"; "no contiene `101`"; `(L1+L2)*` | Prefijo+sufijo obligatorios; **complemento de subcadena** (los lenguajes "no contiene" = invertir finales del "sí contiene"); esquema general de la estrella de una unión |
| 3 | "exactamente tres `a`" y "número de `a` divisible por 4" + **RegEx desde el autómata** | Contadores lineales/cíclicos de a's ignorando b's; lectura de la RegEx: `b*ab*ab*ab*` y `(b*ab*ab*ab*ab*)*` |
| 4 | GR de "sin dos `a` consecutivas" + su AFD | Diseño GR primero, autómata después; distinción **GRE vs GR definitiva** (la pauta muestra ambas) |
| 5 | AFND-λ (tabla) → AFND → AFD, completo | El desarrollo estrella: **tabla sin λ** primero, luego subconjuntos, marcar inalcanzables (B, C) y fusionar basuras (D, E, I) |
| 6 | AP para `L₁ = {aʳbˢcᵗ / s = r+2t}` y `L = {#a(w) = #b(w)}` | Descomponer `s=r+2t` como `aʳbʳ · b²ᵗcᵗ` (concatenación de dos AP con pila vacía); contador positivo/negativo en la pila (P/N/Z) para #a=#b **sin** orden fijo |
| 7 | MT: "número de subcadenas `01` es impar" | MT reconocedora con paridad |
| 8 | MT: `f(x,y) = (2x+y) mod y` en unario, 3 cintas | Componer operaciones: separar input, duplicar, sumar, y **módulo** entre cintas |
| 9 | MT: cociente y resto (`a div b` y `a mod b`) | División unaria por restas sucesivas, 3 cintas; DI inicial `(q0, a#b)` → final `(p, adivb # amodb)` |

## Cómo usar estas guías

1. **Antes de mirar la solución**, intenta cada enunciado desde esta lista.
2. Prioriza según el formato oficial de la Prueba 3: ejercicios de AP (guía 1
   ej. 3–4; guía 2 ej. 6) y de MT (guía 1 ej. 5–6; guía 2 ej. 7–9).
3. Las técnicas de "complemento / unión producto / concatenación ε" (guía 1
   ej. 1) son el fundamento de las preguntas integradoras tipo P1 y P2 del
   formato oficial.
