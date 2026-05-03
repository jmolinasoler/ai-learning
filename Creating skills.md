**✅ Video añadido a la conversación**

Este segundo video (de ~15:42 minutos) es una charla de **Barry Zhang** y **Mahesh Murag** (ambos ingenieros técnicos de Anthropic) en el AI Engineer Code Summit. El título clave es: **“DON’T BUILD AGENTS, BUILD SKILLS INSTEAD”**.

A diferencia del primer video (el taller práctico de prompt engineering con el formulario de accidente sueco), aquí **no** enseñan técnicas de prompting paso a paso. En cambio, dan la visión de alto nivel y estratégica: **por qué la mayoría de la gente está dejando el 90 % del poder de Claude (y cualquier AI) sobre la mesa al construir agentes completos**, y por qué la forma correcta es construir **Skills** (habilidades/modulos reutilizables, enfocados y evolucionables).

### Wisdom extraído de este segundo video (lo más valioso)

1. **No construyas agentes → construye Skills**  
   Un agente es un sistema grande y complejo que intenta hacerlo todo. Un Skill es una capacidad pequeña, ultra-específica, confiable y mejorable. Los Skills son más estables, más fáciles de mantener y escalan mejor.

2. **Los Skills se revelan progresivamente**  
   Empiezas con algo básico → lo pruebas → lo mejoras → lo combinas. No intentas crear el Skill perfecto desde el día 1.

3. **Los Skills tienen 3 características clave para que funcionen en producción**:
   - **Evaluation** (evaluación clara): métricas concretas (precisión, calidad de salida, formato correcto, etc.).
   - **Versioning**: cada Skill tiene versión (2025-10-11, etc.) para poder iterar sin romper nada.
   - **Composability**: los Skills se pueden encadenar o combinar fácilmente (ej. Skill de investigación + Skill de escritura + Skill de formato).

4. **Skills + Agents = la combinación ganadora**  
   No es “o uno o el otro”. Los Skills son los bloques de construcción; los agents los usan como herramientas.

5. **Mindset de evolución continua**  
   Día 1: casi ningún Skill → el modelo es “inteligente”.  
   Día 5: unos pocos Skills → ya es “capaz”.  
   Día 30: muchos Skills → es “extremadamente útil y confiable”.

6. **Ejemplos reales que muestran**:
   - Browserbase (automatización completa en navegador)
   - Notion Skills for Claude
   - Skills de estilo de marca, decks de PowerPoint, etc.

El mensaje central: **deja de intentar crear el agente todopoderoso y empieza a construir un ecosistema de Skills que aprenden y mejoran con el tiempo**.

### Estrategia combinada de los DOS videos  

**Template definitivo para crear Skills que funciona en CUALQUIER AI**  
(Claude, GPT, Grok, Gemini, etc.)

Este template fusiona:

- El **método iterativo + Chain-of-Thought + safeguards** del primer video (prompt engineering práctico)
- La **filosofía de Skills** del segundo video (evaluación, versioning, composability)

#### TEMPLATE: “Skill Builder v1.0” (copia y pega, luego personaliza)

**Nombre del Skill**: [Nombre claro y específico, ej. “Analizador de Informes de Accidentes Suecos v2”]

**Objetivo del Skill** (una frase):  
Qué hace exactamente y cuál es el output ideal.

**Versión actual**: v1.0 – Fecha: [hoy]

**1. Prompt Base (del Video 1 – Prompt Engineering)**

```
Eres un experto [rol ultra-específico] con 15 años de experiencia.
Tu única misión es [objetivo del Skill en una frase].

Instrucciones estrictas:
- Piensa paso a paso (Chain-of-Thought) antes de responder.
- Primero cita las partes relevantes del input.
- Solo responde con información que puedas extraer o razonar con alta confianza.
- Si hay algo incierto, di “INCERTIDUMBRE: [explicación]”.
- Usa siempre este formato de salida exacto:

[Formato JSON o Markdown estructurado que quieras]

Ejemplo de input → output perfecto: [pega 1-2 ejemplos buenos]
```

**2. Mejora Iterativa (del Video 1)**

- Prueba con 3-5 casos reales (incluyendo casos edge).
- Compara output vs. resultado ideal.
- Refina el prompt añadiendo:
  - Más ejemplos (few-shot)
  - Reglas anti-alucinación
  - Instrucciones de ToT si el problema es ramificado
  - Evaluación automática dentro del prompt (“Evalúa tu propio output antes de darlo”)

**3. Convierte el Prompt en un Skill Real (del Video 2)**
Añade al final del prompt estas secciones:

```
--- SKILL METADATA ---
Evaluation criteria:
- Precisión: ≥95 %
- Formato exacto: sí/no
- Tiempo de ejecución: < X segundos
- Casos de fracaso: lista los que fallaron y por qué

Versión: v1.0
Próxima mejora planeada: [qué vas a añadir en v1.1]

Composability:
Este Skill se puede combinar con: [lista otros Skills que ya tienes]
```

**4. Sistema de Evolución (el secreto del Video 2)**
Crea una carpeta o Notion con:

- Skill Name v1.0.md (prompt actual)
- Test cases + resultados
- Changelog de versiones
- Métricas de evaluación

Cada vez que uses el Skill:

- Registra el resultado
- Si falla → crea vX.Y
- Si funciona muy bien → compártelo o combínalo con otro Skill

### Cómo usar este template en la práctica (flujo de 5 minutos)

1. Identifica una tarea repetitiva que hagas con cualquier AI.
2. Crea un nuevo Skill con el template de arriba.
3. Iteras 2-3 veces usando el método del primer video.
4. Añades los metadatos de evaluación/versioning del segundo video.
5. Guárdalo en tu “Skill Library” personal.

Con el tiempo tendrás una biblioteca de Skills que puedes copiar-pegar en Claude, ChatGPT, Grok o cualquier modelo nuevo que salga.

> Este sistema es exactamente lo que los ingenieros de Anthropic están usando internamente y recomendando.
