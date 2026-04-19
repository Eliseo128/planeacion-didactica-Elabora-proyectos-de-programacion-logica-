# 📘 Estructuras de Decisión en Python (if · elif · else)

**Objetivo:** Dominar el uso de estructuras condicionales en Python mediante una guía compacta + práctica progresiva, lista para trabajar en VS Code o Jupyter Notebook.

---

# 🧠 Fundamentos rápidos

### 🔹 Indentación

* Python usa **4 espacios** para definir bloques.
* No existen `{}`.

```python
if True:
    print("Correcto")  # pertenece al bloque
```

### 🔹 Operadores de comparación

```python
==  !=  >  <  >=  <=
```

### 🔹 Operadores lógicos

```python
and  or  not
```

### 🔹 Valores truthy / falsy

```python
False: 0, "", None, [], {}
True: cualquier otro valor
```

### 🔹 Dos puntos (`:`)

Siempre obligatorios:

```python
if condicion:
```

---

# 🛠️ Variantes y cuándo usarlas

| Estructura     | Uso                          |
| -------------- | ---------------------------- |
| `if`           | Ejecuta solo si se cumple    |
| `if-else`      | Dos caminos                  |
| `if-elif-else` | Múltiples decisiones         |
| `if` anidado   | Dependencia entre decisiones |
| Ternario       | Asignación corta             |

---

# 💻 Ejemplos explicados

## 🧩 Ejemplo 1: Clasificador de notas

### 📌 Pseudocódigo

```
SI nota >= 90 → A
SINO SI >= 80 → B
...
SINO → F
```

### 🧪 Código

```python
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
```

### ⚠️ Clave

* Se evalúa **en orden**
* Cuando una condición es verdadera → termina

---

## 🔐 Ejemplo 2: Control de acceso (anidado)

```python
usuario = input("Usuario: ")
contrasena = input("Contraseña: ")

if contrasena == "1234":
    if usuario == "admin":
        print("Acceso total")
    elif usuario == "editor":
        print("Acceso de edición")
    else:
        print("Solo lectura")
else:
    print("Acceso denegado")
```

### ⚠️ Clave

* Primero validas seguridad → luego roles

---

## ⚡ Ternario

```python
edad = int(input("Edad: "))
estado = "mayor de edad" if edad >= 18 else "menor de edad"
print(estado)
```

---

# ⚠️ Puntos clave y errores frecuentes

### ❌ Error 1: Mala indentación

```python
if True:
print("Error")  # ❌
```

✔️ Correcto:

```python
if True:
    print("Bien")
```

---

### ❌ Error 2: Olvidar `:`

```python
if edad >= 18  # ❌
```

---

### ❌ Error 3: Usar `=` en lugar de `==`

```python
if edad = 18:  # ❌
```

---

### ❌ Error 4: Redundancia innecesaria

```python
elif nota >= 80 and nota < 90  # innecesario
```

✔️ Mejor:

```python
elif nota >= 80:
```

---

### ❌ Error 5: Anidar sin necesidad

* Si no depende de otra condición → no anidar

---

# 📝 Módulo de 10 ejercicios progresivos

## 🟢 Básico

### 1. Par o impar

**Enunciado:** Determina si un número es par o impar
💡 Pista: `% 2`

```python
# Solución
num = int(input("Número: "))
if num % 2 == 0:
    print("Par")
else:
    print("Impar")
```

---

### 2. Mayor de dos números

```python
a = int(input("A: "))
b = int(input("B: "))

if a > b:
    print("A es mayor")
else:
    print("B es mayor o igual")
```

---

### 3. Número positivo, negativo o cero

```python
n = int(input("Número: "))

if n > 0:
    print("Positivo")
elif n < 0:
    print("Negativo")
else:
    print("Cero")
```

---

## 🟡 Intermedio

### 4. Descuento

**Enunciado:** Si compra > 1000 aplica 10%

```python
total = float(input("Total: "))

if total > 1000:
    total *= 0.9

print("Total final:", total)
```

---

### 5. Día laboral o fin de semana

```python
dia = input("Día: ")

if dia == "Sabado" or dia == "Domingo":
    print("Fin de semana")
else:
    print("Laboral")
```

---

### 6. Validar login simple

```python
user = input("Usuario: ")
pwd = input("Password: ")

if user == "admin" and pwd == "1234":
    print("Acceso permitido")
else:
    print("Acceso denegado")
```

---

### 7. Calculadora básica

```python
a = float(input("A: "))
b = float(input("B: "))
op = input("Operación (+,-,*,/): ")

if op == "+":
    print(a + b)
elif op == "-":
    print(a - b)
elif op == "*":
    print(a * b)
elif op == "/":
    if b != 0:
        print(a / b)
    else:
        print("Error: división por cero")
else:
    print("Operación inválida")
```

---

## 🔴 Intermedio–Avanzado

### 8. Año bisiesto

💡 Pista: divisible por 4, 100 y 400

```python
anio = int(input("Año: "))

if (anio % 4 == 0 and anio % 100 != 0) or (anio % 400 == 0):
    print("Bisiesto")
else:
    print("No bisiesto")
```

---

### 9. Clasificador de temperatura

```python
t = float(input("Temperatura: "))

if t < 0:
    print("Congelación")
elif t < 20:
    print("Frío")
elif t < 30:
    print("Templado")
else:
    print("Calor")
```

---

### 10. Sistema de acceso con roles (anidado)

```python
usuario = input("Usuario: ")
password = input("Password: ")

if password == "1234":
    if usuario == "admin":
        print("Panel completo")
    elif usuario == "editor":
        print("Panel edición")
    else:
        print("Panel lectura")
else:
    print("Acceso denegado")
```

---

# 📎 Tabla de referencia rápida

| Operador  | Uso         |
| --------- | ----------- |
| `==`      | Igual       |
| `!=`      | Diferente   |
| `>` `<`   | Comparación |
| `>=` `<=` | Inclusivo   |
| `and`     | Ambas       |
| `or`      | Alguna      |
| `not`     | Negación    |

---

# 🖥️ Tips para VS Code

### ⚙️ 1. Auto-indentación

* `Tab` → indentar
* `Shift + Tab` → desindentar

### ⚙️ 2. Ejecutar rápido

* `Ctrl + F5` → ejecutar script

### ⚙️ 3. Formateo automático

Instala extensión:

* **Python (Microsoft)**
* Usa:

```
Shift + Alt + F
```

---

# 💡 Recomendación final

* Prioriza **claridad sobre complejidad**
* Usa `elif` en lugar de múltiples `if` independientes cuando sean excluyentes
* Evita anidar si no es necesario

---

⛔ NO uses `switch/case`, `match/case` (Python 3.10+) ni bibliotecas externas. Solo `if/elif/else` puro.
