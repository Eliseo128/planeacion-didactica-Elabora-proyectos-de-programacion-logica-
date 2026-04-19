# ROL
Eres un experto instructor de Python y diseñador de materiales técnicos educativos.

# CONTEXTO
Necesito que transformes la siguiente información sobre "Estructuras de Decisión en Python (if · elif · else)" en un material pedagógico claro, preciso y listo para estudio práctico en VS Code.

# CONTENIDO BASE
## 1. Conceptos previos obligatorios
- Indentación: Python usa 4 espacios para delimitar bloques. No existen `{}`. La sangría define la pertenencia al bloque.
- Operadores de comparación: `==`, `!=`, `>`, `<`, `>=`, `<=`
- Operadores lógicos: `and`, `or`, `not`
- Valores truthy/falsy: `0`, `""`, `None`, `[]` → `False`. Cualquier otro valor → `True`.
- Dos puntos (`:`): Obligatorios al final de toda línea condicional antes del bloque.

## 2. Variantes de uso
| Variante | Cuándo usarla |
|---|---|
| `if` simple | Ejecutar solo si se cumple la condición; si no, no hacer nada |
| `if` – `else` | Elegir entre dos caminos mutuamente excluyentes |
| `if` – `elif` – `else` | Elegir entre 3+ casos excluyentes |
| `if` anidado | Una decisión depende de que otra ya se haya cumplido |
| Ternario | Asignar un valor en una sola línea (`valor_si if condición else valor_no`) |

## 3. Ejemplo 1: Clasificador de notas (if-elif-else)
**Problema:** Convertir nota numérica (0-100) a letra: A(90-100), B(80-89), C(70-79), D(60-69), F(<60)
**Pseudocódigo:**
INICIO
  LEER nota
  SI nota >= 90 ENTONCES MOSTRAR "Calificación: A"
  SINO SI nota >= 80 ENTONCES MOSTRAR "Calificación: B"
  SINO SI nota >= 70 ENTONCES MOSTRAR "Calificación: C"
  SINO SI nota >= 60 ENTONCES MOSTRAR "Calificación: D"
  SINO MOSTRAR "Calificación: F"
FIN
**Código Python:**
nota = int(input("Ingresa la calificación (0-100): "))
if nota >= 90:
    print("Calificación: A — Excelente")
elif nota >= 80:
    print("Calificación: B — Bien")
elif nota >= 70:
    print("Calificación: C — Regular")
elif nota >= 60:
    print("Calificación: D — Suficiente")
else:
    print("Calificación: F — Reprobado")
⚠️ Punto clave: Python evalúa `elif` en orden. Al cumplirse uno, salta el resto. No hace falta acotar rangos con `and`.

## 4. Ejemplo 2: Control de acceso (if anidado)
**Problema:** Verificar contraseña y, si es correcta, mostrar menú según rol (`admin`, `editor`, `visitante`).
**Código Python:**
usuario = input("Usuario: ")
contrasena = input("Contraseña: ")
if contrasena == "1234":
    if usuario == "admin":
        print("Bienvenido Admin: acceso total al sistema.")
    elif usuario == "editor":
        print("Bienvenido Editor: puedes crear y publicar.")
    else:
        print("Bienvenido Visitante: modo solo lectura.")
else:
    print("Contraseña incorrecta. Acceso denegado.")
⚠️ Punto clave: El `if` anidado se usa cuando una decisión depende de otra. Aquí no tiene sentido verificar el rol si la contraseña ya falló.

## 5. Expresión ternaria
# Tradicional
if edad >= 18:
    estado = "mayor de edad"
else:
    estado = "menor de edad"
# Ternaria
estado = "mayor de edad" if edad >= 18 else "menor de edad"
💡 Recomendación: Úsala solo si la condición y los valores son cortos. Prioriza legibilidad en lógica compleja.

## 6. Tabla de referencia rápida
| Operador | Tipo | Significado | Ejemplo |
|---|---|---|---|
| `==` | Comparación | Igual a | `nota == 10` |
| `!=` | Comparación | Diferente de | `usuario != "admin"` |
| `>` / `<` | Comparación | Mayor / Menor que | `precio > 100` |
| `>=` / `<=` | Comparación | Mayor/Menor o igual | `nota >= 60` |
| `and` | Lógico | Y (ambas ciertas) | `a > 0 and b > 0` |
| `or` | Lógico | O (alguna cierta) | `dia == 'Sab' or dia == 'Dom'` |
| `not` | Lógico | Negación | `not activo` |

# OBJETIVO DE SALIDA
Genera un [ESPECIFICAR: ej. "guía de estudio interactiva", "cheat sheet imprimible", "módulo con ejercicios prácticos", "lección paso a paso para principiantes"].
"cheat sheet compacto y visual, ideal para imprimir o pegar en un bloc de notas"
"módulo de 10 ejercicios progresivos (básico → intermedio) con enunciados, pistas y soluciones comentadas"

# REQUISITOS TÉCNICOS Y DE FORMATO
1. Mantén el rigor sintáctico de Python (indentación de 4 espacios, `:` obligatorios, PEP 8).
2. Usa Markdown limpio. Separa teoría, pseudocódigo, código y notas clave con claridad.
3. Incluye al menos [NÚMERO] ejercicios prácticos con solución comentada.
4. Añade una sección de "Errores comunes y cómo evitarlos" basada en los puntos clave proporcionados.
6. Si el formato lo permite, agrega 2-3 atajos o configuraciones útiles de VS Code para trabajar con condicionales.
7. Tono: Pedagógico, directo y profesional. Idioma: Español.
8. No inventes sintaxis ni modifiques la lógica de los ejemplos base. Si agregas contenido nuevo, márcalo claramente.

# Guía interactiva / Notebook
1. "Formato compatible con Jupyter Notebook, celdas Markdown + celdas de código ejecutables, con comentarios# TODO:para práctica".
# ESTRUCTURA ESPERADA DE LA RESPUESTA
- 📘 Título y objetivo
- 🧠 Fundamentos rápidos (conceptos previos)
- 🛠️ Variantes y cuándo usarlas
- 💻 Ejemplos explicados (con pseudocódigo + Python)
- ⚠️ Puntos clave y errores frecuentes
- 📝 Ejercicios prácticos (enunciado + solución)
- 📎 Tabla de referencia rápida
- 🖥️ Tips para VS Code (opcional pero valorado)

Si la IA alucina sintaxis, añade al final: ⛔ NO usesswitch/case,match/case(Python 3.10+) ni bibliotecas externas. Soloif/elif/elsepuro.
