Excelente. A continuación, te presento **2 ejemplos resueltos en Python para cada tema** de la Segunda Secuencia Didáctica, alineados con el enfoque de **pensamiento sistémico** y el **Subtema 1.2: Presentación de propuestas de solución con IA**.

---

# 🟢 FASE DE APERTURA (6 Horas)
## Tema: Estructura de Propuesta Técnica y Pensamiento Sistémico

---

### 📌 **Tema 1: Estructura de una Propuesta Técnica**

#### **Ejemplo 1: Propuesta de Asistente de Gestión de Inventarios**

```python
"""
=============================================
PROPUESTA TÉCNICA - SISTEMA DE GESTIÓN DE INVENTARIOS CON IA
=============================================
Estructura profesional de una propuesta técnica
"""

class PropuestaTecnica:
    """
    Clase que modela la estructura formal de una propuesta técnica
    para presentación a superiores o clientes
    """
    
    def __init__(self, titulo, autor, fecha):
        self.titulo = titulo
        self.autor = autor
        self.fecha = fecha
        self.secciones = {}
    
    def agregar_resumen_ejecutivo(self, texto):
        """Sección 1: Resumen ejecutivo - visión general del proyecto"""
        self.secciones["resumen_ejecutivo"] = {
            "contenido": texto,
            "propósito": "Presentar de manera concisa el problema y solución propuesta"
        }
    
    def agregar_planteamiento_problema(self, problema, causas, consecuencias):
        """Sección 2: Planteamiento del problema - descripción detallada"""
        self.secciones["planteamiento_problema"] = {
            "problema": problema,
            "causas": causas,
            "consecuencias": consecuencias
        }
    
    def agregar_objetivos(self, objetivo_general, objetivos_especificos):
        """Sección 3: Objetivos - qué se espera lograr"""
        self.secciones["objetivos"] = {
            "general": objetivo_general,
            "especificos": objetivos_especificos
        }
    
    def agregar_recursos(self, humanos, tecnicos, financieros):
        """Sección 4: Recursos - qué se necesita para implementar"""
        self.secciones["recursos"] = {
            "humanos": humanos,
            "tecnicos": tecnicos,
            "financieros": financieros
        }
    
    def agregar_conclusion(self, texto, impacto_esperado):
        """Sección 5: Conclusión - valor agregado y beneficios"""
        self.secciones["conclusion"] = {
            "texto": texto,
            "impacto_esperado": impacto_esperado
        }
    
    def generar_propuesta(self):
        """Genera la propuesta completa con formato estructurado"""
        print("\n" + "="*70)
        print(f"📄 PROPUESTA TÉCNICA: {self.titulo}")
        print(f"👤 Autor: {self.autor}")
        print(f"📅 Fecha: {self.fecha}")
        print("="*70)
        
        for seccion, contenido in self.secciones.items():
            print(f"\n{'='*70}")
            print(f"📌 {seccion.upper().replace('_', ' ')}")
            print('='*70)
            
            if isinstance(contenido, dict):
                for clave, valor in contenido.items():
                    if isinstance(valor, list):
                        print(f"\n   {clave.replace('_', ' ').title()}:")
                        for item in valor:
                            print(f"     • {item}")
                    else:
                        print(f"\n   {clave.replace('_', ' ').title()}: {valor}")
            else:
                print(contenido)
        
        print("\n" + "="*70)
        print("✅ Propuesta generada exitosamente.")
        print("="*70)

# ========== EJEMPLO DE USO ==========
if __name__ == "__main__":
    # Crear una propuesta para un sistema de inventarios
    propuesta = PropuestaTecnica(
        titulo="Sistema de Gestión de Inventarios con Predicción de Demanda IA",
        autor="Ing. Ana Martínez",
        fecha="30 de marzo de 2026"
    )
    
    # 1. Resumen ejecutivo
    propuesta.agregar_resumen_ejecutivo(
        "Se propone implementar un sistema basado en Inteligencia Artificial "
        "para optimizar la gestión de inventarios, reduciendo mermas en un 30% "
        "y mejorando la disponibilidad de productos mediante predicción de demanda."
    )
    
    # 2. Planteamiento del problema
    propuesta.agregar_planteamiento_problema(
        problema="Exceso de inventario en productos de baja rotación y desabasto en productos de alta demanda.",
        causas=[
            "Falta de datos históricos de ventas",
            "Decisiones basadas en intuición",
            "Ausencia de herramientas predictivas"
        ],
        consecuencias=[
            "Pérdidas por productos caducados: $500,000 anuales",
            "Ventas perdidas por desabasto: 15% de ingresos potenciales",
            "Incremento en costos de almacenamiento"
        ]
    )
    
    # 3. Objetivos
    propuesta.agregar_objetivos(
        objetivo_general="Implementar un sistema predictivo de inventarios que reduzca mermas y optimice niveles de stock.",
        objetivos_especificos=[
            "Desarrollar modelo predictivo de demanda con 85% de precisión",
            "Implementar alertas automáticas de reabastecimiento",
            "Reducir costos de almacenamiento en 20%",
            "Capacitar al personal en uso del sistema"
        ]
    )
    
    # 4. Recursos
    propuesta.agregar_recursos(
        humanos=[
            "1 Líder de proyecto (Tiempo parcial)",
            "2 Desarrolladores Python (Full-time, 3 meses)",
            "1 Analista de datos (Full-time, 2 meses)",
            "1 Capacitador (1 semana)"
        ],
        tecnicos=[
            "Servidor Cloud (AWS/GCP) - $15,000/mes",
            "Base de datos PostgreSQL",
            "Bibliotecas Python: pandas, scikit-learn, flask",
            "Herramienta de visualización: Power BI"
        ],
        financieros=[
            "Inversión inicial: $450,000 MXN",
            "Costo operativo mensual: $35,000 MXN",
            "ROI proyectado: 145% en 12 meses"
        ]
    )
    
    # 5. Conclusión
    propuesta.agregar_conclusion(
        texto="La implementación de este sistema permitirá a la empresa tomar decisiones "
              "basadas en datos, optimizando recursos y mejorando la competitividad en el mercado.",
        impacto_esperado=[
            "Reducción del 30% en mermas",
            "Incremento del 12% en ventas por mejor disponibilidad",
            "Recuperación de inversión en 8 meses"
        ]
    )
    
    # Generar la propuesta completa
    propuesta.generar_propuesta()
```

---

#### **Ejemplo 2: Propuesta de Asistente Virtual para Atención al Cliente**

```python
"""
=============================================
PROPUESTA TÉCNICA - ASISTENTE VIRTUAL PARA ATENCIÓN AL CLIENTE
=============================================
Estructura profesional con enfoque en beneficios tangibles
"""

from datetime import datetime
from typing import Dict, List

class PropuestaAsistenteVirtual:
    """
    Modelo de propuesta para implementación de chatbot/ asistente virtual
    con métricas de impacto cuantificables
    """
    
    def __init__(self, nombre_proyecto, empresa, responsable):
        self.nombre_proyecto = nombre_proyecto
        self.empresa = empresa
        self.responsable = responsable
        self.fecha = datetime.now().strftime("%d/%m/%Y")
        self.metricas_actuales = {}
        self.metricas_proyectadas = {}
    
    def diagnosticar_situacion_actual(self, tiempo_espera_min, costo_atencion, 
                                       horas_operacion, tasa_abandono):
        """Análisis de la situación actual (línea base)"""
        self.metricas_actuales = {
            "tiempo_espera_promedio": tiempo_espera_min,
            "costo_por_atencion": costo_atencion,
            "horas_operacion_dia": horas_operacion,
            "tasa_abandono": tasa_abandono,
            "satisfaccion_actual": 65  # % base
        }
    
    def definir_solucion(self, alcance, funcionalidades):
        """Define la solución propuesta y sus capacidades"""
        self.alcance = alcance
        self.funcionalidades = funcionalidades
    
    def proyectar_impacto(self):
        """Calcula métricas proyectadas basadas en datos de referencia"""
        self.metricas_proyectadas = {
            "tiempo_espera_promedio": self.metricas_actuales["tiempo_espera_promedio"] * 0.1,
            "costo_por_atencion": self.metricas_actuales["costo_por_atencion"] * 0.3,
            "horas_operacion_dia": 24,  # Atención 24/7
            "tasa_abandono": self.metricas_actuales["tasa_abandono"] * 0.4,
            "satisfaccion_proyectada": 88,  # %
            "atencion_automatizada": 75  # % de consultas resueltas sin intervención humana
        }
    
    def calcular_roi(self, inversion, plazo_meses=12):
        """Calcula el retorno de inversión estimado"""
        ahorro_mensual = (
            (self.metricas_actuales["costo_por_atencion"] * 1000) -  # Asumiendo 1000 consultas/mes
            (self.metricas_proyectadas["costo_por_atencion"] * 1000 * 0.25)  # Solo 25% requiere humano
        )
        
        ahorro_total = ahorro_mensual * plazo_meses
        roi = ((ahorro_total - inversion) / inversion) * 100
        
        return {
            "ahorro_mensual": ahorro_mensual,
            "ahorro_anual": ahorro_total,
            "inversion": inversion,
            "roi_porcentaje": roi,
            "recuperacion_meses": inversion / ahorro_mensual if ahorro_mensual > 0 else 0
        }
    
    def generar_documento(self):
        """Genera el documento formal de la propuesta"""
        print("\n" + "█"*70)
        print(f"📋 PROPUESTA DE SOLUCIÓN CON INTELIGENCIA ARTIFICIAL")
        print(f"   {self.nombre_proyecto}")
        print("█"*70)
        
        print(f"\n📌 DATOS GENERALES")
        print(f"   Empresa: {self.empresa}")
        print(f"   Responsable: {self.responsable}")
        print(f"   Fecha: {self.fecha}")
        
        print(f"\n📌 RESÚMEN EJECUTIVO")
        print(f"   Se propone implementar un asistente virtual basado en IA para ")
        print(f"   optimizar la atención al cliente, reduciendo tiempos de espera ")
        print(f"   en un 90% y costos operativos en un 70%.")
        
        print(f"\n📌 SITUACIÓN ACTUAL VS PROYECTADA")
        print(f"\n   {'Métrica':<25} {'Actual':<15} {'Proyectada':<15} {'Mejora':<15}")
        print(f"   {'-'*65}")
        
        for metric in self.metricas_actuales:
            actual = self.metricas_actuales.get(metric, 0)
            proyectada = self.metricas_proyectadas.get(metric, 0)
            if isinstance(actual, (int, float)) and isinstance(proyectada, (int, float)):
                mejora = ((actual - proyectada) / actual * 100) if actual > 0 else 0
                unidad = "min" if "tiempo" in metric else "%" if "tasa" in metric else "$" if "costo" in metric else ""
                print(f"   {metric.replace('_',' ').title():<25} {actual}{unidad:<12} {proyectada}{unidad:<12} {mejora:.0f}% mejora")
        
        print(f"\n📌 ALCANCE DE LA SOLUCIÓN")
        print(f"   {self.alcance}")
        
        print(f"\n📌 FUNCIONALIDADES")
        for i, func in enumerate(self.funcionalidades, 1):
            print(f"   {i}. {func}")
        
        # Calcular y mostrar ROI
        roi_data = self.calcular_roi(inversion=350000)
        print(f"\n📌 ANÁLISIS DE INVERSIÓN Y RETORNO")
        print(f"   Inversión estimada: ${roi_data['inversion']:,.0f} MXN")
        print(f"   Ahorro mensual proyectado: ${roi_data['ahorro_mensual']:,.0f} MXN")
        print(f"   Ahorro anual: ${roi_data['ahorro_anual']:,.0f} MXN")
        print(f"   ROI proyectado: {roi_data['roi_porcentaje']:.0f}%")
        print(f"   Periodo de recuperación: {roi_data['recuperacion_meses']:.1f} meses")
        
        print(f"\n📌 CONCLUSIÓN Y RECOMENDACIÓN")
        print(f"   La implementación del asistente virtual representa una oportunidad ")
        print(f"   estratégica para mejorar la experiencia del cliente mientras se ")
        print(f"   reducen costos operativos. Se recomienda iniciar con un piloto ")
        print(f"   de 3 meses en el área de atención al cliente.")
        
        print("\n" + "█"*70)
        print("✅ Propuesta lista para presentación a superiores.")
        print("█"*70)

# ========== EJEMPLO DE USO ==========
if __name__ == "__main__":
    propuesta = PropuestaAsistenteVirtual(
        nombre_proyecto="ASISTENTE VIRTUAL IA - SERVICIO AL CLIENTE 24/7",
        empresa="Corporativo ABC S.A. de C.V.",
        responsable="Departamento de Innovación Tecnológica"
    )
    
    # Diagnosticar situación actual
    propuesta.diagnosticar_situacion_actual(
        tiempo_espera_min=15,
        costo_atencion=85,  # $ por consulta atendida
        horas_operacion=10,
        tasa_abandono=35  # % de clientes que cuelgan antes de ser atendidos
    )
    
    # Definir solución
    propuesta.definir_solucion(
        alcance="Atención al cliente en canales digitales: WhatsApp, Web Chat y Messenger",
        funcionalidades=[
            "Respuesta automática a preguntas frecuentes",
            "Escalamiento inteligente a agente humano cuando sea necesario",
            "Agendamiento automático de citas y servicios",
            "Análisis de sentimiento para priorizar casos urgentes",
            "Reportes automáticos de métricas de atención"
        ]
    )
    
    # Proyectar impacto
    propuesta.proyectar_impacto()
    
    # Generar documento
    propuesta.generar_documento()
```

---

## 🟡 FASE DE DESARROLLO (26 Horas)

---

### 📌 **Unidad 1: Pensamiento Sistémico y Diagramación (10 h)**

#### **Ejemplo 1: Diagrama Sistémico de un Sistema de Recomendación**

```python
"""
=============================================
PENSAMIENTO SISTÉMICO - SISTEMA DE RECOMENDACIÓN
=============================================
Modelado de entradas, procesos y salidas en un sistema de IA
"""

class DiagramaSistemico:
    """
    Representa un diagrama sistémico que modela las interacciones
    de un sistema basado en IA
    """
    
    def __init__(self, nombre_sistema):
        self.nombre_sistema = nombre_sistema
        self.entradas = []
        self.procesos = []
        self.salidas = []
        self.retroalimentacion = []
        self.subsistemas = []
    
    def agregar_entrada(self, nombre, tipo, fuente):
        """Define una entrada al sistema"""
        self.entradas.append({
            "nombre": nombre,
            "tipo": tipo,  # datos, energía, recurso, etc.
            "fuente": fuente
        })
    
    def agregar_proceso(self, nombre, descripcion, algoritmo):
        """Define un proceso dentro del sistema"""
        self.procesos.append({
            "nombre": nombre,
            "descripcion": descripcion,
            "algoritmo": algoritmo
        })
    
    def agregar_salida(self, nombre, tipo, destino):
        """Define una salida del sistema"""
        self.salidas.append({
            "nombre": nombre,
            "tipo": tipo,
            "destino": destino
        })
    
    def agregar_retroalimentacion(self, origen, destino, criterio):
        """Define bucles de retroalimentación"""
        self.retroalimentacion.append({
            "origen": origen,
            "destino": destino,
            "criterio": criterio
        })
    
    def simular_flujo(self, datos_entrada):
        """
        Simula el flujo de información a través del sistema
        Demuestra cómo los datos se transforman en valor
        """
        print("\n" + "="*70)
        print(f"🔄 DIAGRAMA SISTÉMICO: {self.nombre_sistema}")
        print("="*70)
        
        # Mostrar entradas
        print("\n📥 ENTRADAS AL SISTEMA:")
        for entrada in self.entradas:
            print(f"   • {entrada['nombre']} ({entrada['tipo']}) ← {entrada['fuente']}")
        
        # Simular procesamiento
        print("\n⚙️ PROCESAMIENTO:")
        datos_procesados = datos_entrada.copy()
        
        for proceso in self.procesos:
            print(f"\n   🔧 {proceso['nombre']}")
            print(f"      📝 {proceso['descripcion']}")
            
            # Simular aplicación del algoritmo
            if proceso['algoritmo'] == "filtrado_colaborativo":
                # Simular recomendación basada en usuarios similares
                datos_procesados['recomendaciones'] = [
                    "Producto A (basado en usuarios similares)",
                    "Producto B (alta probabilidad de interés)"
                ]
                print(f"      ✅ Generadas {len(datos_procesados['recomendaciones'])} recomendaciones")
            
            elif proceso['algoritmo'] == "clasificacion":
                # Simular clasificación de datos
                datos_procesados['clasificacion'] = "Alto interés"
                print(f"      ✅ Clasificación completada: {datos_procesados['clasificacion']}")
            
            elif proceso['algoritmo'] == "analisis_sentimiento":
                # Simular análisis de sentimiento
                datos_procesados['sentimiento'] = 0.85
                print(f"      ✅ Sentimiento positivo detectado (score: 0.85)")
        
        # Mostrar salidas
        print("\n📤 SALIDAS DEL SISTEMA:")
        for salida in self.salidas:
            if salida['nombre'] in datos_procesados:
                print(f"   • {salida['nombre']}: {datos_procesados[salida['nombre']]} → {salida['destino']}")
        
        # Mostrar retroalimentación
        if self.retroalimentacion:
            print("\n🔄 BUCLES DE RETROALIMENTACIÓN:")
            for fb in self.retroalimentacion:
                print(f"   • {fb['origen']} → {fb['destino']} (criterio: {fb['criterio']})")
        
        return datos_procesados
    
    def visualizar_estructura(self):
        """Genera una representación textual de la estructura del sistema"""
        print("\n" + "="*70)
        print(f"📊 ESTRUCTURA SISTÉMICA: {self.nombre_sistema}")
        print("="*70)
        
        print("\n┌─────────────────────────────────────────────────────────┐")
        print("│                    ENTRADAS                             │")
        print("├─────────────────────────────────────────────────────────┤")
        for e in self.entradas:
            print(f"│  • {e['nombre']:<45} │")
        
        print("├─────────────────────────────────────────────────────────┤")
        print("│                    PROCESOS                             │")
        print("├─────────────────────────────────────────────────────────┤")
        for p in self.procesos:
            print(f"│  • {p['nombre']:<45} │")
        
        print("├─────────────────────────────────────────────────────────┤")
        print("│                    SALIDAS                              │")
        print("├─────────────────────────────────────────────────────────┤")
        for s in self.salidas:
            print(f"│  • {s['nombre']:<45} │")
        
        print("├─────────────────────────────────────────────────────────┤")
        print("│              RETROALIMENTACIÓN                          │")
        print("├─────────────────────────────────────────────────────────┤")
        for f in self.retroalimentacion:
            print(f"│  • {f['origen']} → {f['destino']:<35} │")
        
        print("└─────────────────────────────────────────────────────────┘")

# ========== EJEMPLO DE USO ==========
if __name__ == "__main__":
    # Crear diagrama para un sistema de recomendación
    sistema = DiagramaSistemico("Sistema de Recomendación de Contenido")
    
    # Definir entradas
    sistema.agregar_entrada("Historial del usuario", "datos", "Base de datos de usuarios")
    sistema.agregar_entrada("Preferencias explícitas", "datos", "Perfil del usuario")
    sistema.agregar_entrada("Catálogo de contenido", "datos", "Base de datos de productos")
    sistema.agregar_entrada("Interacciones de otros usuarios", "datos", "Registro de comportamiento")
    
    # Definir procesos
    sistema.agregar_proceso(
        "Filtrado colaborativo",
        "Encuentra usuarios similares basado en patrones de consumo",
        "filtrado_colaborativo"
    )
    sistema.agregar_proceso(
        "Clasificación de preferencias",
        "Clasifica al usuario en segmentos de interés",
        "clasificacion"
    )
    sistema.agregar_proceso(
        "Generación de recomendaciones",
        "Combina múltiples fuentes para generar lista personalizada",
        "ranking"
    )
    
    # Definir salidas
    sistema.agregar_salida("Recomendaciones personalizadas", "lista", "Interfaz de usuario")
    sistema.agregar_salida("Reporte de engagement", "métrica", "Dashboard de analítica")
    
    # Definir retroalimentación
    sistema.agregar_retroalimentacion(
        "Interacción del usuario con recomendaciones",
        "Actualización de perfil",
        "Mejora continua del modelo"
    )
    
    # Visualizar estructura
    sistema.visualizar_estructura()
    
    # Simular flujo con datos de ejemplo
    datos_ejemplo = {
        "usuario_id": 12345,
        "historial": ["acción", "ciencia ficción", "acción"],
        "preferencias": ["acción", "thriller"],
        "tiempo_sesion": 45
    }
    
    resultado = sistema.simular_flujo(datos_ejemplo)
    
    print("\n" + "="*70)
    print("💡 REFLEXIÓN SISTÉMICA:")
    print("   Este sistema demuestra cómo las entradas se transforman")
    print("   mediante procesos algorítmicos para generar valor.")
    print("   Los bucles de retroalimentación permiten la mejora continua.")
```

---

#### **Ejemplo 2: Análisis Sistémico de un Problema Organizacional**

```python
"""
=============================================
PENSAMIENTO SISTÉMICO - ANÁLISIS DE PROBLEMA ORGANIZACIONAL
=============================================
Identificación de causas raíz, subsistemas e intervenciones de IA
"""

class AnalisisSistemico:
    """
    Herramienta para analizar problemas desde una perspectiva sistémica
    e identificar puntos de intervención para soluciones con IA
    """
    
    def __init__(self, problema, contexto):
        self.problema = problema
        self.contexto = contexto
        self.causas = []
        self.consecuencias = []
        self.subsistemas_afectados = []
        self.intervenciones_ia = []
    
    def identificar_causas_raiz(self, causas):
        """Identifica causas estructurales del problema"""
        self.causas = causas
    
    def mapear_consecuencias(self, consecuencias):
        """Mapea efectos en cascada del problema"""
        self.consecuencias = consecuencias
    
    def identificar_subsistemas(self, subsistemas):
        """Identifica áreas o componentes afectados"""
        self.subsistemas_afectados = subsistemas
    
    def proponer_intervenciones_ia(self, intervenciones):
        """Propone soluciones basadas en IA con enfoque sistémico"""
        self.intervenciones_ia = intervenciones
    
    def generar_analisis(self):
        """Genera análisis completo con recomendaciones"""
        print("\n" + "█"*70)
        print(f"🔍 ANÁLISIS SISTÉMICO DEL PROBLEMA")
        print(f"   {self.problema}")
        print("█"*70)
        
        print(f"\n📌 CONTEXTO")
        print(f"   {self.contexto}")
        
        print(f"\n📌 CAUSAS RAÍZ (ENFOQUE SISTÉMICO)")
        for i, causa in enumerate(self.causas, 1):
            print(f"   {i}. {causa}")
        
        print(f"\n📌 EFECTOS EN CADENA")
        for i, cons in enumerate(self.consecuencias, 1):
            print(f"   {i}. {cons}")
        
        print(f"\n📌 SUBSISTEMAS AFECTADOS")
        for sub in self.subsistemas_afectados:
            print(f"   • {sub['nombre']}: {sub['impacto']}")
        
        print(f"\n🤖 INTERVENCIONES BASADAS EN IA")
        print("   " + "-"*50)
        for i, interv in enumerate(self.intervenciones_ia, 1):
            print(f"\n   {i}. {interv['nombre']}")
            print(f"      📍 Punto de intervención: {interv['punto_intervencion']}")
            print(f"      🎯 Cómo funciona: {interv['mecanismo']}")
            print(f"      📊 Impacto esperado: {interv['impacto']}")
        
        print("\n" + "█"*70)
        print("✅ Análisis sistémico completado")
    
    def evaluar_interdependencias(self):
        """Analiza cómo los subsistemas interactúan entre sí"""
        print("\n🔄 ANÁLISIS DE INTERDEPENDENCIAS")
        print("   " + "="*50)
        
        relaciones = []
        for i, sub_a in enumerate(self.subsistemas_afectados):
            for sub_b in self.subsistemas_afectados[i+1:]:
                relaciones.append(f"{sub_a['nombre']} ↔ {sub_b['nombre']}")
        
        for rel in relaciones:
            print(f"   • {rel}")
        
        return relaciones

# ========== EJEMPLO DE USO ==========
if __name__ == "__main__":
    # Crear análisis para problema específico
    analisis = AnalisisSistemico(
        problema="Alta rotación de personal en área de atención al cliente",
        contexto="Empresa de telecomunicaciones con 500 agentes de servicio al cliente. "
                 "Rotación del 45% anual, afectando calidad de servicio y costos de capacitación."
    )
    
    # Identificar causas raíz
    analisis.identificar_causas_raiz([
        "Carga de trabajo excesiva por alta demanda de llamadas",
        "Tareas repetitivas que generan desmotivación",
        "Falta de herramientas para resolver casos complejos rápidamente",
        "Horarios rígidos sin flexibilidad",
        "Retroalimentación insuficiente sobre desempeño"
    ])
    
    # Mapear consecuencias
    analisis.mapear_consecuencias([
        "Disminución de calidad en atención al cliente",
        "Incremento de quejas por tiempos de espera",
        "Pérdida de conocimiento institucional",
        "Costos crecientes de reclutamiento y capacitación",
        "Sobrecarga en agentes restantes"
    ])
    
    # Identificar subsistemas afectados
    analisis.identificar_subsistemas([
        {"nombre": "Recursos Humanos", "impacto": "Alta demanda de reclutamiento"},
        {"nombre": "Operaciones", "impacto": "Baja productividad y calidad"},
        {"nombre": "Tecnología", "impacto": "Herramientas subutilizadas"},
        {"nombre": "Finanzas", "impacto": "Incremento de costos operativos"},
        {"nombre": "Experiencia Cliente", "impacto": "Baja satisfacción (NPS en descenso)"}
    ])
    
    # Proponer intervenciones con IA
    analisis.proponer_intervenciones_ia([
        {
            "nombre": "Asistente Virtual Inteligente (Chatbot)",
            "punto_intervencion": "Primer contacto con cliente",
            "mecanismo": "IA resuelve consultas simples (60-70% del volumen) automáticamente",
            "impacto": "Reduce carga de agentes en tareas repetitivas, mejora tiempos de respuesta"
        },
        {
            "nombre": "Sistema de Asistencia a Agentes (Agent Assist)",
            "punto_intervencion": "Durante la interacción con cliente",
            "mecanismo": "IA sugiere respuestas, accede a conocimiento base y predice intención del cliente",
            "impacto": "Reduce tiempo por llamada 30%, aumenta resolución en primer contacto"
        },
        {
            "nombre": "Analítica Predictiva de Rotación",
            "punto_intervencion": "Gestión de talento",
            "mecanismo": "Modelo IA identifica agentes en riesgo de renuncia y sugiere acciones preventivas",
            "impacto": "Reduce rotación 20% mediante intervención temprana"
        },
        {
            "nombre": "Optimización de Horarios con IA",
            "punto_intervencion": "Planificación operativa",
            "mecanismo": "Algoritmos predicen demanda y asignan horarios flexibles equilibrando carga",
            "impacto": "Mejora satisfacción laboral, reduce burnout"
        }
    ])
    
    # Generar análisis
    analisis.generar_analisis()
    
    # Evaluar interdependencias
    analisis.evaluar_interdependencias()
    
    print("\n💡 CONCLUSIÓN SISTÉMICA:")
    print("   Las intervenciones con IA no actúan de forma aislada.")
    print("   Al reducir carga operativa (Tecnología → Operaciones),")
    print("   se mejora satisfacción laboral (RRHH) y se reducen costos (Finanzas),")
    print("   generando un efecto positivo en todo el sistema organizacional.")
```

---

### 📌 **Unidad 2: Laboratorio de Python Avanzado (16 h)**

---

#### **Práctica Demostrativa (2h): Decisiones Múltiples y Validación de Datos**

#### **Ejemplo 1: Clasificador de Riesgo con Decisiones Múltiples**

```python
"""
=============================================
PRÁCTICA DEMOSTRATIVA - CLASIFICADOR DE RIESGO
=============================================
Uso de decisiones múltiples (if-elif-else) y validación de datos
"""

import re
from typing import Dict, Tuple, Optional

class ClasificadorRiesgo:
    """
    Sistema que evalúa múltiples variables para clasificar niveles de riesgo
    Demuestra el uso de estructuras condicionales anidadas y validación robusta
    """
    
    def __init__(self):
        self.historial_evaluaciones = []
        
    def validar_entrada(self, valor, tipo_esperado, minimo=None, maximo=None):
        """
        Valida datos de entrada para prevenir errores
        Implementa validación robusta de tipos y rangos
        """
        if tipo_esperado == "int":
            try:
                valor_int = int(valor)
                if minimo is not None and valor_int < minimo:
                    return False, f"El valor debe ser >= {minimo}"
                if maximo is not None and valor_int > maximo:
                    return False, f"El valor debe ser <= {maximo}"
                return True, valor_int
            except ValueError:
                return False, "Debe ingresar un número entero válido"
        
        elif tipo_esperado == "float":
            try:
                valor_float = float(valor)
                if minimo is not None and valor_float < minimo:
                    return False, f"El valor debe ser >= {minimo}"
                if maximo is not None and valor_float > maximo:
                    return False, f"El valor debe ser <= {maximo}"
                return True, valor_float
            except ValueError:
                return False, "Debe ingresar un número válido"
        
        elif tipo_esperado == "str":
            valor_str = str(valor).strip()
            if not valor_str:
                return False, "El campo no puede estar vacío"
            return True, valor_str
        
        return False, "Tipo de dato no soportado"
    
    def evaluar_riesgo(self, datos: Dict) -> Tuple[int, str, Dict]:
        """
        Evalúa múltiples variables usando estructura de decisiones
        Retorna puntaje, nivel de riesgo y desglose
        """
        puntajes = {}
        observaciones = []
        
        # ========== VARIABLE 1: INGRESOS ==========
        ingresos = datos.get("ingresos_mensuales", 0)
        
        if ingresos >= 50000:
            puntajes["ingresos"] = 100
            observaciones.append("Ingresos altos: excelente capacidad financiera")
        elif ingresos >= 30000:
            puntajes["ingresos"] = 70
            observaciones.append("Ingresos medios-altos: buena capacidad de pago")
        elif ingresos >= 15000:
            puntajes["ingresos"] = 40
            observaciones.append("Ingresos medios: capacidad de pago moderada")
        elif ingresos >= 8000:
            puntajes["ingresos"] = 20
            observaciones.append("Ingresos bajos: capacidad de pago limitada
