# Lab 4 – ComfyUI: Pipeline de Generación y Edición de Imágenes con Preservación de Identidad Facial

## Integrantes
- **Miguel Angel Silva Cajusol**
- **Kelvin Palomino**
- **Paul Sanchez**

## Curso
Deep Learning — Universidad de Ingeniería y Tecnología (UTEC)

---

## 1. Descripción del Pipeline

### Herramientas utilizadas
- **Plataforma:** [cloud.comfy.org](https://cloud.comfy.org) — ComfyUI en la nube (versión oficial)
- **Modelo generativo:** Nano Banana 2 (Gemini 3.1 Flash Image) — modelo liviano y eficiente
- **Workflow:** Grafo de nodos en ComfyUI con soporte multi-imagen (BatchImagesNode)

### Arquitectura del workflow

```
[LoadImage: Persona 1] ──┐
[LoadImage: Persona 2] ──┤──→ [BatchImagesNode] ──→ [GeminiNanoBanana2] ──→ [SaveImage]
[LoadImage: Persona 3] ──┘         (Up to 14)           (Nano Banana 2)
```

**Nodos principales:**
| Nodo | Función |
|---|---|
| `LoadImage` | Carga la foto de entrada del integrante |
| `BatchImagesNode` | Agrupa múltiples imágenes para procesamiento (usado en grupales) |
| `GeminiNanoBanana2` | Motor generativo — procesa imagen + prompt y genera el resultado |
| `SaveImage` | Guarda el resultado final |

**Parámetros clave:**
| Parámetro | Nivel Leve | Nivel Moderado | Nivel Fuerte |
|---|---|---|---|
| `thinking_level` | MINIMAL | HIGH | HIGH |
| `resolution` | 1K | 1K | 1K |
| `model` | Nano Banana 2 | Nano Banana 2 | Nano Banana 2 |

El parámetro `thinking_level` controla cuánto "razona" el modelo antes de generar. MINIMAL produce cambios conservadores que preservan la identidad; HIGH permite transformaciones más agresivas.

---

## 2. Resultados Individuales

### 2.1 Miguel Angel Silva Cajusol

#### 🟢 Cambios Leves
| Escena | Imagen | Identidad |
|---|---|---|
| Retrato de estudio | ![studio](outputs/individual/Miguel_Silva/leve/miguel_leve_01_studio.png) | ✅ Alta |
| Golden Hour | ![golden](outputs/individual/Miguel_Silva/leve/miguel_leve_02_golden.png) | ✅ Alta |
| Oficina corporativa | ![oficina](outputs/individual/Miguel_Silva/leve/miguel_leve_03_oficina.png) | ✅ Alta |

#### 🟡 Cambios Moderados
| Escena | Imagen | Identidad |
|---|---|---|
| Lab IA futurista | ![futurista](outputs/individual/Miguel_Silva/moderado/miguel_moderado_01_futurista.png) | ✅ Media-Alta |
| Escena cyberpunk | ![cyberpunk](outputs/individual/Miguel_Silva/moderado/miguel_moderado_02_cyberpunk.png) | ✅ Media |
| Editorial revista | ![editorial](outputs/individual/Miguel_Silva/moderado/miguel_moderado_03_editorial.png) | ✅ Media-Alta |

#### 🔴 Cambios Fuertes
| Escena | Imagen | Identidad |
|---|---|---|
| Científico 1920s | ![1920s](outputs/individual/Miguel_Silva/fuerte/miguel_fuerte_01_1920s.png) | ⚠️ Baja-Media |
| Visitando Tahuantinsuyo | ![inca](outputs/individual/Miguel_Silva/fuerte/miguel_fuerte_02_inca.png) | ⚠️ Baja |
| Astronauta en la Luna | ![luna](outputs/individual/Miguel_Silva/fuerte/miguel_fuerte_03_luna.png) | ⚠️ Baja |

---

### 2.2 Kelvin Palomino

#### 🟢 Cambios Leves
| Escena | Imagen | Identidad |
|---|---|---|
| Retrato de estudio | ![studio](outputs/individual/Kelvin_Palomino/leve/kelvin_leve_01_studio.png) | ✅ Alta |
| Oficina corporativa | ![oficina](outputs/individual/Kelvin_Palomino/leve/kelvin_leve_03_oficina.png) | ✅ Alta |

#### 🟡 Cambios Moderados
| Escena | Imagen | Identidad |
|---|---|---|
| Lab IA futurista | ![futurista](outputs/individual/Kelvin_Palomino/moderado/kelvin_moderado_01_futurista.png) | ✅ Media-Alta |
| Editorial revista | ![editorial](outputs/individual/Kelvin_Palomino/moderado/kelvin_moderado_03_editorial.png) | ✅ Media |

#### 🔴 Cambios Fuertes
| Escena | Imagen | Identidad |
|---|---|---|
| Científico 1920s | ![1920s](outputs/individual/Kelvin_Palomino/fuerte/kelvin_fuerte_01_1920s.png) | ⚠️ Baja-Media |
| Astronauta en la Luna | ![luna](outputs/individual/Kelvin_Palomino/fuerte/kelvin_fuerte_03_luna.png) | ⚠️ Baja |

---

### 2.3 Paul Sanchez

#### 🟢 Cambios Leves
| Escena | Imagen | Identidad |
|---|---|---|
| Retrato de estudio | ![studio](outputs/individual/Paul_Sanchez/leve/paul_leve_01_studio.png) | ✅ Alta |
| Oficina corporativa | ![oficina](outputs/individual/Paul_Sanchez/leve/paul_leve_03_oficina.png) | ✅ Alta |

#### 🟡 Cambios Moderados
| Escena | Imagen | Identidad |
|---|---|---|
| Lab IA futurista | ![futurista](outputs/individual/Paul_Sanchez/moderado/paul_moderado_01_futurista.png) | ✅ Media-Alta |
| Editorial revista | ![editorial](outputs/individual/Paul_Sanchez/moderado/paul_moderado_03_editorial.png) | ✅ Media |

#### 🔴 Cambios Fuertes
| Escena | Imagen | Identidad |
|---|---|---|
| Científico 1920s | ![1920s](outputs/individual/Paul_Sanchez/fuerte/paul_fuerte_01_1920s.png) | ⚠️ Baja-Media |
| Astronauta en la Luna | ![luna](outputs/individual/Paul_Sanchez/fuerte/paul_fuerte_03_luna.png) | ⚠️ Baja |

---

## 3. Resultados Grupales

| Escena | Imagen | Coherencia visual |
|---|---|---|
| Equipo de investigación IA | ![ia](outputs/grupales/grupal_01_equipo_ia.png) | ✅ Alta |
| Panel de conferencistas v1 | ![conf1](outputs/grupales/grupal_02_conferenciaV1.png) | ✅ Media-Alta |
| Panel de conferencistas v2 | ![conf2](outputs/grupales/grupal_02_conferenciaV2.png) | ✅ Alta |
| Tripulación explorando Marte | ![marte](outputs/grupales/grupal_03_marte.png) | ✅ Alta |

Las escenas grupales fueron generadas utilizando el nodo `BatchImagesNode` que permite ingresar hasta 14 imágenes simultáneamente al modelo, quien las combina en una composición coherente.

---

## 4. Comparación entre tipos de transformación

### Tabla comparativa de preservación de identidad

| Nivel | thinking_level | Cambio de fondo | Cambio de estilo | Cambio de época | Identidad |
|---|---|---|---|---|---|
| **Leve** | MINIMAL | ✅ Sí | ❌ No | ❌ No | ✅ Muy alta |
| **Moderado** | HIGH | ✅ Sí | ✅ Sí | ❌ No | ✅ Media-Alta |
| **Fuerte** | HIGH | ✅ Sí | ✅ Sí | ✅ Sí | ⚠️ Baja-Media |

### Observaciones clave por nivel

**Cambios Leves (thinking_level: MINIMAL)**
- El modelo reemplaza el fondo y la iluminación preservando completamente la estructura facial
- Cambios de contexto (estudio, golden hour, oficina) no afectan los rasgos faciales
- La identidad es inmediatamente recognoscible en el 100% de los casos

**Cambios Moderados (thinking_level: HIGH)**
- El modelo aplica iluminación estilizada (neón, hologramas, spotlight dramático) sobre el rostro
- Los rasgos faciales se mantienen pero se "adaptan" al estilo del ambiente
- La identidad es recognoscible pero requiere comparación con la foto original
- El cyberpunk fue el más agresivo por la iluminación de color mixto

**Cambios Fuertes (thinking_level: HIGH)**
- La transformación semántica domina sobre la preservación de identidad
- El modelo prioriza la coherencia histórica/contextual sobre los rasgos específicos
- El traje de astronauta oculta gran parte de la cara (solo visible por visor)
- El estilo 1920s (sepia, textura vintage) altera perceptualmente la apariencia
- El Tahuantinsuyo fue el más agresivo en términos de pérdida de identidad

---

## 5. Observaciones sobre preservación de identidad

### Casos donde la identidad se preserva bien
- Prompts de nivel **leve** con `thinking_level: MINIMAL` — el modelo interpreta la instrucción de forma conservadora y prioriza el mantenimiento de rasgos
- Prompts que especifican explícitamente `PRESERVE EXACTLY: the person's face` con descripción detallada de qué preservar
- Contextos de iluminación que no requieren cambiar la apariencia física del sujeto (solo el fondo)
- Escenas modernas y contemporáneas donde la ropa y el entorno son similares a la foto original

### Casos donde la identidad comienza a degradarse
- Al cambiar `thinking_level` a `HIGH` — el modelo tiene más "libertad creativa" para reinterpretar
- Prompts con cambios de vestimenta elaborados (trajes históricos, spacesuits)
- Estilos que requieren modificar el tono de piel o textura (vintage sepia, neon colorcast agresivo)
- Escenas futuristas donde el modelo añade elementos que parcialmente ocluyen el rostro

### Casos donde la identidad se pierde significativamente
- Transformaciones históricas (1920s, Inca) — el modelo adapta los rasgos al contexto cultural
- Astronauta con casco — la cara queda parcialmente oculta por el visor reflectante
- Escenas grupales — al combinar 3 personas, el modelo generaliza los rasgos para lograr coherencia

---

## 6. Dificultades en escenas con múltiples integrantes

La generación de escenas grupales presentó las siguientes dificultades:

**Técnicas:**
- El nodo `BatchImagesNode` requirió ser activado manualmente eliminando el estado "Bypass"
- Las imágenes de entrada no persisten entre sesiones/cuentas — deben recargarse
- El modelo no garantiza que cada persona del input corresponda a una posición específica en el output

**De identidad:**
- Al combinar 3 identidades distintas, el modelo tiende a "promediar" los rasgos faciales
- La coherencia de escala y perspectiva mejoró notablemente con prompts más detallados
- Se generaron 2 versiones de la escena de conferencia para obtener mejor resultado

**De composición:**
- Sin foto grupal de referencia, el modelo construye la composición desde cero basándose solo en el prompt
- La iluminación coherente entre los 3 sujetos fue el mayor desafío visual

---

## 7. Errores, limitaciones y observaciones del pipeline

### Limitaciones del modelo
- **Nano Banana 2 usa Gemini internamente** — no es Stable Diffusion puro, sino un modelo de edición de imágenes basado en LLM multimodal
- La **resolución máxima práctica es 1K** en el plan gratuito para mantener el costo por imagen bajo (~14-15 créditos)
- El modelo no tiene memoria entre generaciones — cada ejecución es independiente
- **No hay control explícito de denoise/CFG** como en SD clásico — el control es via lenguaje natural

### Limitaciones de la plataforma
- **Créditos limitados** — 400 créditos por cuenta gratuita (~28 imágenes a 1K)
- Las sesiones no persisten las imágenes subidas — al cambiar de cuenta hay que re-subir
- El workflow importado no carga automáticamente las imágenes de entrada

### Errores encontrados durante el lab
- **Error de máscara:** Al intentar usar el workflow `gsc_creator_2_2` (Inpainting + ControlNet), la máscara no se aplicaba correctamente y el modelo no modificaba el fondo. Se descartó este enfoque.
- **Bypass incorrecto:** El nodo `BatchImagesNode` estaba en estado Bypass por defecto y debía activarse manualmente via clic derecho → "Eliminar Bypass"
- **Incompatibilidad de formato:** Las fotos en formato `.HEIC` (iPhone) no son aceptadas por ComfyUI — requirieron conversión previa a `.JPEG`
- **Pérdida de contexto entre cuentas:** Al agotar créditos y cambiar de cuenta, el workflow JSON se importó correctamente pero las referencias a imágenes quedaron rotas

### Observaciones relevantes
- El `thinking_level: HIGH` no siempre produce mejores resultados — en algunos casos el modelo "sobrepiensa" y altera la identidad más de lo deseado
- Los prompts en inglés produjeron mejores resultados que en español
- Prompts más específicos y detallados (con secciones: BACKGROUND, LIGHTING, PRESERVE, QUALITY) generaron resultados notablemente superiores a prompts simples
- Para las escenas grupales, describir explícitamente la composición espacial ("two in front, one slightly behind") mejoró la coherencia visual

---

## 8. Estructura del repositorio

```
lab4-comfyui/
├── README.md
├── prompts.md
├── workflow_grupal_Lab04_DeepLearning.json
├── inputs/
│   ├── Miguel_Silva.jpeg
│   ├── Kelvin_Palomino.JPG
│   └── Paul_Sanchez.JPG
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
