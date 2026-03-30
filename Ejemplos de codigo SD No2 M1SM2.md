Para cumplir con los objetivos de la **Segunda Secuencia Didáctica**, he preparado tres ejemplos de código en Python que progresan en complejidad, siguiendo las actividades de la **Fase de Desarrollo**.

Cada código incluye un enfoque de **pensamiento sistémico**, considerando entradas, procesos lógicos y salidas que impactan un entorno.

---

### 1. Práctica Guiada: Sistema de Clasificación de Riesgo (Decisiones Múltiples)
**Objetivo:** Evaluar el nivel de riesgo de un proyecto considerando variables interconectadas (Presupuesto y Tiempo).

```python
# TEMA: Sistema de decisiones múltiples con validación
# ENFOQUE SISTÉMICO: El riesgo no depende de una sola variable, sino de la relación entre ellas.

def evaluar_riesgo():
    print("--- Sistema de Evaluación de Riesgos de Proyecto ---")
    
    try:
        # Validación de datos (Parte de la práctica demostrativa)
        presupuesto = float(input("Ingrese el presupuesto disponible (USD): "))
        retraso_dias = int(input("Ingrese los días de retraso estimados: "))
        
        if presupuesto < 0 or retraso_dias < 0:
            raise ValueError("Los valores no pueden ser negativos.")

        # Lógica de decisión múltiple
        if presupuesto < 1000 and retraso_dias > 10:
            resultado = "RIESGO CRÍTICO: El proyecto requiere intervención inmediata."
        elif presupuesto < 5000 or retraso_dias > 5:
            resultado = "RIESGO MODERADO: Se recomienda monitoreo semanal."
        else:
            resultado = "RIESGO BAJO: El proyecto está dentro de los parámetros seguros."

        print(f"\nResultado del Análisis: {resultado}")

    except ValueError as e:
        print(f"Error de entrada: {e}. Por favor, ingrese números válidos.")

if __name__ == "__main__":
    evaluar_riesgo()
```

---

### 2. Práctica Supervisada: Recomendador Avanzado (4 Variables)
**Objetivo:** Simular un motor de recomendación lógico para la elección de una herramienta de IA basada en el perfil del usuario.

```python
# TEMA: Recomendador lógico con 4+ variables
# ENFOQUE SISTÉMICO: Considera el entorno técnico, económico y humano.

def recomendador_ia():
    print("--- Selector de Herramientas de IA para Empresas ---")
    
    # 1. Variable Técnica: Conocimiento de programación (0-10)
    coding = int(input("Nivel de programación del equipo (0-10): "))
    # 2. Variable Económica: Presupuesto
    presupuesto = input("¿Cuenta con presupuesto para licencias? (si/no): ").lower()
    # 3. Variable Operativa: Volumen de datos
    datos = input("¿El volumen de datos es Alto o Bajo?: ").lower()
    # 4. Variable Estratégica: Tiempo de implementación
    urgencia = input("¿La solución es urgente? (si/no): ").lower()

    print("\n--- Propuesta de Solución ---")

    # Lógica de recomendación basada en el sistema de variables
    if coding > 7 and datos == "alto":
        propuesta = "Desarrollo propio en Python utilizando TensorFlow/PyTorch."
    elif coding <= 7 and presupuesto == "si" and urgencia == "si":
        propuesta = "Uso de herramientas No-Code (ej. Azure ML o AWS SageMaker Canvas)."
    elif presupuesto == "no" and coding > 4:
        propuesta = "Implementación de modelos Open Source pre-entrenados."
    else:
        propuesta = "Consultoría externa para diagnóstico profundo."

    print(f"Basado en su perfil, la mejor opción es: {propuesta}")

recomendador_ia()
```

---

### 3. Práctica Autónoma: Asistente Lógico de Oficina (Mini-Proyecto)
**Objetivo:** Automatizar la priorización de tareas (Backlog) aplicando lógica sistémica para mejorar la productividad.

```python
# TEMA: Asistente Lógico de Automatización (Mini-proyecto)
# ENFOQUE SISTÉMICO: Optimización del flujo de trabajo (Workflow) escolar o de oficina.

class AsistenteTareas:
    def __init__(self):
        self.tareas = []

    def agregar_tarea(self):
        print("\n--- Nueva Tarea ---")
        nombre = input("Nombre de la tarea: ")
        deadline = int(input("Días para la entrega: "))
        importancia = int(input("Nivel de importancia (1-10): "))
        es_grupal = input("¿Es trabajo en equipo? (s/n): ").lower() == 's'

        # Cálculo lógico de prioridad (Heurística simple tipo IA)
        # Una tarea es más prioritaria si tiene poco tiempo y mucha importancia
        puntuacion_prioridad = (importancia * 2) - deadline
        if es_grupal: puntuacion_prioridad += 3 # El trabajo grupal requiere más coordinación

        self.tareas.append({
            "nombre": nombre,
            "puntos": puntuacion_prioridad,
            "tipo": "Colaborativa" if es_grupal else "Individual"
        })

    def generar_plan(self):
        # Ordenar tareas por puntuación de prioridad de mayor a menor
        self.tareas.sort(key=lambda x: x['puntos'], reverse=True)
        
        print("\n=== PLAN DE ACCIÓN RECOMENDADO ===")
        for i, t in enumerate(self.tareas, 1):
            impacto = "ALTO" if t['puntos'] > 10 else "MEDIO"
            print(f"{i}. {t['nombre']} [{t['tipo']}] - Impacto Sistémico: {impacto}")

# Ejecución del asistente
asistente = AsistenteTareas()
for _ in range(3): # El alumno puede registrar 3 tareas para probar
    asistente.agregar_tarea()
asistente.generar_plan()
```

---

### Cómo conectar estos códigos con la Propuesta Técnica (Fase de Cierre):

Para que el alumno tenga éxito en la entrega final de **8 horas**, debe usar estos códigos como "Evidencia Técnica" y explicar:

1.  **Entradas (Inputs):** ¿Qué datos recolecta el código? (Presupuestos, niveles de habilidad, tiempos).
2.  **Procesamiento:** ¿Cómo la lógica de Python (if/else, listas, funciones) simula la toma de decisiones humana?
3.  **Salidas (Outputs):** ¿Cómo la respuesta del programa resuelve el problema planteado inicialmente?
4.  **Visión Sistémica:** Explicar que, por ejemplo, en el *Asistente de Tareas*, una mala priorización no solo afecta una nota, sino que desequilibra el tiempo de descanso y el rendimiento en otras materias (impacto en todo el sistema).
