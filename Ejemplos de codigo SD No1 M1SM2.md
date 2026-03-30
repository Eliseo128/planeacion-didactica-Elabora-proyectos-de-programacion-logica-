¡Excelente idea! A continuación, te presento ejemplos de código en Python para cada una de las prácticas de laboratorio en las tres fases. Estos ejemplos están diseñados para ser didácticos, funcionales y alineados con los objetivos de cada momento.

---

## 🟢 FASE DE APERTURA - Práctica Demostrativa

### **Ejemplo: Introducción a la sintaxis de Python con un simulador de decisiones simples**

Este ejemplo se utiliza para mostrar a los estudiantes la estructura básica de Python y cómo se pueden simular procesos de decisión lógica.

```python
# ============================================
# PRÁCTICA DEMOSTRATIVA - Introducción a Python
# Simulador básico de decisión para un asistente virtual
# ============================================

# 1. Variables y tipos de datos
nombre_usuario = input("👤 ¿Cuál es tu nombre? ")
edad = int(input("📅 ¿Cuántos años tienes? "))
esta_lloviendo = input("🌧️ ¿Está lloviendo? (sí/no): ").lower()

# 2. Estructura condicional simple
print("\n" + "="*40)
print(f"✨ Hola {nombre_usuario}, analizando tu situación...")
print("="*40)

# 3. Lógica de decisión simulada (base para futuros sistemas de IA)
if edad >= 18:
    print("✅ Eres mayor de edad.")
    
    if esta_lloviendo == "sí":
        print("🌂 Te recomiendo llevar paraguas si vas a salir.")
    else:
        print("☀️ El clima está despejado, ¡disfruta tu día!")
        
else:
    print("📚 Eres menor de edad.")
    print("🎮 Te recomiendo actividades supervisadas.")

# 4. Bucle simple para mostrar iteración
print("\n📋 Sugerencias personalizadas para ti:")
actividades = ["Leer un libro", "Practicar programación", "Hacer ejercicio"]

for i, actividad in enumerate(actividades, 1):
    print(f"   {i}. {actividad}")

print("\n💡 ¿Te diste cuenta? ¡Acabas de usar un algoritmo!")
print("   Este es el primer paso para crear sistemas de IA.")
```

**Explicación para los estudiantes:**
- Se introducen variables, entrada de datos, condicionales y bucles.
- Se establece la analogía: "así como tú tomas decisiones basadas en condiciones, una IA también lo hace".

---

## 🟡 FASE DE DESARROLLO - Prácticas de Laboratorio

### **1. Práctica Guiada: Sistema de recomendación básico**

```python
# ============================================
# PRÁCTICA GUIADA - Sistema de Recomendación
# Uso de lógica condicional para sugerir contenido
# ============================================

def recomendar_pelicula(genero, edad, tiempo_disponible):
    """
    Función que recomienda una película basada en:
    - Género preferido
    - Edad del usuario
    - Tiempo disponible
    """
    
    print("\n🎬 ANALIZANDO TUS PREFERENCIAS...")
    
    # Validación de entrada
    if edad < 0 or edad > 120:
        return "❌ Edad no válida."
    
    # Lógica de recomendación por género
    if genero == "acción":
        if edad < 12:
            recomendacion = "Los Increíbles (Animación con acción)"
        elif edad < 18:
            recomendacion = "Spider-Man: Across the Spider-Verse"
        else:
            recomendacion = "John Wick (Acción intensa para adultos)"
            
    elif genero == "comedia":
        if tiempo_disponible < 90:
            recomendacion = "Cortos de Pixar (Menos de 1 hora)"
        else:
            recomendacion = "Supercool (Comedia juvenil)"
            
    elif genero == "ciencia ficción":
        if edad < 15:
            recomendacion = "Wall-E (Ciencia ficción familiar)"
        else:
            recomendacion = "Interestelar (Ciencia ficción profunda)"
    else:
        recomendacion = "No tenemos recomendaciones para ese género. Prueba: acción, comedia o ciencia ficción."
    
    return f"🎯 RECOMENDACIÓN: {recomendacion}"

# ========== PROGRAMA PRINCIPAL ==========
print("="*50)
print("🎥 SISTEMA DE RECOMENDACIÓN DE PELÍCULAS")
print("="*50)

# Entrada de datos
nombre = input("👤 Nombre: ")
genero = input("🎭 Género preferido (acción/comedia/ciencia ficción): ").lower()
edad = int(input("📅 Edad: "))
tiempo = int(input("⏱️ Tiempo disponible (minutos): "))

# Llamada a la función y muestra de resultado
resultado = recomendar_pelicula(genero, edad, tiempo)
print("\n" + "="*50)
print(resultado)
print("="*50)

# Extensión: Mostrar historial de recomendaciones
historial = []
historial.append({"usuario": nombre, "recomendacion": resultado})
print(f"\n📊 Historial de {len(historial)} recomendación(es) registrada(s).")
```

---

### **2. Práctica Supervisada: Sistema de diagnóstico lógico**

```python
# ============================================
# PRÁCTICA SUPERVISADA - Sistema de Diagnóstico
# Simulación de un sistema experto básico (síntomas → diagnóstico)
# ============================================

# Base de conocimiento (diccionario de síntomas y diagnósticos)
base_conocimiento = {
    "fiebre": {
        "tos": "🤧 Posible gripe o resfriado común.",
        "dolor_cabeza": "🦠 Posible infección viral. Consulta a un médico.",
        "default": "🌡️ Fiebre sin otros síntomas. Reposo e hidratación."
    },
    "dolor_estómago": {
        "náuseas": "🍽️ Posible intoxicación alimentaria.",
        "fiebre": "⚠️ Posible apendicitis. ¡ACUDE A URGENCIAS!",
        "default": "🍵 Indigestión. Té de manzanilla y reposo."
    },
    "dolor_cabeza": {
        "visión_borrosa": "👁️ Posible migraña con aura. Busca un lugar oscuro y silencioso.",
        "náuseas": "🤕 Migraña severa. Requiere evaluación médica.",
        "default": "💧 Deshidratación o tensión. Bebe agua y descansa."
    }
}

def diagnosticar():
    """
    Función interactiva que realiza un diagnóstico basado en síntomas.
    Simula el razonamiento de un sistema experto.
    """
    
    print("\n🩺 SISTEMA DE DIAGNÓSTICO RÁPIDO")
    print("="*40)
    print("⚠️ NOTA: Este es un simulador educativo.")
    print("   Ante cualquier emergencia, acude al médico.")
    print("="*40)
    
    # Recolección de síntomas principales
    sintoma_principal = input("\n🔍 ¿Cuál es tu síntoma principal?\n   (fiebre/dolor_estómago/dolor_cabeza): ").lower()
    
    if sintoma_principal not in base_conocimiento:
        return "❌ Síntoma no reconocido en nuestra base de conocimiento."
    
    # Recolección de síntoma secundario
    sintoma_secundario = input("📋 ¿Presentas algún otro síntoma? (tos/dolor_cabeza/náuseas/fiebre/visión_borrosa): ").lower()
    
    # Lógica de diagnóstico con anidamiento de condiciones
    if sintoma_secundario in base_conocimiento[sintoma_principal]:
        diagnostico = base_conocimiento[sintoma_principal][sintoma_secundario]
    else:
        diagnostico = base_conocimiento[sintoma_principal]["default"]
    
    return diagnostico

def mostrar_consejos(diagnostico):
    """Recomendaciones generales según el tipo de diagnóstico"""
    if "URGENCIAS" in diagnostico:
        print("\n🚨 ¡ESTA ES UNA SITUACIÓN DE EMERGENCIA!")
        print("   Por favor, acude al centro de salud más cercano de inmediato.")
    elif "médico" in diagnostico.lower():
        print("\n📞 Se recomienda consultar con un profesional de la salud.")
    else:
        print("\n💚 Sigue las recomendaciones y monitorea tus síntomas.")

# ========== PROGRAMA PRINCIPAL ==========
print("🏥 BIENVENIDO AL SISTEMA DE DIAGNÓSTICO LÓGICO")
print("(Simulación de un sistema experto basado en reglas)")

while True:
    resultado = diagnosticar()
    print("\n📋 DIAGNÓSTICO SUGERIDO:")
    print(f"   {resultado}")
    mostrar_consejos(resultado)
    
    continuar = input("\n¿Deseas realizar otra consulta? (sí/no): ").lower()
    if continuar != "sí":
        print("\n👋 ¡Cuídate! Recuerda que esto es solo una simulación educativa.")
        break
```

---

### **3. Práctica Autónoma: Chatbot básico con anidamiento**

```python
# ============================================
# PRÁCTICA AUTÓNOMA - Chatbot Básico
# Simulación de un asistente conversacional con lógica anidada
# ============================================

import random
import time

# Base de respuestas del chatbot
saludos = ["¡Hola!", "👋 ¡Qué gusto verte!", "✨ ¡Bienvenido!", "😊 ¡Hola! ¿Cómo estás?"]
despedidas = ["¡Hasta luego!", "👋 Nos vemos pronto", "😊 ¡Que tengas un excelente día!", "✨ ¡Hasta la próxima!"]

def respuesta_por_defecto():
    """Respuesta genérica cuando no se reconoce la entrada"""
    respuestas = [
        "Interesante. Cuéntame más.",
        "No estoy seguro de entender. ¿Podrías explicarlo de otra forma?",
        "Eso suena importante. ¿Quieres profundizar en el tema?",
        "🤔 No tengo información sobre eso. ¿Te ayudo con programación o tecnología?"
    ]
    return random.choice(respuestas)

def procesar_mensaje(mensaje):
    """
    Función principal que procesa el mensaje del usuario
    Utiliza lógica condicional anidada para clasificar intenciones
    """
    mensaje = mensaje.lower()
    
    # === NIVEL 1: Detección de saludos ===
    if any(palabra in mensaje for palabra in ["hola", "buenas", "saludos", "qué tal"]):
        return random.choice(saludos)
    
    # === NIVEL 2: Detección de despedidas ===
    elif any(palabra in mensaje for palabra in ["adiós", "chao", "hasta luego", "nos vemos"]):
        return random.choice(despedidas)
    
    # === NIVEL 3: Consultas sobre programación ===
    elif "python" in mensaje or "código" in mensaje or "programar" in mensaje:
        if "aprender" in mensaje:
            return "📚 ¡Excelente! Python es ideal para empezar. ¿Quieres que te recomiende recursos?"
        elif "difícil" in mensaje:
            return "💪 Todos empezamos así. La práctica constante es la clave. ¿En qué parte tienes dudas?"
        else:
            return "🐍 Python es un lenguaje versátil usado en IA, desarrollo web y más. ¿Te interesa algún área específica?"
    
    # === NIVEL 4: Consultas sobre Inteligencia Artificial ===
    elif "ia" in mensaje or "inteligencia artificial" in mensaje:
        if "qué es" in mensaje or "definición" in mensaje:
            return "🤖 La IA es la simulación de procesos de inteligencia humana por máquinas. ¿Quieres saber cómo se programa?"
        elif "ejemplo" in mensaje:
            return "💡 Ejemplos de IA: asistentes como Siri, recomendaciones de Netflix, autos autónomos. ¿Te gustaría crear uno?"
        else:
            return "🧠 La IA tiene muchos campos: machine learning, procesamiento de lenguaje, visión computacional. ¿Qué te llama la atención?"
    
    # === NIVEL 5: Consultas sobre el curso ===
    elif "curso" in mensaje or "clase" in mensaje or "aprender" in mensaje:
        return "📖 En este curso aprenderás algoritmos, lógica de programación y cómo construir sistemas inteligentes. ¿Tienes alguna pregunta específica?"
    
    # === NIVEL 6: Respuesta por defecto ===
    else:
        return respuesta_por_defecto()

# ========== PROGRAMA PRINCIPAL ==========
print("="*55)
print("🤖 CHATBOT EDUCATIVO - Asistente de Programación e IA")
print("="*55)
print("Puedes preguntarme sobre:")
print("  • Programación en Python")
print("  • Inteligencia Artificial")
print("  • El curso que estás tomando")
print("Escribe 'salir' para terminar la conversación.")
print("="*55)

nombre_usuario = input("\nAntes de empezar, ¿cómo te llamas? ").capitalize()
print(f"\n✨ ¡Encantado de conocerte, {nombre_usuario}!")

# Bucle principal de conversación
conversacion_activa = True
while conversacion_activa:
    # Entrada del usuario
    entrada = input(f"\n{nombre_usuario}: ")
    
    # Verificar si quiere salir
    if entrada.lower() in ["salir", "exit", "adiós", "terminar"]:
        print(f"\n🤖: {random.choice(despedidas)}")
        print(f"📊 Resumen de la conversación guardado.")
        conversacion_activa = False
    
    else:
        # Procesar y mostrar respuesta con efecto de escritura
        respuesta = procesar_mensaje(entrada)
        print(f"\n🤖: ", end="")
        for caracter in respuesta:
            print(caracter, end="", flush=True)
            time.sleep(0.02)  # Efecto de escritura
        print()  # Salto de línea final

print("\n💡 ¡Practica modificando este chatbot! Agrega más temas y respuestas.")
```

---

## 🔴 FASE DE CIERRE - Proyecto Integrador

### **Ejemplo: Evaluador de crédito (minisistema inteligente)**

```python
# ============================================
# PROYECTO INTEGRADOR - Evaluador de Crédito
# Sistema de decisión simulado con múltiples factores
# ============================================

import json
import datetime
from typing import Dict, List, Tuple

class EvaluadorCredito:
    """
    Clase que simula un sistema de evaluación crediticia.
    Utiliza algoritmos de decisión basados en múltiples criterios.
    """
    
    def __init__(self):
        """Inicializa el evaluador con los criterios de evaluación"""
        self.historial_evaluaciones: List[Dict] = []
        self.puntaje_maximo = 100
        
        # Pesos para cada criterio (importancia relativa)
        self.pesos = {
            "ingresos": 0.35,
            "edad": 0.15,
            "historial_laboral": 0.20,
            "deudas": 0.20,
            "garantias": 0.10
        }
    
    def evaluar_ingresos(self, ingreso_mensual: float, gastos_mensuales: float) -> Tuple[float, str]:
        """
        Evalúa la capacidad de pago basada en ingresos y gastos
        """
        capacidad_ahorro = ingreso_mensual - gastos_mensuales
        relacion_ingreso_gasto = capacidad_ahorro / ingreso_mensual if ingreso_mensual > 0 else 0
        
        if relacion_ingreso_gasto >= 0.3:
            return 100, "Excelente capacidad de ahorro"
        elif relacion_ingreso_gasto >= 0.15:
            return 70, "Capacidad de pago aceptable"
        elif relacion_ingreso_gasto >= 0.05:
            return 40, "Capacidad de pago limitada"
        else:
            return 10, "Alto riesgo de impago"
    
    def evaluar_edad(self, edad: int) -> Tuple[float, str]:
        """
        Evalúa el factor edad en relación con la estabilidad financiera
        """
        if 25 <= edad <= 45:
            return 100, "Edad óptima para crédito"
        elif 46 <= edad <= 65:
            return 80, "Edad adecuada, considerar horizonte de pago"
        elif 18 <= edad <= 24:
            return 60, "Perfil joven, historial limitado"
        elif edad > 65:
            return 50, "Requeriría garantías adicionales"
        else:
            return 0, "No cumple edad mínima"
    
    def evaluar_historial_laboral(self, años_antiguedad: int, empleo_actual: str) -> Tuple[float, str]:
        """
        Evalúa la estabilidad laboral
        """
        if años_antiguedad >= 3 and empleo_actual.lower() == "formal":
            return 100, "Alta estabilidad laboral"
        elif años_antiguedad >= 1 and empleo_actual.lower() == "formal":
            return 70, "Estabilidad laboral en consolidación"
        elif años_antiguedad >= 2 and empleo_actual.lower() == "independiente":
            return 60, "Perfil independiente con trayectoria"
        else:
            return 30, "Historial laboral limitado"
    
    def evaluar_nivel_deudas(self, deudas_totales: float, ingresos_mensuales: float) -> Tuple[float, str]:
        """
        Evalúa el nivel de endeudamiento
        """
        if ingresos_mensuales == 0:
            return 0, "Sin ingresos registrados"
        
        relacion_deuda_ingreso = (deudas_totales / ingresos_mensuales) * 100
        
        if relacion_deuda_ingreso <= 30:
            return 100, "Nivel de deuda saludable"
        elif relacion_deuda_ingreso <= 50:
            return 60, "Nivel de deuda moderado"
        elif relacion_deuda_ingreso <= 70:
            return 30, "Alto nivel de endeudamiento"
        else:
            return 0, "Sobreendeudamiento crítico"
    
    def evaluar_garantias(self, tiene_garantia: bool, valor_garantia: float, monto_solicitado: float) -> Tuple[float, str]:
        """
        Evalúa las garantías ofrecidas
        """
        if not tiene_garantia:
            return 50, "Sin garantías, evaluación más estricta"
        
        cobertura = (valor_garantia / monto_solicitado) * 100 if monto_solicitado > 0 else 0
        
        if cobertura >= 150:
            return 100, "Garantía sobregarantizada"
        elif cobertura >= 100:
            return 80, "Garantía completa"
        elif cobertura >= 50:
            return 60, "Garantía parcial"
        else:
            return 30, "Garantía insuficiente"
    
    def calcular_puntaje_total(self, evaluaciones: Dict[str, Tuple[float, str]]) -> float:
        """
        Calcula el puntaje ponderado total
        """
        puntaje_total = 0
        for criterio, (puntaje, _) in evaluaciones.items():
            puntaje_total += puntaje * self.pesos.get(criterio, 0)
        
        return round(puntaje_total, 2)
    
    def determinar_decision(self, puntaje_total: float, monto_solicitado: float) -> Dict:
        """
        Determina la decisión final basada en el puntaje obtenido
        """
        if puntaje_total >= 80:
            decision = "APROBADO"
            nivel_riesgo = "Bajo"
            mensaje = "✅ Crédito aprobado. Excelente perfil crediticio."
            tasa_interes = "12% anual"
        elif puntaje_total >= 60:
            decision = "APROBADO CON CONDICIONES"
            nivel_riesgo = "Medio"
            mensaje = "⚠️ Crédito aprobado con tasa ajustada. Se requiere revisión adicional."
            tasa_interes = "18% anual"
        elif puntaje_total >= 40:
            decision = "EN REVISIÓN"
            nivel_riesgo = "Alto"
            mensaje = "📋 Solicitud en análisis. Se requieren documentos adicionales."
            tasa_interes = "Pendiente de evaluación"
        else:
            decision = "RECHAZADO"
            nivel_riesgo = "Muy Alto"
            mensaje = "❌ Crédito no aprobado. Perfil no cumple con criterios mínimos."
            tasa_interes = "No aplica"
        
        return {
            "decision": decision,
            "nivel_riesgo": nivel_riesgo,
            "mensaje": mensaje,
            "tasa_interes": tasa_interes,
            "puntaje": puntaje_total
        }
    
    def evaluar_solicitud(self, datos_solicitante: Dict) -> Dict:
        """
        Método principal que coordina toda la evaluación
        """
        print("\n" + "="*60)
        print("🏦 SISTEMA DE EVALUACIÓN CREDITICIA")
        print("="*60)
        
        # Realizar evaluaciones por criterio
        evaluaciones = {}
        
        # Evaluar ingresos
        evaluaciones["ingresos"] = self.evaluar_ingresos(
            datos_solicitante["ingresos_mensuales"],
            datos_solicitante["gastos_mensuales"]
        )
        
        # Evaluar edad
        evaluaciones["edad"] = self.evaluar_edad(datos_solicitante["edad"])
        
        # Evaluar historial laboral
        evaluaciones["historial_laboral"] = self.evaluar_historial_laboral(
            datos_solicitante["antiguedad_laboral"],
            datos_solicitante["tipo_empleo"]
        )
        
        # Evaluar nivel de deudas
        evaluaciones["deudas"] = self.evaluar_nivel_deudas(
            datos_solicitante["deudas_totales"],
            datos_solicitante["ingresos_mensuales"]
        )
        
        # Evaluar garantías
        evaluaciones["garantias"] = self.evaluar_garantias(
            datos_solicitante["tiene_garantia"],
            datos_solicitante.get("valor_garantia", 0),
            datos_solicitante["monto_solicitado"]
        )
        
        # Calcular puntaje total
        puntaje_total = self.calcular_puntaje_total(evaluaciones)
        
        # Determinar decisión
        decision = self.determinar_decision(puntaje_total, datos_solicitante["monto_solicitado"])
        
        # Construir resultado completo
        resultado = {
            "fecha_evaluacion": datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S"),
            "solicitante": datos_solicitante["nombre"],
            "monto_solicitado": datos_solicitante["monto_solicitado"],
            "puntaje_total": puntaje_total,
            "evaluacion_por_criterio": {
                criterio: {"puntaje": p, "comentario": c} 
                for criterio, (p, c) in evaluaciones.items()
            },
            "decision_final": decision
        }
        
        # Guardar en historial
        self.historial_evaluaciones.append(resultado)
        
        return resultado
    
    def mostrar_reporte(self, resultado: Dict):
        """
        Muestra un reporte formateado de la evaluación
        """
        print("\n" + "="*60)
        print("📊 REPORTE DE EVALUACIÓN CREDITICIA")
        print("="*60)
        
        print(f"\n👤 Solicitante: {resultado['solicitante']}")
        print(f"💰 Monto solicitado: ${resultado['monto_solicitado']:,.2f} MXN")
        print(f"📅 Fecha: {resultado['fecha_evaluacion']}")
        
        print("\n📈 PUNTAJE POR CRITERIO:")
        print("-"*40)
        for criterio, datos in resultado['evaluacion_por_criterio'].items():
            print(f"  • {criterio.title()}: {datos['puntaje']} pts - {datos['comentario']}")
        
        print(f"\n🎯 PUNTAJE TOTAL: {resultado['puntaje_total']}/100")
        
        print("\n🏷️ DECISIÓN FINAL:")
        print(f"  • Decisión: {resultado['decision_final']['decision']}")
        print(f"  • Nivel de riesgo: {resultado['decision_final']['nivel_riesgo']}")
        print(f"  • {resultado['decision_final']['mensaje']}")
        print(f"  • Tasa de interés sugerida: {resultado['decision_final']['tasa_interes']}")
        
        print("\n" + "="*60)

# ========== PROGRAMA PRINCIPAL ==========

def main():
    """Función principal que ejecuta el sistema evaluador"""
    
    # Datos de ejemplo para demostración
    solicitante = {
        "nombre": "Ana Martínez",
        "edad": 32,
        "ingresos_mensuales": 35000,
        "gastos_mensuales": 18000,
        "deudas_totales": 5000,
        "antiguedad_laboral": 4,
        "tipo_empleo": "formal",
        "monto_solicitado": 150000,
        "tiene_garantia": True,
        "valor_garantia": 200000
    }
    
    # Crear instancia del evaluador
    evaluador = EvaluadorCredito()
    
    # Realizar evaluación
    print("🏦 BIENVENIDO AL SISTEMA EVALUADOR DE CRÉDITO")
    print("Simulación de un sistema de decisión basado en múltiples criterios")
    
    # Opción: ingresar datos manualmente o usar ejemplo
    opcion = input("\n¿Deseas usar datos de ejemplo? (sí/no): ").lower()
    
    if opcion != "sí":
        print("\n📝 INGRESA LOS DATOS DEL SOLICITANTE:")
        solicitante["nombre"] = input("Nombre completo: ")
        solicitante["edad"] = int(input("Edad: "))
        solicitante["ingresos_mensuales"] = float(input("Ingresos mensuales (MXN): "))
        solicitante["gastos_mensuales"] = float(input("Gastos mensuales (MXN): "))
        solicitante["deudas_totales"] = float(input("Deudas totales (MXN): "))
        solicitante["antiguedad_laboral"] = float(input("Antigüedad laboral (años): "))
        solicitante["tipo_empleo"] = input("Tipo de empleo (formal/independiente): ")
        solicitante["monto_solicitado"] = float(input("Monto solicitado (MXN): "))
        tiene_garantia = input("¿Ofrece garantía? (sí/no): ").lower()
        solicitante["tiene_garantia"] = tiene_garantia == "sí"
        
        if solicitante["tiene_garantia"]:
            solicitante["valor_garantia"] = float(input("Valor de la garantía (MXN): "))
    
    # Ejecutar evaluación
    resultado = evaluador.evaluar_solicitud(solicitante)
    evaluador.mostrar_reporte(resultado)
    
    # Mostrar estadísticas del historial
    print(f"\n📊 Estadísticas del sistema:")
    print(f"   Total de evaluaciones realizadas: {len(evaluador.historial_evaluaciones)}")
    
    if len(evaluador.historial_evaluaciones) > 1:
        puntajes = [e["puntaje_total"] for e in evaluador.historial_evaluaciones]
        print(f"   Promedio de puntajes: {sum(puntajes)/len(puntajes):.2f}")
    
    print("\n💡 ¡Felicidades! Has completado el proyecto integrador.")
    print("   Este sistema utiliza algoritmos de decisión basados en múltiples criterios.")
    print("   Puedes extenderlo agregando más criterios o conectándolo a una base de datos.")

if __name__ == "__main__":
    main()
```

---

## 📚 Resumen de Conceptos Clave por Fase

| Fase | Conceptos de Programación | Relación con IA |
|------|--------------------------|-----------------|
| **Apertura** | Variables, tipos de datos, input/output, condicionales simples | Base del razonamiento lógico en sistemas de IA |
| **Desarrollo** | Condicionales anidadas, funciones, diccionarios, manejo de errores | Sistemas basados en reglas, árboles de decisión |
| **Cierre** | Programación orientada a objetos, modularidad, persistencia de datos | Simulación de sistemas expertos, evaluación multicriterio |

Estos ejemplos están diseñados para que los estudiantes puedan:
1. **Comprender** la lógica detrás de cada algoritmo
2. **Modificar** y experimentar con los parámetros
3. **Extender** las funcionalidades según sus propios proyectos
4. **Documentar** su código en GitHub como evidencia de aprendizaje

¿Te gustaría que profundice en algún ejemplo específico o que agregue más variantes para alguna de las prácticas?
