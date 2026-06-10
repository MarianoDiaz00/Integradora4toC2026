# Actividad integradora de Tecnologías de la Información — 4° año C

## Proyecto: **"Misión espacial Python"** 🚀
### La idea

Su grupo programará el **control de una misión espacial**. El programa tiene que ser
**interactivo**: le pide datos al usuario (`input`), valida la **matrícula** de la
nave, calcula la energía de despegue, el consumo de combustible y el tiempo de
viaje, y al final decide si la **misión se cumple, se aborta o falla**.

El programa final es uno solo, dividido en **4 partes (A, B, C y D)**. **Cada
integrante se hace cargo de una parte completa.** Las cuatro partes tienen la
misma estructura y dificultad, así cada uno trabaja y se evalúa por igual.

> **Lo más importante de la evaluación es el código y que cada uno entienda la totalidad
> del código.** En la defensa, cada integrante explica su parte línea por línea y como se
> integra en el código total.

> ✅ **Temas que hay que usar (todos vistos en clase):** tipos de datos (`str`,
> `int`, `float`, `bool`) y conversiones (`int()`, `float()`, `str()`); variables
> e `input()`; **cadenas** (concatenación, `len()`, índices, slices `[a:b]`,
> métodos como `.upper()`, `.isalpha()`, `.isdigit()`); funciones con `def` /
> `return` y **que se llamen entre sí**; condicionales `if / elif / else` (incluso
> anidados); operadores `+ - * ** / % //` y `and`, `or`, `not`.
---

## Estructura de cada parte

Cada integrante entrega **varias funciones** (no una sola), variables con su
tipo de dato anotado, y **una decisión `if/elif/else`**. Las funciones
que **calculan** deben recibir los datos por parámetro y **devolver** (`return`)
el resultado, no imprimirlo.

---

### PARTE A — La nave y su matrícula 🛰️ 

- **`matricula_valida(matricula)`** → `True` si tiene al menos 3 caracteres, las
  **2 primeras son letras** y **el resto son números**. Ej válido: `"NX42"`.
- **`codigo_mision(matricula, anio)`** → arma el código de misión:
  `"M-"` + las 2 primeras letras en mayúscula + el año. Ej: `"nx42", 2026` →
  `"M-NX2026"`. 
- **`energia_despegue(masa, velocidad)`** → `masa * velocidad ** 2` (la velocidad
  va **al cuadrado**). 

### PARTE B — El consumo del viaje ⛽ 

- **`consumo_base(distancia, consumo_km)`** → `distancia * consumo_km`. *(`*`)*
- **`hay_turbo(es_nave_nueva, velocidad)`** → `True` si la nave es nueva **o** la
  velocidad es 1000 o más.
- **`consumo_total(distancia, consumo_km, turbo)`** → si hay turbo, devuelve el
  **doble** de `consumo_base(...)`; si no, el consumo normal. *(esta función
  **llama a `consumo_base`** y multiplica)*

### PARTE C — Combustible y tiempo 📊

- **`nivel_combustible(actual, maximo)`** → `actual / maximo * 100`. *(`/`, `*`)*
- **`estado_tanque(porcentaje)`** → devuelve `"CRITICO"` (≤15), `"BAJO"` (≤40),
  `"OK"` (≤75) o `"LLENO"`. *(`if/elif/else` que devuelve un `str`)*
- **`dias_y_horas(horas)`** → convierte un total de horas en **días** (`//`) y
  **horas** restantes (`%`).

### PARTE D — Despegue y resultado 🎯  

- **`puede_despegar(combustible, falla_sistema)`** → `True` si hay combustible
  **y no** hay falla de sistema.
- **`combustible_restante(combustible, gasto)`** → el combustible después del
  viaje, pero **nunca menos que 0** (usá un `if/else`).
- **`mision_exitosa(combustible_final, sin_fallas)`** → `True` si quedó
  combustible **y** no hubo fallas.
---

La nave y el consumo

En el programa principal:

1. Pedir la **matrícula** con `input()` y validarla con `matricula_valida(...)`. Si
   no sirve, usar una por defecto. Después aplicarle `.upper()`.
2. Pedir la **masa** y la **velocidad** con `int(input(...))` y mostrar el **código
   de misión** y la **energía de despegue**.
3. Pedir la **distancia** y el **combustible** cargado; calcular el **consumo
   total** del viaje (con turbo según la velocidad) y el **combustible restante**.

El viaje y el despegue

Usando **todas las funciones del grupo**:

1. Mostrar el **nivel** y el **estado** del tanque después del viaje.
2. Calcular las horas de viaje (`distancia // velocidad`) y mostrarlas en **días y
   horas** con `dias_y_horas(...)`.
3. Resultado con `if / elif / else`: misión cumplida, despegue abortado (falla o
   sin combustible) o combustible insuficiente.

Prueben con **dos casos distintos** (por ejemplo: matrícula válida con buen
combustible, y una matrícula inválida con una velocidad de despegue peligrosa) para
mostrar que las validaciones y la lógica responden bien.

---

## Esqueleto para arrancar

```python
# ===== PARTE A =====
def matricula_valida(matricula):
    pass    # len(matricula) >= 3 and matricula[0:2].isalpha() and matricula[2:].isdigit()
def codigo_mision(matricula, anio):
    pass    # "M-" + matricula[0:2].upper() + str(anio)
def energia_despegue(masa, velocidad):
    pass    # masa * velocidad ** 2

# ===== PARTE B =====
def consumo_base(distancia, consumo_km):
    pass    # distancia * consumo_km
def hay_turbo(es_nave_nueva, velocidad):
    pass    # es_nave_nueva or velocidad >= 1000
def consumo_total(distancia, consumo_km, turbo):
    pass    # si turbo -> consumo_base(...) * 2 ; si no -> consumo_base(...)

# ===== PARTE C =====
def nivel_combustible(actual, maximo):
    pass    # actual / maximo * 100
def estado_tanque(porcentaje):
    pass    # if/elif/else -> "CRITICO"/"BAJO"/"OK"/"LLENO"
def dias_y_horas(horas):
    pass    # horas // 24  y  horas % 24

# ===== PARTE D =====
def puede_despegar(combustible, falla_sistema):
    pass    # combustible > 0 and not falla_sistema
def combustible_restante(combustible, gasto):
    pass    # si combustible - gasto < 0 -> 0 ; si no -> combustible - gasto
def mision_exitosa(combustible_final, sin_fallas):
    pass    # combustible_final > 0 and sin_fallas

# ===== PROGRAMA PRINCIPAL (Clases 2 y 3) =====
# pedir matricula, masa y velocidad; validar; mostrar codigo y energia.
# pedir distancia y combustible; calcular consumo y restante.
# mostrar nivel/estado del tanque y el tiempo de viaje en dias y horas.
# resultado final con if/elif/else.
```

---

## Cómo se evalúa (por alumno)

| Criterio | Puntos |
|---|---|
| **El código funciona** (todas sus funciones devuelven lo correcto) | 25 |
| **Explica su código** en la defensa (qué hace cada línea y por qué) | 30 |
| Tipos de datos y conversiones usados correctamente | 15 |
| Operadores y/o manejo de cadenas usados con sentido | 15 |
| Una función que **llame a otra** o un `if/elif/else` bien resuelto | 10 |
| Código legible: nombres claros y un comentario por función | 5 |
| **Total individual** | **100** |

> El despegue final (integración de las 4 partes) suma como **nota grupal aparte**.
> Si un alumno no puede explicar su propia parte, esa parte no se aprueba aunque el
> código funcione.

## Desafíos extra (para grupos que terminan antes)

- Validar que la **masa** y la **velocidad** sean números con `.isdigit()` antes de
  convertirlas.
- Que el código de misión incluya también el **último número** de la matrícula
  (`matricula[-1]`).
- Agregar una **segunda etapa** del viaje (otra distancia) reutilizando las
  funciones.
