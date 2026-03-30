Excelente. A continuación, te presento los **5 ejemplos completamente funcionales en Python**, cada uno con su respectivo planteamiento del problema y código resuelto. Estos ejemplos implementan un sistema de **Procesamiento de Lenguaje Natural (PLN)** básico que detecta intenciones y genera respuestas apropiadas.

---

## 📌 **EJEMPLO 1: Consulta de Capital de País**

### **Planteamiento del Problema**
Desarrollar un asistente virtual que pueda identificar cuando un usuario pregunta por la capital de un país y responder con información relevante. El sistema debe detectar la intención de "solicitud de dato geográfico" y proporcionar una respuesta enriquecida con contexto cultural.

```python
"""
=============================================
EJEMPLO 1: ASISTENTE DE CAPITALES DEL MUNDO
=============================================
Intención: Solicitud de dato geográfico
Funcionalidad: Detecta preguntas sobre capitales y responde con información
"""

import re
from typing import Dict, Tuple, Optional

class AsistenteCapitales:
    """
    Sistema especializado en responder preguntas sobre capitales de países
    Utiliza PLN básico con coincidencia de patrones
    """
    
    def __init__(self):
        # Base de conocimiento de capitales
        self.base_capitales = {
            "francia": {
                "capital": "París",
                "datos": "una ciudad conocida por su arte, moda, gastronomía y la Torre Eiffel"
            },
            "alemania": {
                "capital": "Berlín",
                "datos": "famosa por su historia, el Muro de Berlín y su vibrante escena cultural"
            },
            "españa": {
                "capital": "Madrid",
                "datos": "hogar del Museo del Prado y famosa por su vida nocturna y tapas"
            },
            "italia": {
                "capital": "Roma",
                "datos": "la Ciudad Eterna, conocida por el Coliseo y su increíble historia"
            },
            "méxico": {
                "capital": "Ciudad de México",
                "datos": "una metrópolis vibrante con rica historia azteca y colonial"
            },
            "argentina": {
                "capital": "Buenos Aires",
                "datos": "conocida como la París de América, famosa por el tango y su arquitectura europea"
            },
            "japón": {
                "capital": "Tokio",
                "datos": "una metrópolis futurista que combina tradición y tecnología"
            },
            "reino unido": {
                "capital": "Londres",
                "datos": "ciudad histórica con el Big Ben, el Támesis y una rica cultura"
            }
        }
        
        # Patrones para detectar preguntas sobre capitales
        self.patrones = [
            r"capital\s+(?:de\s+)?([a-záéíóúñ\s]+)",
            r"cu[áa]l\s+es\s+la\s+capital\s+(?:de\s+)?([a-záéíóúñ\s]+)",
            r"d[óo]nde\s+queda\s+la\s+capital\s+(?:de\s+)?([a-záéíóúñ\s]+)",
            r"qu[eé]\s+capital\s+tiene\s+([a-záéíóúñ\s]+)"
        ]
        
        self.historial_conversaciones = []
    
    def normalizar_texto(self, texto: str) -> str:
        """Normaliza el texto para mejor procesamiento"""
        texto = texto.lower().strip()
        texto = re.sub(r'[¿?¡!]', '', texto)
        return texto
    
    def extraer_pais(self, mensaje: str) -> Optional[str]:
        """Extrae el nombre del país de la pregunta"""
        mensaje_norm = self.normalizar_texto(mensaje)
        
        for patron in self.patrones:
            coincidencia = re.search(patron, mensaje_norm)
            if coincidencia:
                pais = coincidencia.group(1).strip()
                # Limpiar posibles artículos
                pais = re.sub(r'^(el|la|los|las)\s+', '', pais)
                return pais.lower()
        
        return None
    
    def detectar_intencion(self, mensaje: str) -> Dict:
        """Detecta la intención del mensaje"""
        mensaje_norm = self.normalizar_texto(mensaje)
        
        # Detectar si es pregunta de capital
        if any(re.search(patron, mensaje_norm) for patron in self.patrones):
            pais = self.extraer_pais(mensaje)
            return {
                "intencion": "solicitud_dato_geografico",
                "pais": pais,
                "confianza": 0.95 if pais else 0.70
            }
        
        return {
            "intencion": "no_reconocida",
            "pais": None,
            "confianza": 0.0
        }
    
    def generar_respuesta(self, mensaje: str) -> Tuple[str, Dict]:
        """Genera respuesta basada en la intención detectada"""
        
        # Detectar intención
        intencion = self.detectar_intencion(mensaje)
        
        if intencion["intencion"] == "solicitud_dato_geografico":
            pais = intencion["pais"]
            
            if not pais:
                return "No pude identificar de qué país quieres saber la capital. ¿Podrías especificarlo?", intencion
            
            # Buscar en base de conocimiento
            for nombre_pais, info in self.base_capitales.items():
                if pais in nombre_pais or nombre_pais in pais:
                    respuesta = f"La capital de {nombre_pais.title()} es {info['capital']}, {info['datos']}."
                    return respuesta, intencion
            
            # Si no se encuentra el país
            return f"Lo siento, no tengo información sobre la capital de '{pais}'. ¿Podrías verificar el nombre?", intencion
        
        return "Lo siento, no entendí tu pregunta. ¿Podrías reformularla?", intencion
    
    def iniciar_conversacion(self):
        """Inicia una conversación interactiva"""
        print("\n" + "="*60)
        print("🗺️  ASISTENTE DE CAPITALES - ¡Pregúntame sobre cualquier capital!")
        print("="*60)
        print("Ejemplos: '¿Cuál es la capital de Francia?' o 'Capital de México'")
        print("Escribe 'salir' para terminar la conversación.")
        print("-"*60)
        
        while True:
            usuario = input("\n👤 Tú: ").strip()
            
            if usuario.lower() in ["salir", "exit", "adiós", "chao"]:
                print("\n🤖 Asistente: ¡Hasta luego! Espero haberte ayudado.")
                break
            
            if not usuario:
                continue
            
            respuesta, intencion = self.generar_respuesta(usuario)
            
            # Registrar en historial
            self.historial_conversaciones.append({
                "usuario": usuario,
                "intencion": intencion["intencion"],
                "respuesta": respuesta
            })
            
            print(f"\n🤖 Asistente: {respuesta}")

# ========== EJECUCIÓN DEL ASISTENTE ==========
if __name__ == "__main__":
    asistente = AsistenteCapitales()
    
    # Modo interactivo
    asistente.iniciar_conversacion()
    
    # También se puede usar para consultas individuales
    print("\n" + "="*60)
    print("📋 PRUEBAS RÁPIDAS:")
    print("="*60)
    
    pruebas = [
        "¿Cuál es la capital de Francia?",
        "capital de Japón",
        "Dónde queda la capital de Italia",
        "Qué capital tiene Alemania"
    ]
    
    for prueba in pruebas:
        respuesta, _ = asistente.generar_respuesta(prueba)
        print(f"\n🔍 Pregunta: {prueba}")
        print(f"✨ Respuesta: {respuesta}")
```

---

## 📌 **EJEMPLO 2: Explicación de Fotosíntesis**

### **Planteamiento del Problema**
Crear un asistente educativo que pueda detectar cuando un usuario solicita explicaciones conceptuales sobre temas científicos, en particular sobre fotosíntesis, y responder con explicaciones claras y accesibles en lenguaje sencillo.

```python
"""
=============================================
EJEMPLO 2: ASISTENTE EDUCATIVO - EXPLICACIONES CIENTÍFICAS
=============================================
Intención: Solicitud de explicación conceptual
Funcionalidad: Explica conceptos científicos en términos simples
"""

import re
from typing import Dict, List, Tuple

class AsistenteEducativo:
    """
    Sistema que explica conceptos científicos y académicos
    Adapta el nivel de detalle según la solicitud del usuario
    """
    
    def __init__(self):
        # Base de conocimiento de conceptos
        self.conceptos = {
            "fotosíntesis": {
                "titulo": "Fotosíntesis",
                "simple": "La fotosíntesis es el proceso mediante el cual las plantas, algas y algunas bacterias convierten la luz solar, agua y dióxido de carbono en alimento (glucosa) y oxígeno. ¡Así es como las plantas fabrican su propio alimento!",
                "detallada": "La fotosíntesis es un proceso bioquímico que ocurre en los cloroplastos de las células vegetales. Consta de dos fases principales:\n\n"
                            "1. FASE LUMÍNICA: Ocurre en presencia de luz. La energía solar es capturada por la clorofila y convertida en energía química (ATP y NADPH), liberando oxígeno como subproducto.\n\n"
                            "2. FASE OSCURA (Ciclo de Calvin): No requiere luz directamente. Utiliza el ATP y NADPH de la fase lumínica para fijar dióxido de carbono (CO₂) y producir glucosa.\n\n"
                            "Ecuación general: 6CO₂ + 6H₂O + luz → C₆H₁₂O₆ + 6O₂"
            },
            "respiración celular": {
                "titulo": "Respiración Celular",
                "simple": "La respiración celular es el proceso mediante el cual las células obtienen energía de los nutrientes. Es como cuando tú comes para tener energía, pero a nivel microscópico.",
                "detallada": "La respiración celular es un conjunto de reacciones metabólicas que convierten la energía química de los nutrientes en ATP (adenosín trifosfato)."
            },
            "fotosíntesis en términos simples": {
                "titulo": "Fotosíntesis",
                "simple": "La fotosíntesis es el proceso mediante el cual las plantas convierten la luz solar, agua y dióxido de carbono en alimento y oxígeno.",
                "detallada": "La fotosíntesis es el proceso mediante el cual las plantas convierten la luz solar, agua y dióxido de carbono en alimento y oxígeno."
            }
        }
        
        # Patrones para detección de intenciones
        self.patrones_explicacion = [
            r"expl[ií]came?\s+([a-záéíóúñ\s]+)",
            r"qu[eé]\s+es\s+([a-záéíóúñ\s]+)",
            r"c[óo]mo\s+funciona\s+([a-záéíóúñ\s]+)",
            r"defin[eí]cion\s+de\s+([a-záéíóúñ\s]+)",
            r"qu[eé]\s+significa\s+([a-záéíóúñ\s]+)"
        ]
        
        self.palabras_clave = {
            "fotosíntesis": ["fotosíntesis", "plantas", "luz solar", "clorofila"],
            "respiración": ["respiración", "células", "energía"]
        }
        
        self.historial = []
    
    def normalizar_texto(self, texto: str) -> str:
        """Normaliza texto para procesamiento"""
        texto = texto.lower().strip()
        texto = re.sub(r'[¿?¡!]', '', texto)
        return texto
    
    def extraer_tema(self, mensaje: str) -> str:
        """Extrae el tema de la explicación solicitada"""
        mensaje_norm = self.normalizar_texto(mensaje)
        
        for patron in self.patrones_explicacion:
            coincidencia = re.search(patron, mensaje_norm)
            if coincidencia:
                tema = coincidencia.group(1).strip()
                # Limpiar artículos y palabras comunes
                tema = re.sub(r'^(el|la|los|las|un|una)\s+', '', tema)
                return tema
        
        # Si no se detecta patrón, buscar por palabras clave
        for tema_base, palabras in self.palabras_clave.items():
            if any(palabra in mensaje_norm for palabra in palabras):
                return tema_base
        
        return None
    
    def detectar_intencion(self, mensaje: str) -> Dict:
        """Detecta la intención del mensaje"""
        mensaje_norm = self.normalizar_texto(mensaje)
        
        # Detectar si es solicitud de explicación
        if any(re.search(patron, mensaje_norm) for patron in self.patrones_explicacion):
            tema = self.extraer_tema(mensaje)
            
            # Detectar si pide términos simples
            es_simple = "simple" in mensaje_norm or "fácil" in mensaje_norm or "sencillo" in mensaje_norm
            
            return {
                "intencion": "solicitud_explicacion_conceptual",
                "tema": tema,
                "nivel": "simple" if es_simple else "detallada",
                "confianza": 0.95 if tema else 0.70
            }
        
        return {
            "intencion": "no_reconocida",
            "tema": None,
            "nivel": None,
            "confianza": 0.0
        }
    
    def generar_respuesta(self, mensaje: str) -> Tuple[str, Dict]:
        """Genera respuesta educativa"""
        intencion = self.detectar_intencion(mensaje)
        
        if intencion["intencion"] == "solicitud_explicacion_conceptual":
            tema = intencion["tema"]
            nivel = intencion["nivel"]
            
            if not tema:
                return "¿Sobre qué tema te gustaría que te explique? Puedo ayudarte con fotosíntesis, respiración celular, y más.", intencion
            
            # Buscar el concepto
            concepto_encontrado = None
            for nombre_concepto, info in self.conceptos.items():
                if tema in nombre_concepto or nombre_concepto in tema:
                    concepto_encontrado = info
                    break
            
            if concepto_encontrado:
                # Si pide términos simples o el mensaje lo sugiere
                if nivel == "simple" or "términos simples" in mensaje.lower():
                    respuesta = concepto_encontrado["simple"]
                else:
                    respuesta = concepto_encontrado["detallada"]
                
                # Agregar pregunta de seguimiento para fomentar aprendizaje
                respuesta += "\n\n¿Te gustaría que profundice en algún aspecto específico?"
                return respuesta, intencion
            
            return f"Lo siento, aún no tengo información sobre '{tema}'. ¿Te gustaría que te explique sobre fotosíntesis o respiración celular?", intencion
        
        return "Hola, soy un asistente educativo. Puedo explicarte conceptos como la fotosíntesis, respiración celular, y más. ¿Qué te gustaría aprender?", intencion
    
    def iniciar_conversacion(self):
        """Modo conversación interactiva"""
        print("\n" + "="*60)
        print("📚 ASISTENTE EDUCATIVO - ¡Aprende con explicaciones claras!")
        print("="*60)
        print("Ejemplos: 'Explícame la fotosíntesis', '¿Qué es la respiración celular?'")
        print("Escribe 'salir' para terminar.")
        print("-"*60)
        
        while True:
            usuario = input("\n👤 Tú: ").strip()
            
            if usuario.lower() in ["salir", "exit", "adiós"]:
                print("\n🤖 Asistente: ¡Sigue aprendiendo! ¡Hasta pronto!")
                break
            
            if not usuario:
                continue
            
            respuesta, intencion = self.generar_respuesta(usuario)
            self.historial.append({"usuario": usuario, "respuesta": respuesta})
            
            print(f"\n🤖 Asistente: {respuesta}")

# ========== EJECUCIÓN ==========
if __name__ == "__main__":
    asistente = AsistenteEducativo()
    
    print("\n" + "="*60)
    print("📋 PRUEBAS DE CONSULTAS:")
    print("="*60)
    
    pruebas = [
        "Explícame la fotosíntesis en términos simples",
        "¿Qué es la fotosíntesis?",
        "Cómo funciona la fotosíntesis"
    ]
    
    for prueba in pruebas:
        respuesta, _ = asistente.generar_respuesta(prueba)
        print(f"\n🔍 {prueba}")
        print(f"✨ {respuesta[:200]}..." if len(respuesta) > 200 else f"✨ {respuesta}")
    
    # Modo interactivo
    asistente.iniciar_conversacion()
```

---

## 📌 **EJEMPLO 3: Resolución de Ecuaciones de Segundo Grado**

### **Planteamiento del Problema**
Implementar un asistente matemático que detecte solicitudes de procedimientos matemáticos, específicamente para resolver ecuaciones de segundo grado, mostrando la fórmula general y ofreciendo ejemplos paso a paso.

```python
"""
=============================================
EJEMPLO 3: ASISTENTE MATEMÁTICO - ECUACIONES DE SEGUNDO GRADO
=============================================
Intención: Solicitud de procedimiento matemático
Funcionalidad: Explica y resuelve ecuaciones cuadráticas paso a paso
"""

import re
import math
from typing import Dict, Tuple, List, Optional

class AsistenteMatematico:
    """
    Sistema especializado en resolver ecuaciones de segundo grado
    Detecta solicitudes y ofrece solución paso a paso
    """
    
    def __init__(self):
        self.historial = []
        
        # Patrones para detección de intenciones matemáticas
        self.patrones_ecuacion = [
            r"(?:resolver|solucionar)\s+(?:la\s+)?ecuaci[oó]n\s+([a-z0-9x²\^+\-\=\s]+)",
            r"(?:c[oó]mo\s+se\s+resuelve)\s+(?:una\s+)?ecuaci[oó]n\s+([a-z0-9x²\^+\-\=\s]+)",
            r"ecuaci[oó]n\s+de\s+segundo\s+grado",
            r"([a-z0-9x²\^+\-\=\s]+)\s*=\s*0",
            r"f[oó]rmula\s+general"
        ]
        
        # Patrones para detección de intención de procedimiento
        self.patrones_procedimiento = [
            r"c[oó]mo\s+se\s+(?:resuelve|hace|calcula)",
            r"paso\s+a\s+paso",
            r"ejemplo"
        ]
    
    def normalizar_texto(self, texto: str) -> str:
        """Normaliza texto para procesamiento"""
        texto = texto.lower().strip()
        texto = re.sub(r'[¿?¡!]', '', texto)
        # Normalizar potencias
        texto = texto.replace('²', '^2')
        return texto
    
    def extraer_ecuacion(self, mensaje: str) -> Optional[str]:
        """Extrae la ecuación del mensaje del usuario"""
        mensaje_norm = self.normalizar_texto(mensaje)
        
        for patron in self.patrones_ecuacion:
            coincidencia = re.search(patron, mensaje_norm)
            if coincidencia:
                if len(coincidencia.groups()) > 0:
                    ecuacion = coincidencia.group(1).strip()
                    if ecuacion:
                        return ecuacion
                return "ax^2 + bx + c = 0"  # Ecuación genérica
        
        return None
    
    def parsear_ecuacion(self, ecuacion: str) -> Tuple[float, float, float]:
        """
        Parsea una ecuación cuadrática y extrae coeficientes a, b, c
        Soporta formatos como: x^2 + 3x + 2 = 0, 2x^2 - 5x + 3 = 0
        """
        # Limpiar espacios
        ecuacion = ecuacion.replace(" ", "")
        
        # Separar lado izquierdo y derecho
        if "=" in ecuacion:
            izquierda, derecha = ecuacion.split("=")
            if derecha != "0":
                # Mover todo al lado izquierdo
                izquierda = f"{izquierda}-({derecha})"
        
        # Inicializar coeficientes
        a = b = c = 0.0
        
        # Buscar término x^2
        patron_a = r'([+-]?\d*\.?\d*)x\^2'
        match_a = re.search(patron_a, ecuacion)
        if match_a:
            coef = match_a.group(1)
            if coef == '' or coef == '+':
                a = 1.0
            elif coef == '-':
                a = -1.0
            else:
                a = float(coef)
        
        # Buscar término x
        patron_b = r'([+-]?\d*\.?\d*)x(?!\^)'
        # Encontrar todas las coincidencias, excluyendo x^2
        for match in re.finditer(patron_b, ecuacion):
            if not re.search(r'x\^2', match.group(0)):
                coef = match.group(1)
                if coef == '' or coef == '+':
                    b += 1.0
                elif coef == '-':
                    b += -1.0
                else:
                    b += float(coef)
        
        # Buscar término constante
        patron_c = r'([+-]?\d*\.?\d+)(?![x\d])'
        for match in re.finditer(patron_c, ecuacion):
            # Verificar que no sea parte de un coeficiente de x o x^2
            pos = match.start()
            if not (pos > 0 and ecuacion[pos-1] in 'x^'):
                coef = match.group(1)
                c += float(coef)
        
        return a, b, c
    
    def resolver_ecuacion(self, a: float, b: float, c: float) -> Dict:
        """Resuelve la ecuación usando la fórmula general"""
        resultado = {
            "a": a,
            "b": b,
            "c": c,
            "discriminante": None,
            "tipo_soluciones": None,
            "soluciones": [],
            "pasos": []
        }
        
        # Paso 1: Calcular discriminante
        discriminante = b**2 - 4*a*c
        resultado["discriminante"] = discriminante
        resultado["pasos"].append(f"Δ = b² - 4ac = ({b})² - 4({a})({c}) = {discriminante}")
        
        # Paso 2: Analizar discriminante
        if discriminante > 0:
            resultado["tipo_soluciones"] = "dos soluciones reales distintas"
            x1 = (-b + math.sqrt(discriminante)) / (2*a)
            x2 = (-b - math.sqrt(discriminante)) / (2*a)
            resultado["soluciones"] = [x1, x2]
            resultado["pasos"].append(f"x₁ = (-{b} + √{discriminante}) / (2·{a}) = {x1}")
            resultado["pasos"].append(f"x₂ = (-{b} - √{discriminante}) / (2·{a}) = {x2}")
            
        elif discriminante == 0:
            resultado["tipo_soluciones"] = "una solución real doble"
            x = -b / (2*a)
            resultado["soluciones"] = [x]
            resultado["pasos"].append(f"x = -{b} / (2·{a}) = {x}")
            
        else:
            resultado["tipo_soluciones"] = "dos soluciones complejas conjugadas"
            parte_real = -b / (2*a)
            parte_imaginaria = math.sqrt(abs(discriminante)) / (2*a)
            resultado["soluciones"] = [
                f"{parte_real} + {parte_imaginaria}i",
                f"{parte_real} - {parte_imaginaria}i"
            ]
            resultado["pasos"].append(f"x = (-{b} ± i√{abs(discriminante)}) / (2·{a})")
        
        return resultado
    
    def detectar_intencion(self, mensaje: str) -> Dict:
        """Detecta la intención del mensaje"""
        mensaje_norm = self.normalizar_texto(mensaje)
        
        # Detectar si es sobre procedimiento matemático
        es_procedimiento = any(re.search(p, mensaje_norm) for p in self.patrones_procedimiento)
        
        ecuacion = self.extraer_ecuacion(mensaje)
        
        if "ecuación" in mensaje_norm or "segundo grado" in mensaje_norm or ecuacion:
            return {
                "intencion": "solicitud_procedimiento_matematico",
                "ecuacion": ecuacion,
                "es_procedimiento": es_procedimiento,
                "confianza": 0.95
            }
        
        return {
            "intencion": "no_reconocida",
            "ecuacion": None,
            "es_procedimiento": False,
            "confianza": 0.0
        }
    
    def generar_respuesta(self, mensaje: str) -> Tuple[str, Dict]:
        """Genera respuesta matemática"""
        intencion = self.detectar_intencion(mensaje)
        
        if intencion["intencion"] == "solicitud_procedimiento_matematico":
            ecuacion = intencion["ecuacion"]
            
            # Si no se detectó ecuación específica, mostrar fórmula general
            if not ecuacion:
                respuesta = ("Para resolver una ecuación de segundo grado (ax² + bx + c = 0), "
                            "se usa la fórmula general:\n\n"
                            "x = [-b ± √(b² - 4ac)] / 2a\n\n"
                            "¿Te gustaría que te muestre un ejemplo paso a paso con números específicos?")
                return respuesta, intencion
            
            # Intentar parsear y resolver
            try:
                a, b, c = self.parsear_ecuacion(ecuacion)
                
                if a == 0:
                    return "No es una ecuación de segundo grado (coeficiente a = 0). ¿Quieres que te ayude con una ecuación lineal?", intencion
                
                resultado = self.resolver_ecuacion(a, b, c)
                
                respuesta = f"**Resolución de {ecuacion}**\n\n"
                respuesta += f"**Paso 1:** Identificar coeficientes:\n"
                respuesta += f"   a = {resultado['a']}, b = {resultado['b']}, c = {resultado['c']}\n\n"
                respuesta += f"**Paso 2:** Aplicar fórmula general:\n"
                respuesta += f"   {resultado['pasos'][0]}\n\n"
                respuesta += f"**Resultado:** {resultado['tipo_soluciones']}\n"
                
                if len(resultado['soluciones']) == 2:
                    respuesta += f"   x₁ = {resultado['soluciones'][0]:.4f}\n"
                    respuesta += f"   x₂ = {resultado['soluciones'][1]:.4f}"
                elif len(resultado['soluciones']) == 1:
                    respuesta += f"   x = {resultado['soluciones'][0]:.4f}"
                
                respuesta += "\n\n¿Te gustaría resolver otra ecuación o que te explique algún paso en detalle?"
                
                return respuesta, intencion
                
            except Exception as e:
                return f"No pude procesar la ecuación '{ecuacion}'. Asegúrate de escribirla en formato como 'x^2 + 3x + 2 = 0'. ¿Quieres que te muestre un ejemplo?", intencion
        
        return ("Hola, soy un asistente matemático. Puedo ayudarte a resolver ecuaciones de segundo grado. "
                "Por ejemplo: 'Resuelve x^2 + 5x + 6 = 0' o '¿Cómo se resuelve una ecuación de segundo grado?'"), intencion
    
    def iniciar_conversacion(self):
        """Modo interactivo"""
        print("\n" + "="*60)
        print("🧮 ASISTENTE MATEMÁTICO - Ecuaciones de Segundo Grado")
        print("="*60)
        print("Ejemplos:")
        print("  • '¿Cómo se resuelve una ecuación de segundo grado?'")
        print("  • 'Resuelve x^2 + 5x + 6 = 0'")
        print("  • '2x^2 - 4x - 6 = 0'")
        print("Escribe 'salir' para terminar.")
        print("-"*60)
        
        while True:
            usuario = input("\n👤 Tú: ").strip()
            
            if usuario.lower() in ["salir", "exit", "adiós"]:
                print("\n🤖 Asistente: ¡Sigue practicando matemáticas! ¡Hasta luego!")
                break
            
            if not usuario:
                continue
            
            respuesta, intencion = self.generar_respuesta(usuario)
            self.historial.append({"usuario": usuario, "respuesta": respuesta})
            
            print(f"\n🤖 Asistente: {respuesta}")

# ========== EJECUCIÓN ==========
if __name__ == "__main__":
    asistente = AsistenteMatematico()
    
    print("\n" + "="*60)
    print("📋 PRUEBAS DE CONSULTAS MATEMÁTICAS:")
    print("="*60)
    
    pruebas = [
        "¿Cómo se resuelve una ecuación de segundo grado?",
        "Resuelve x^2 + 5x + 6 = 0",
        "2x^2 - 4x - 6 = 0"
    ]
    
    for prueba in pruebas:
        respuesta, _ = asistente.generar_respuesta(prueba)
        print(f"\n🔍 {prueba}")
        print(f"✨ {respuesta}")
    
    asistente.iniciar_conversacion()
```

---

## 📌 **EJEMPLO 4: Consulta de Autor Literario**

### **Planteamiento del Problema**
Desarrollar un asistente cultural que detecte consultas sobre autores literarios, identificando preguntas como "¿Quién escribió...?" y respondiendo con información biográfica y contextual relevante.

```python
"""
=============================================
EJEMPLO 4: ASISTENTE LITERARIO - CONSULTAS DE AUTORES
=============================================
Intención: Consulta de autor literario
Funcionalidad: Identifica obras y sus autores con contexto cultural
"""

import re
from typing import Dict, Optional, List

class AsistenteLiterario:
    """
    Sistema especializado en identificar autores de obras literarias
    Responde con información biográfica y contexto
    """
    
    def __init__(self):
        # Base de conocimiento de obras y autores
        self.base_conocimiento = {
            "cien años de soledad": {
                "autor": "Gabriel García Márquez",
                "datos_autor": "escritor colombiano y premio Nobel de Literatura en 1982",
                "contexto": "Considerada una obra maestra del realismo mágico",
                "fecha": "1967"
            },
            "el amor en los tiempos del cólera": {
                "autor": "Gabriel García Márquez",
                "datos_autor": "escritor colombiano y premio Nobel de Literatura en 1982",
                "contexto": "Una de las novelas de amor más importantes del siglo XX",
                "fecha": "1985"
            },
            "don quijote de la mancha": {
                "autor": "Miguel de Cervantes",
                "datos_autor": "escritor español, considerado la figura más importante de la literatura española",
                "contexto": "Considerada la primera novela moderna",
                "fecha": "1605"
            },
            "rayuela": {
                "autor": "Julio Cortázar",
                "datos_autor": "escritor argentino, figura clave del boom latinoamericano",
                "contexto": "Novela que revolucionó la narrativa con su estructura no lineal",
                "fecha": "1963"
            },
            "la casa de los espíritus": {
                "autor": "Isabel Allende",
                "datos_autor": "escritora chilena, una de las autoras más leídas del mundo",
                "contexto": "Novela que mezcla realismo mágico con crítica social",
                "fecha": "1982"
            },
            "pedro páramo": {
                "autor": "Juan Rulfo",
                "datos_autor": "escritor mexicano, precursor del realismo mágico",
                "contexto": "Obra fundamental de la literatura mexicana",
                "fecha": "1955"
            }
        }
        
        # Patrones para detección de intenciones
        self.patrones_autor = [
            r"qui[eé]n\s+(?:escribi[oó]|escribi[oó]?)\s+(?:el\s+)?libro\s+([a-záéíóúñ\s]+)",
            r"qui[eé]n\s+es\s+el\s+autor\s+(?:de\s+)?([a-záéíóúñ\s]+)",
            r"(?:escrito|escrita)\s+por\s+qui[eé]n",
            r"(?:autor|autora)\s+(?:de\s+)?([a-záéíóúñ\s]+)",
            r"qui[eé]n\s+(?:escribi[oó]|escribi[oó]?)\s+([a-záéíóúñ\s]+)"
        ]
        
        self.historial = []
    
    def normalizar_texto(self, texto: str) -> str:
        """Normaliza texto para procesamiento"""
        texto = texto.lower().strip()
        texto = re.sub(r'[¿?¡!]', '', texto)
        texto = re.sub(r'["\']', '', texto)
        return texto
    
    def extraer_obra(self, mensaje: str) -> Optional[str]:
        """Extrae el nombre de la obra consultada"""
        mensaje_norm = self.normalizar_texto(mensaje)
        
        for patron in self.patrones_autor:
            coincidencia = re.search(patron, mensaje_norm)
            if coincidencia:
                obra = coincidencia.group(1).strip()
                # Limpiar artículos
                obra = re.sub(r'^(el|la|los|las|un|una)\s+', '', obra)
                return obra
        
        return None
    
    def detectar_intencion(self, mensaje: str) -> Dict:
        """Detecta la intención del mensaje"""
        mensaje_norm = self.normalizar_texto(mensaje)
        
        # Detectar si es consulta de autor
        if any(re.search(patron, mensaje_norm) for patron in self.patrones_autor):
            obra = self.extraer_obra(mensaje)
            return {
                "intencion": "consulta_autor_literario",
                "obra": obra,
                "confianza": 0.95 if obra else 0.80
            }
        
        return {
            "intencion": "no_reconocida",
            "obra": None,
            "confianza": 0.0
        }
    
    def buscar_obra(self, obra_buscada: str) -> Optional[Dict]:
        """Busca la obra en la base de conocimiento con matching flexible"""
        obra_buscada = obra_buscada.lower().strip()
        
        # Búsqueda exacta
        if obra_buscada in self.base_conocimiento:
            return self.base_conocimiento[obra_buscada]
        
        # Búsqueda parcial
        for obra, info in self.base_conocimiento.items():
            if obra in obra_buscada or obra_buscada in obra:
                return info
        
        return None
    
    def generar_respuesta(self, mensaje: str) -> Tuple[str, Dict]:
        """Genera respuesta literaria"""
        intencion = self.detectar_intencion(mensaje)
        
        if intencion["intencion"] == "consulta_autor_literario":
            obra = intencion["obra"]
            
            if not obra:
                return "¿De qué obra te gustaría saber el autor? Por ejemplo: 'Cien años de soledad' o 'Don Quijote'.", intencion
            
            # Buscar obra
            info = self.buscar_obra(obra)
            
            if info:
                respuesta = f"{info['autor']}, {info['datos_autor']}."
                
                # Agregar contexto adicional
                if 'contexto' in info:
                    respuesta += f" {info['contexto']}."
                
                if 'fecha' in info:
                    respuesta += f" Publicada en {info['fecha']}."
                
                return respuesta, intencion
            else:
                # Sugerencias si no se encuentra
                sugerencias = list(self.base_conocimiento.keys())[:3]
                sugerencias_texto = ", ".join(sugerencias)
                return f"Lo siento, no tengo información sobre '{obra}'. ¿Te interesaría saber sobre {sugerencias_texto}?", intencion
        
        return ("Hola, soy un asistente literario. Puedo decirte quién escribió tus libros favoritos. "
                "Pregúntame: '¿Quién escribió Cien años de soledad?'"), intencion
    
    def iniciar_conversacion(self):
        """Modo interactivo"""
        print("\n" + "="*60)
        print("📖 ASISTENTE LITERARIO - Descubre autores de tus libros favoritos")
        print("="*60)
        print("Ejemplos:")
        print("  • '¿Quién escribió Cien años de soledad?'")
        print("  • '¿Quién es el autor de Rayuela?'")
        print("  • '¿Quién escribió La casa de los espíritus?'")
        print("Escribe 'salir' para terminar.")
        print("-"*60)
        
        while True:
            usuario = input("\n👤 Tú: ").strip()
            
            if usuario.lower() in ["salir", "exit", "adiós"]:
                print("\n🤖 Asistente: ¡Sigue disfrutando de la lectura! ¡Hasta luego!")
                break
            
            if not usuario:
                continue
            
            respuesta, intencion = self.generar_respuesta(usuario)
            self.historial.append({"usuario": usuario, "respuesta": respuesta})
            
            print(f"\n🤖 Asistente: {respuesta}")

# ========== EJECUCIÓN ==========
if __name__ == "__main__":
    asistente = AsistenteLiterario()
    
    print("\n" + "="*60)
    print("📋 PRUEBAS DE CONSULTAS LITERARIAS:")
    print("="*60)
    
    pruebas = [
        "¿Quién escribió 'Cien años de soledad'?",
        "¿Quién es el autor de Don Quijote de la Mancha?",
        "¿Quién escribió La casa de los espíritus?"
    ]
    
    for prueba in pruebas:
        respuesta, _ = asistente.generar_respuesta(prueba)
        print(f"\n🔍 {prueba}")
        print(f"✨ {respuesta}")
    
    asistente.iniciar_conversacion()
```

---

## 📌 **EJEMPLO 5: Conjugación del Verbo "Tener"**

### **Planteamiento del Problema**
Crear un asistente gramatical que detecte solicitudes de conjugaciones verbales, específicamente para el verbo "tener" en presente de indicativo, proporcionando la conjugación completa y ejemplos de uso.

```python
"""
=============================================
EJEMPLO 5: ASISTENTE GRAMATICAL - CONJUGACIÓN DE VERBOS
=============================================
Intención: Solicitud gramatical
Funcionalidad: Conjuga verbos en diferentes tiempos y modos
"""

import re
from typing import Dict, List, Optional, Tuple

class AsistenteGramatical:
    """
    Sistema especializado en conjugación verbal
    Detecta solicitudes de información gramatical
    """
    
    def __init__(self):
        # Base de conocimiento de verbos
        self.verbos = {
            "tener": {
                "significado": "poseer, contar con algo",
                "conjugaciones": {
                    "presente_indicativo": {
                        "yo": "tengo",
                        "tú": "tienes",
                        "él/ella/usted": "tiene",
                        "nosotros/nosotras": "tenemos",
                        "vosotros/vosotras": "tenéis",
                        "ellos/ellas/ustedes": "tienen"
                    },
                    "pretérito_imperfecto": {
                        "yo": "tenía",
                        "tú": "tenías",
                        "él/ella/usted": "tenía",
                        "nosotros/nosotras": "teníamos",
                        "vosotros/vosotras": "teníais",
                        "ellos/ellas/ustedes": "tenían"
                    },
                    "pretérito_perfecto_simple": {
                        "yo": "tuve",
                        "tú": "tuviste",
                        "él/ella/usted": "tuvo",
                        "nosotros/nosotras": "tuvimos",
                        "vosotros/vosotras": "tuvisteis",
                        "ellos/ellas/ustedes": "tuvieron"
                    },
                    "futuro_simple": {
                        "yo": "tendré",
                        "tú": "tendrás",
                        "él/ella/usted": "tendrá",
                        "nosotros/nosotras": "tendremos",
                        "vosotros/vosotras": "tendréis",
                        "ellos/ellas/ustedes": "tendrán"
                    }
                },
                "ejemplos": [
                    ("Yo tengo un perro.", "Primera persona singular"),
                    ("Tú tienes mucha paciencia.", "Segunda persona singular"),
                    ("Ella tiene una casa hermosa.", "Tercera persona singular"),
                    ("Nosotros tenemos planes para el fin de semana.", "Primera persona plural"),
                    ("Ellos tienen que estudiar.", "Tercera persona plural")
                ]
            },
            "ser": {
                "significado": "existir, identificarse, pertenecer",
                "conjugaciones": {
                    "presente_indicativo": {
                        "yo": "soy",
                        "tú": "eres",
                        "él/ella/usted": "es",
                        "nosotros/nosotras": "somos",
                        "vosotros/vosotras": "sois",
                        "ellos/ellas/ustedes": "son"
                    }
                }
            },
            "estar": {
                "significado": "ubicarse, estado temporal",
                "conjugaciones": {
                    "presente_indicativo": {
                        "yo": "estoy",
                        "tú": "estás",
                        "él/ella/usted": "está",
                        "nosotros/nosotras": "estamos",
                        "vosotros/vosotras": "estáis",
                        "ellos/ellas/ustedes": "están"
                    }
                }
            }
        }
        
        # Patrones para detección de intenciones
        self.patrones_conjugacion = [
            r"(?:conjugaci[oó]n|conjugar)\s+(?:del?\s+)?verbo\s+([a-záéíóúñ]+)",
            r"c[oó]mo\s+se\s+conjuga\s+([a-záéíóúñ]+)",
            r"(?:conjuga|escribe)\s+el\s+verbo\s+([a-záéíóúñ]+)",
            r"([a-záéíóúñ]+)\s+en\s+presente"
        ]
        
        self.historial = []
    
    def normalizar_texto(self, texto: str) -> str:
        """Normaliza texto para procesamiento"""
        texto = texto.lower().strip()
        texto = re.sub(r'[¿?¡!]', '', texto)
        return texto
    
    def extraer_verbo(self, mensaje: str) -> Optional[str]:
        """Extrae el verbo solicitado"""
        mensaje_norm = self.normalizar_texto(mensaje)
        
        for patron in self.patrones_conjugacion:
            coincidencia = re.search(patron, mensaje_norm)
            if coincidencia:
                verbo = coincidencia.group(1).strip()
                return verbo
        
        # Búsqueda de verbos conocidos
        for verbo in self.verbos.keys():
            if verbo in mensaje_norm:
                return verbo
        
        return None
    
    def extraer_tiempo(self, mensaje: str) -> str:
        """Extrae el tiempo verbal solicitado"""
        mensaje_norm = self.normalizar_texto(mensaje)
        
        tiempos = {
            "presente": ["presente", "ahora", "actual"],
            "pretérito": ["pretérito", "pasado", "ayer"],
            "futuro": ["futuro", "mañana", "después"],
            "imperfecto": ["imperfecto", "antes"]
        }
        
        for tiempo, palabras in tiempos.items():
            if any(p in mensaje_norm for p in palabras):
                return tiempo
        
        return "presente_indicativo"
    
    def detectar_intencion(self, mensaje: str) -> Dict:
        """Detecta la intención del mensaje"""
        mensaje_norm = self.normalizar_texto(mensaje)
        
        # Detectar si es solicitud gramatical
        if any(re.search(patron, mensaje_norm) for patron in self.patrones_conjugacion):
            verbo = self.extraer_verbo(mensaje)
            tiempo = self.extraer_tiempo(mensaje)
            return {
                "intencion": "solicitud_gramatical",
                "verbo": verbo,
                "tiempo": tiempo,
                "confianza": 0.95 if verbo else 0.75
            }
        
        return {
            "intencion": "no_reconocida",
            "verbo": None,
            "tiempo": None,
            "confianza": 0.0
        }
    
    def conjugar_verbo(self, verbo: str, tiempo: str = "presente_indicativo") -> Optional[Dict]:
        """Retorna la conjugación del verbo solicitado"""
        if verbo not in self.verbos:
            return None
        
        verbo_info = self.verbos[verbo]
        
        # Mapear tiempo solicitado al formato de la base
        mapeo_tiempos = {
            "presente": "presente_indicativo",
            "pretérito": "pretérito_perfecto_simple",
            "pasado": "pretérito_perfecto_simple",
            "futuro": "futuro_simple",
            "imperfecto": "pretérito_imperfecto"
        }
        
        tiempo_clave = mapeo_tiempos.get(tiempo, tiempo)
        
        if tiempo_clave in verbo_info["conjugaciones"]:
            return {
                "verbo": verbo,
                "significado": verbo_info["significado"],
                "tiempo": tiempo_clave,
                "conjugacion": verbo_info["conjugaciones"][tiempo_clave],
                "ejemplos": verbo_info.get("ejemplos", [])
            }
        
        return None
    
    def formatear_conjugacion(self, info: Dict) -> str:
        """Formatea la conjugación para presentación"""
        if not info:
            return None
        
        respuesta = f"📚 **Conjugación del verbo '{info['verbo']}' en {info['tiempo'].replace('_', ' ').title()}**\n\n"
        respuesta += f"*Significado:* {info['significado']}\n\n"
        
        # Conjugación en tabla
        respuesta += "| Pronombre | Conjugación |\n"
        respuesta += "|-----------|-------------|\n"
        
        for pronombre, conjugacion in info['conjugacion'].items():
            respuesta += f"| {pronombre.title()} | {conjugacion} |\n"
        
        # Agregar ejemplos si existen
        if info.get('ejemplos'):
            respuesta += "\n**📖 Ejemplos de uso:**\n"
            for i, (ejemplo, explicacion) in enumerate(info['ejemplos'][:3], 1):
                respuesta += f"{i}. *{ejemplo}* → {explicacion}\n"
        
        return respuesta
    
    def generar_respuesta(self, mensaje: str) -> Tuple[str, Dict]:
        """Genera respuesta gramatical"""
        intencion = self.detectar_intencion(mensaje)
        
        if intencion["intencion"] == "solicitud_gramatical":
            verbo = intencion["verbo"]
            tiempo = intencion["tiempo"]
            
            if not verbo:
                return ("¿Qué verbo te gustaría conjugar? Puedo ayudarte con: "
                        "tener, ser, estar. Por ejemplo: 'Conjuga el verbo tener en presente'"), intencion
            
            # Conjugar verbo
            conjugacion = self.conjugar_verbo(verbo, tiempo)
            
            if conjugacion:
                respuesta = self.formatear_conjugacion(conjugacion)
                return respuesta, intencion
            else:
                verbos_disponibles = ", ".join(self.verbos.keys())
                return (f"Lo siento, aún no tengo información sobre el verbo '{verbo}'. "
                        f"Puedo ayudarte con: {verbos_disponibles}. ¿Quieres probar con alguno de estos?"), intencion
        
        return ("Hola, soy un asistente gramatical. Puedo ayudarte con la conjugación de verbos. "
                "Pregúntame: 'Conjuga el verbo tener en presente'"), intencion
    
    def iniciar_conversacion(self):
        """Modo interactivo"""
        print("\n" + "="*60)
        print("📝 ASISTENTE GRAMATICAL - Conjugación de Verbos")
        print("="*60)
        print("Ejemplos:")
        print("  • 'Conjuga el verbo tener en presente'")
        print("  • 'Cómo se conjuga tener en pretérito'")
        print("  • 'Necesito ayuda con la conjugación del verbo tener en presente'")
        print("Escribe 'salir' para terminar.")
        print("-"*60)
        
        while True:
            usuario = input("\n👤 Tú: ").strip()
            
            if usuario.lower() in ["salir", "exit", "adiós"]:
                print("\n🤖 Asistente: ¡Sigue practicando español! ¡Hasta luego!")
                break
            
            if not usuario:
                continue
            
            respuesta, intencion = self.generar_respuesta(usuario)
            self.historial.append({"usuario": usuario, "respuesta": respuesta})
            
            print(f"\n🤖 Asistente: {respuesta}")

# ========== EJECUCIÓN ==========
if __name__ == "__main__":
    asistente = AsistenteGramatical()
    
    print("\n" + "="*60)
    print("📋 PRUEBAS DE CONSULTAS GRAMATICALES:")
    print("="*60)
    
    pruebas = [
        "Necesito ayuda con la conjugación del verbo 'tener' en presente",
        "¿Cómo se conjuga el verbo tener en pretérito?",
        "Conjuga el verbo tener"
    ]
    
    for prueba in pruebas:
        respuesta, _ = asistente.generar_respuesta(prueba)
        print(f"\n🔍 {prueba}")
        print(f"✨ {respuesta}")
    
    asistente.iniciar_conversacion()
```

---

## 📊 **Resumen de los 5 Ejemplos**

| Ejemplo | Intención Detectada | Funcionalidad Principal | Características |
|---------|---------------------|------------------------|-----------------|
| **1** | Solicitud de dato geográfico | Capitales del mundo | Base de conocimientos, patrones regex, respuesta enriquecida |
| **2** | Solicitud de explicación conceptual | Fotosíntesis | Niveles de detalle, lenguaje simple/técnico |
| **3** | Solicitud de procedimiento matemático | Ecuaciones cuadráticas | Parsing de ecuaciones, resolución paso a paso |
| **4** | Consulta de autor literario | Obras y autores | Matching flexible, contexto cultural |
| **5** | Solicitud gramatical | Conjugación verbal | Tablas formatadas, ejemplos de uso |

Cada asistente implementa:
- ✅ Detección de intenciones mediante patrones regex
- ✅ Extracción de entidades (país, tema, ecuación, obra, verbo)
- ✅ Base de conocimiento específica
- ✅ Generación de respuestas contextuales
- ✅ Modo interactivo para conversación continua
- ✅ Historial de conversaciones

¿Te gustaría que agregue más ejemplos o que profundice en alguna funcionalidad específica?
