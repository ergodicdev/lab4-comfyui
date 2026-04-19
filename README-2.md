# Lab 4 – ComfyUI: Pipeline de Generación y Edición de Imágenes con Preservación de Identidad Facial

## Integrantes
- **Miguel Angel Silva Cajusol**
- **Kelvin Palomino**
- **Paul Sanchez**

**Curso:** Deep Learning — Universidad de Ingeniería y Tecnología (UTEC)  
**Fecha de entrega:** Domingo 19 de abril, 2026

---

## Tabla de Contenidos
1. [Descripción del Pipeline](#1-descripción-del-pipeline)
2. [Explicación de la Metodología por Módulo](#2-explicación-de-la-metodología-por-módulo)
3. [Integración del Pipeline Completo](#3-integración-del-pipeline-completo)
4. [Resultados Individuales](#4-resultados-individuales)
5. [Resultados Grupales](#5-resultados-grupales)
6. [Comparación entre Tipos de Transformación](#6-comparación-entre-tipos-de-transformación)
7. [Observaciones sobre Preservación de Identidad](#7-observaciones-sobre-preservación-de-identidad)
8. [Errores, Limitaciones y Comentarios del Pipeline](#8-errores-limitaciones-y-comentarios-del-pipeline)
9. [Estructura del Repositorio](#9-estructura-del-repositorio)

---

## 1. Descripción del Pipeline

### Herramientas utilizadas
| Herramienta | Rol | Por qué se eligió |
|---|---|---|
| **cloud.comfy.org** | Plataforma ComfyUI en la nube | Gratuita, sin setup, 400 créditos por cuenta |
| **Nano Banana 2 (Gemini 3.1 Flash Image)** | Modelo generativo principal | Liviano, rápido, excelente comprensión de instrucciones en lenguaje natural |
| **BatchImagesNode** | Procesamiento multi-imagen | Permite combinar hasta 14 fotos de entrada para escenas grupales |

### ¿Por qué Nano Banana 2?
El profesor indicó usar **modelos pequeños**. Nano Banana 2 es una versión optimizada y liviana que usa Gemini 3.1 Flash como motor — un modelo multimodal eficiente diseñado para edición de imágenes con instrucciones en lenguaje natural. A diferencia de modelos como SDXL (~6.5GB) o Flux (~12GB), este modelo es rápido y consume pocos créditos (~15 créditos por imagen a resolución 1K).

---

## 2. Explicación de la Metodología por Módulo

### Módulo 1: Carga de Imagen (`LoadImage`)
El primer nodo del pipeline recibe la fotografía real del integrante del grupo. Esta imagen es la referencia de identidad que el modelo debe transformar según las instrucciones del prompt.

- **Para resultados individuales:** se usa un solo nodo `LoadImage` con la foto del integrante
- **Para resultados grupales:** se usan tres nodos `LoadImage` simultáneos (uno por integrante)

### Módulo 2: Procesamiento por Lotes (`BatchImagesNode`)
Este nodo agrupa todas las imágenes de entrada y las pasa como un conjunto al modelo generativo. Es crítico para las escenas grupales, donde tres fotografías distintas deben fusionarse en una sola imagen coherente.

- Acepta hasta 14 imágenes de entrada simultáneas
- Por defecto aparece en estado "Bypass" y debe activarse manualmente via clic derecho → "Eliminar Bypass"

### Módulo 3: Motor Generativo (`GeminiNanoBanana2`)
Este es el núcleo del pipeline. Recibe las imágenes y el prompt de instrucción, y genera la imagen transformada.

| Parámetro | Función | Valores usados |
|---|---|---|
| `prompt` | Instrucción de transformación en lenguaje natural | Ver `prompts.md` |
| `thinking_level` | Profundidad de razonamiento del modelo | MINIMAL (leve) / HIGH (moderado y fuerte) |
| `resolution` | Resolución de salida | 1K en todos los casos |
| `model` | Versión del modelo | Nano Banana 2 (Gemini 3.1 Flash Image) |
| `seed` | Semilla de aleatoriedad | Aleatorio en cada ejecución |

El parámetro `thinking_level` es el control principal de transformación:
- **MINIMAL:** el modelo preserva la identidad facial, solo modifica contexto e iluminación
- **HIGH:** el modelo tiene mayor libertad creativa para transformaciones más profundas

### Módulo 4: Guardado (`SaveImage`)
Recibe la imagen generada con el prefijo `Nano_Banana2` y la guarda para descarga manual.

### Screenshot del Workflow Completo

![Workflow ComfyUI](WorkFlow.png)

---

## 3. Integración del Pipeline Completo

### Flujo de datos

```
ENTRADA                    PROCESAMIENTO                      SALIDA
──────                    ─────────────                      ──────

[LoadImage: Miguel]  ─┐
[LoadImage: Kelvin]  ─┤→ [BatchImagesNode] → [GeminiNanoBanana2] → [SaveImage]
[LoadImage: Paul]    ─┘      (Up to 14)       ↑            ↑
                                           [prompt]  [thinking_level]
```

### Para resultados individuales:
1. Cargar foto del integrante en `LoadImage`
2. Escribir prompt del nivel correspondiente (leve/moderado/fuerte)
3. Ajustar `thinking_level` (MINIMAL para leve, HIGH para moderado y fuerte)
4. Ejecutar y descargar resultado

### Para resultados grupales:
1. Activar `BatchImagesNode` eliminando su estado Bypass
2. Conectar tres nodos `LoadImage` a `image0`, `image1`, `image2`
3. Cargar foto de cada integrante en su nodo correspondiente
4. Usar prompt grupal que instruye al modelo a combinar las 3 personas
5. `thinking_level: HIGH` para permitir la recomposición creativa

### Decisiones de diseño
- `thinking_level: MINIMAL` para cambios leves → maximiza preservación de identidad
- `thinking_level: HIGH` para moderado y fuerte → permite transformaciones profundas
- Prompts estructurados en secciones (BACKGROUND, LIGHTING, PRESERVE, QUALITY) para mayor precisión
- Resolución 1K como balance entre calidad y consumo de créditos

---

## 4. Resultados Individuales

### 4.1 Miguel Angel Silva Cajusol

#### 🟢 Cambios Leves — `thinking_level: MINIMAL`

| Escena | Resultado | Identidad |
|---|---|---|
| Retrato de estudio | ![](outputs/individual/Miguel_Silva/leve/miguel_leve_01_studio.png) | ✅ Muy alta |
| Golden Hour | ![](outputs/individual/Miguel_Silva/leve/miguel_leve_02_golden.png) | ✅ Muy alta |
| Oficina corporativa | ![](outputs/individual/Miguel_Silva/leve/miguel_leve_03_oficina.png) | ✅ Muy alta |

#### 🟡 Cambios Moderados — `thinking_level: HIGH`

| Escena | Resultado | Identidad |
|---|---|---|
| Lab IA futurista | ![](outputs/individual/Miguel_Silva/moderado/miguel_moderado_01_futurista.png) | ✅ Media-Alta |
| Cyberpunk nocturno | ![](outputs/individual/Miguel_Silva/moderado/miguel_moderado_02_cyberpunk.png) | ✅ Media |
| Editorial revista | ![](outputs/individual/Miguel_Silva/moderado/miguel_moderado_03_editorial.png) | ✅ Media-Alta |

#### 🔴 Cambios Fuertes — `thinking_level: HIGH`

| Escena | Resultado | Identidad |
|---|---|---|
| Científico 1920s | ![](outputs/individual/Miguel_Silva/fuerte/miguel_fuerte_01_1920s.png) | ⚠️ Baja-Media |
| Tahuantinsuyo | ![](outputs/individual/Miguel_Silva/fuerte/miguel_fuerte_02_inca.png) | ⚠️ Baja |
| Astronauta Luna | ![](outputs/individual/Miguel_Silva/fuerte/miguel_fuerte_03_luna.png) | ⚠️ Baja |

---

### 4.2 Kelvin Palomino

#### 🟢 Cambios Leves — `thinking_level: MINIMAL`

| Escena | Resultado | Identidad |
|---|---|---|
| Retrato de estudio | ![](outputs/individual/Kelvin_Palomino/leve/kelvin_leve_01_studio.png) | ✅ Muy alta |
| Oficina corporativa | ![](outputs/individual/Kelvin_Palomino/leve/kelvin_leve_03_oficina.png) | ✅ Muy alta |

#### 🟡 Cambios Moderados — `thinking_level: HIGH`

| Escena | Resultado | Identidad |
|---|---|---|
| Lab IA futurista | ![](outputs/individual/Kelvin_Palomino/moderado/kelvin_moderado_01_futurista.png) | ✅ Media-Alta |
| Editorial revista | ![](outputs/individual/Kelvin_Palomino/moderado/kelvin_moderado_03_editorial.png) | ✅ Media |

#### 🔴 Cambios Fuertes — `thinking_level: HIGH`

| Escena | Resultado | Identidad |
|---|---|---|
| Científico 1920s | ![](outputs/individual/Kelvin_Palomino/fuerte/kelvin_fuerte_01_1920s.png) | ⚠️ Baja-Media |
| Astronauta Luna | ![](outputs/individual/Kelvin_Palomino/fuerte/kelvin_fuerte_03_luna.png) | ⚠️ Baja |

---

### 4.3 Paul Sanchez

#### 🟢 Cambios Leves — `thinking_level: MINIMAL`

| Escena | Resultado | Identidad |
|---|---|---|
| Retrato de estudio | ![](outputs/individual/Paul_Sanchez/leve/paul_leve_01_studio.png) | ✅ Muy alta |
| Oficina corporativa | ![](outputs/individual/Paul_Sanchez/leve/paul_leve_03_oficina.png) | ✅ Muy alta |

#### 🟡 Cambios Moderados — `thinking_level: HIGH`

| Escena | Resultado | Identidad |
|---|---|---|
| Lab IA futurista | ![](outputs/individual/Paul_Sanchez/moderado/paul_moderado_01_futurista.png) | ✅ Media-Alta |
| Editorial revista | ![](outputs/individual/Paul_Sanchez/moderado/paul_moderado_03_editorial.png) | ✅ Media |

#### 🔴 Cambios Fuertes — `thinking_level: HIGH`

| Escena | Resultado | Identidad |
|---|---|---|
| Científico 1920s | ![](outputs/individual/Paul_Sanchez/fuerte/paul_fuerte_01_1920s.png) | ⚠️ Baja-Media |
| Astronauta Luna | ![](outputs/individual/Paul_Sanchez/fuerte/paul_fuerte_03_luna.png) | ⚠️ Baja |

---

## 5. Resultados Grupales

Generadas usando `BatchImagesNode` con las 3 fotos simultáneas como entrada. Se generaron 2 versiones de la conferencia para obtener mejor resultado.

| Escena | Resultado | Coherencia | Identidad |
|---|---|---|---|
| Equipo investigación IA | ![](outputs/grupales/grupal_01_equipo_ia.png) | ✅ Alta | ⚠️ Parcial |
| Panel conferencistas v1 | ![](outputs/grupales/grupal_02_conferenciaV1.png) | ✅ Media-Alta | ⚠️ Parcial |
| Panel conferencistas v2 | ![](outputs/grupales/grupal_02_conferenciaV2.png) | ✅ Alta | ⚠️ Parcial |
| Tripulación en Marte | ![](outputs/grupales/grupal_03_marte.png) | ✅ Alta | ⚠️ Baja |

---

## 6. Comparación entre Tipos de Transformación

| Nivel | thinking_level | Fondo | Estilo | Época | Identidad resultante |
|---|---|---|---|---|---|
| **Leve** | MINIMAL | ✅ | ❌ | ❌ | ✅ Muy alta (95-100%) |
| **Moderado** | HIGH | ✅ | ✅ | ❌ | ✅ Media-Alta (65-80%) |
| **Fuerte** | HIGH | ✅ | ✅ | ✅ | ⚠️ Baja-Media (30-50%) |
| **Grupal** | HIGH | ✅ | ✅ | Varía | ⚠️ Parcial (40-60%) |

**Leve — Retrato de estudio:** El modelo reemplaza el fondo preservando cara, cabello, expresión y ropa de forma idéntica. Mayor control demostrado del pipeline.

**Moderado — Cyberpunk:** La iluminación de neón mixto (rojo + azul) fue la transformación más agresiva del nivel moderado. El modelo aplicó los colores directamente sobre la piel alterando el tono pero manteniendo la estructura facial.

**Fuerte — Tahuantinsuyo:** Transformación más agresiva. El modelo adaptó rasgos faciales al contexto cultural andino. La identidad individual se pierde casi completamente en favor de la coherencia histórica.

**Fuerte — Astronauta:** El casco oculta físicamente el rostro. La cara es visible a través del visor pero el reflejo del paisaje lunar reduce su legibilidad. El contexto domina sobre la identidad.

---

## 7. Observaciones sobre Preservación de Identidad

### ✅ Casos donde la identidad se preserva bien

1. **thinking_level: MINIMAL con prompts de contexto/iluminación** — El modelo no modifica rasgos faciales, solo el fondo y la iluminación.
2. **Prompts con sección PRESERVE EXACTLY detallada** — Especificar exactamente qué preservar ("face, facial structure, skin tone, eye color, hair style") produce alta fidelidad.
3. **Escenas contemporáneas** — Sin necesidad de adaptar rasgos a un contexto histórico diferente.
4. **Iluminación sin color dominante** — El estudio fotográfico (luz blanca neutra) preserva mejor que iluminación de color fuerte.

### ⚠️ Casos donde la identidad comienza a degradarse

1. **thinking_level: HIGH** — Mayor libertad de razonamiento produce reinterpretación de rasgos.
2. **Iluminación de color dominante** — Neón y hologramas alteran perceptualmente el tono de piel.
3. **Cambios de vestimenta elaborados** — El modelo a veces reinterpreta partes del cuerpo junto con la ropa.
4. **Escenas grupales** — El modelo "promedia" rasgos para lograr coherencia visual entre los tres sujetos.

### ❌ Casos donde la identidad se pierde significativamente

1. **Transformaciones históricas (1920s, Inca)** — Los rasgos se adaptan al contexto cultural e histórico.
2. **Trajes que ocluyen el rostro** — El casco espacial hace imposible la comparación de identidad.
3. **Escenas grupales con HIGH** — La coherencia visual grupal se prioriza sobre la fidelidad individual.

---

## 8. Errores, Limitaciones y Comentarios del Pipeline

### Errores encontrados

| Error | Descripción | Solución |
|---|---|---|
| **Formato HEIC no soportado** | Fotos iPhone no aceptadas por ComfyUI | Conversión previa a JPEG |
| **Máscara no funcional** | Workflow `gsc_creator_2_2` (Inpainting+ControlNet) no aplicaba la máscara correctamente | Se migró a Nano Banana 2 |
| **BatchImagesNode en Bypass** | Nodo desactivado por defecto, no obvio cómo activarlo | Clic derecho → "Eliminar Bypass" |
| **Imágenes no persistentes** | Al cambiar de cuenta las referencias a imágenes quedan rotas | Re-subir manualmente las fotos |
| **Créditos agotados** | 400 créditos insuficientes para todo el lab | Uso de segunda cuenta Gmail |

### Limitaciones del modelo

1. **No es Stable Diffusion puro** — No hay parámetros como CFG, denoise strength o steps. El control es exclusivamente via lenguaje natural.
2. **Sin memoria entre generaciones** — Cada ejecución es independiente, sin ajustes finos incrementales.
3. **Control limitado de composición espacial** — En grupales, la posición exacta de cada persona es aproximada.
4. **Alta variabilidad** — Con el mismo prompt y seed aleatorio, los resultados varían significativamente.
5. **Resolución limitada en plan gratuito** — 1K como máximo práctico (~15 créditos). 2K duplica el costo con mejora moderada.

### Limitaciones de la plataforma

1. **Créditos limitados** — 400 créditos por cuenta ≈ 26-28 imágenes a 1K. Se requirieron múltiples cuentas.
2. **Sin persistencia de sesión** — Las imágenes subidas no se mantienen entre sesiones.
3. **Sin historial de generaciones** — Todas las imágenes deben descargarse manualmente en el momento.

### Observaciones sobre prompting

1. **Inglés produce mejores resultados** — El modelo fue entrenado predominantemente en inglés.
2. **La estructura del prompt importa** — Secciones explícitas (BACKGROUND, LIGHTING, PRESERVE, QUALITY) producen resultados superiores a prompts simples.
3. **thinking_level: HIGH no siempre es mejor** — En varios casos produjo transformaciones más agresivas de lo deseado.
4. **Escenas grupales requieren descripción espacial** — "two in front, one slightly behind" mejora notablemente la coherencia.

### Discusión de resultados

El pipeline demostró ser efectivo para los niveles leve y moderado, donde la identidad se preserva de forma recognoscible. El nivel fuerte confirmó que existe un límite claro donde las transformaciones semánticas profundas superan la capacidad del modelo de mantener la identidad individual.

Las escenas grupales representaron el mayor desafío técnico. La ausencia de fotografía grupal de referencia obligó a un enfoque de composición desde múltiples entradas, con resultados visualmente coherentes pero con pérdida notable de identidad individual.

El parámetro `thinking_level` funcionó como análogo al `denoise_strength` de Stable Diffusion: a mayor valor, mayor transformación y menor preservación de identidad.

---

## 9. Estructura del Repositorio

```
lab4-comfyui/
│
├── README.md
├── prompts.md
├── WorkFlow.png
├── workflow_grupal_Lab04_DeepLearning.json
│
├── inputs/
│   ├── Miguel_Silva.jpeg
│   ├── Kelvin_Palomino.JPG
│   └── Paul_Sanchez.JPG
│
└── outputs/
    ├── individual/
    │   ├── Miguel_Silva/
    │   │   ├── leve/
    │   │   ├── moderado/
    │   │   └── fuerte/
    │   ├── Kelvin_Palomino/
    │   │   ├── leve/
    │   │   ├── moderado/
    │   │   └── fuerte/
    │   └── Paul_Sanchez/
    │       ├── leve/
    │       ├── moderado/
    │       └── fuerte/
    └── grupales/
        ├── grupal_01_equipo_ia.png
        ├── grupal_02_conferenciaV1.png
        ├── grupal_02_conferenciaV2.png
        └── grupal_03_marte.png
```
