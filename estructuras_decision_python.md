**Estructuras de Decisión en Python** if · elif · else — Guía completa con pseudocódigo y ejemplos 

**1\. Conceptos que debes saber antes de usarlas** 

• **Indentación (sangría):** Python usa 4 espacios para delimitar bloques. No hay llaves `{}` — el nivel de sangría define qué código pertenece a cada bloque. 

• **Operadores de comparación:** `==` (igual), `!=` (diferente), `>` / `<` (mayor/menor), `>=` / `<=` (mayor o igual / menor o igual). 

• **Operadores lógicos:** `and`, `or`, `not` — permiten combinar varias condiciones en una sola expresión. 

• **Valores truthy / falsy:** `0`, `""`, `None` y listas vacías `[]` se evalúan como `False`. Cualquier otro valor se evalúa como `True`. 

• **Dos puntos obligatorios:** Toda condición termina con `:` antes del bloque que le pertenece. **2\. Las 4 formas principales de usar la estructura** 

| Variante  | Cuándo usarla |
| :---- | :---- |
| if simple  | Ejecutar algo solo si se cumple la condición; si no, no hacer nada |
| if – else  | Elegir entre dos caminos posibles |
| if – elif – else  | Elegir entre tres o más casos mutuamente excluyentes |
| if anidado  | Una decisión dentro de otra (condiciones dependientes) |
| Ternario  | Asignar un valor en una sola línea |

**3\. Ejemplo 1 — Clasificador de notas escolares** 

**Problema:** Un profesor quiere un programa que, al ingresar la calificación numérica de un alumno (0–100), indique la letra correspondiente: A (90–100), B (80–89), C (70–79), D (60–69) o F (menos de 60). 

**Pseudocódigo** 

`INICIO` 

`LEER nota`  
`SI nota >= 90 ENTONCES` 

`MOSTRAR "Calificación: A"` 

`SINO SI nota >= 80 ENTONCES` 

`MOSTRAR "Calificación: B"` 

`SINO SI nota >= 70 ENTONCES` 

`MOSTRAR "Calificación: C"` 

`SINO SI nota >= 60 ENTONCES` 

`MOSTRAR "Calificación: D"` 

`SINO` 

`MOSTRAR "Calificación: F"` 

`FIN SI` 

`FIN` 

**Código en Python** 

`# Ejemplo 1: Clasificador de notas (if - elif - else)` 

`nota = int(input("Ingresa la calificación (0-100): "))` 

`if nota >= 90:` 

`print("Calificación: A — Excelente")` 

`elif nota >= 80:` 

`print("Calificación: B — Bien")` 

`elif nota >= 70:` 

`print("Calificación: C — Regular")` 

`elif nota >= 60:` 

`print("Calificación: D — Suficiente")` 

`else:` 

`print("Calificación: F — Reprobado")` 

■ **Punto clave:** Python evalúa los `elif` en orden. En cuanto una condición es verdadera, ejecuta ese bloque y salta el resto. Por eso no necesitas escribir `nota >= 80 and nota < 90`; al llegar a ese `elif` ya se sabe que la nota es menor a 90\. 

**4\. Ejemplo 2 — Control de acceso con if anidado** 

**Problema:** Un sistema tiene tres tipos de usuario: `admin`, `editor` y `visitante`. El programa pide el nombre de usuario y su contraseña. Si la contraseña es incorrecta, niega el acceso. Si es correcta, muestra un menú diferente según el rol. 

**Pseudocódigo** 

`INICIO` 

`LEER usuario`  
`LEER contraseña` 

`SI contraseña == "1234" ENTONCES` 

`SI usuario == "admin" ENTONCES` 

`MOSTRAR "Bienvenido Admin: acceso total"` 

`SINO SI usuario == "editor" ENTONCES` 

`MOSTRAR "Bienvenido Editor: puedes publicar"` 

`SINO` 

`MOSTRAR "Bienvenido Visitante: solo lectura"` 

`FIN SI` 

`SINO` 

`MOSTRAR "Contraseña incorrecta. Acceso denegado."` 

`FIN SI` 

`FIN` 

**Código en Python** 

`# Ejemplo 2: Control de acceso (if anidado + if-elif-else)` 

`usuario = input("Usuario: ")` 

`contrasena = input("Contraseña: ")` 

`if contrasena == "1234": # verifica contraseña` 

`if usuario == "admin": # verifica rol` 

`print("Bienvenido Admin: acceso total al sistema.")` 

`elif usuario == "editor":` 

`print("Bienvenido Editor: puedes crear y publicar.")` 

`else:` 

`print("Bienvenido Visitante: modo solo lectura.")` 

`else: # else del if externo` 

`print("Contraseña incorrecta. Acceso denegado.")` 

■ **Punto clave:** Los `if` anidados se usan cuando una decisión **depende de que otra condición ya se haya cumplido**. Aquí no tiene sentido verificar el rol si la contraseña ya fue rechazada. 

**5\. Variante extra — Expresión ternaria (una sola línea)** 

Python permite escribir un `if-else` simple en una sola línea para asignar valores. Esta forma se llama **expresión ternaria** o **operador condicional**. 

`# Forma larga (tradicional)` 

`if edad >= 18:` 

`estado = "mayor de edad"` 

`else:` 

`estado = "menor de edad"`  
`# Forma ternaria (equivalente en una línea)` 

`estado = "mayor de edad" if edad >= 18 else "menor de edad"` 

■■ **Recomendación:** Usa la forma ternaria solo cuando la condición y los valores son cortos y claros. Si la lógica es compleja, prefiere la forma tradicional para mantener la legibilidad del código. 

**6\. Resumen: operadores de comparación y lógicos** 

| Operador  | Tipo  | Significado  | Ejemplo |
| ----- | :---- | :---- | :---- |
| `==`  | Comparación  | Igual a  | `nota == 10` |
| `!=`  | Comparación  | Diferente de  | `usuario != "admin"` |
| `>`  | Comparación  | Mayor que  | `precio > 100` |
| `<`  | Comparación  | Menor que  | `edad < 18` |
| `>=`  | Comparación  | Mayor o igual que  | `nota >= 60` |
| `<=`  | Comparación  | Menor o igual que  | `temp <= 0` |
| `and`  | Lógico  | Y (ambas ciertas)  | `a > 0 and b > 0` |
| `or`  | Lógico  | O (alguna cierta)  | `dia == 'Sab' or dia == 'Dom'` |
| `not`  | Lógico  | Negación  | `not activo` |

Guía de Estudio · Estructuras de Decisión en Python · VS Code \+ Python