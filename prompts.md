# Prompts y Configuraciones — Lab 4 ComfyUI

## Herramienta
- **Plataforma:** cloud.comfy.org (ComfyUI Cloud)
- **Modelo:** Nano Banana 2 (Gemini 3.1 Flash Image)
- **Resolución:** 1K en todas las generaciones
- **Aspect Ratio:** auto

---

## Configuración por nivel de transformación

| Nivel | thinking_level | Descripción |
|---|---|---|
| Leve | MINIMAL | Cambios conservadores — preserva identidad |
| Moderado | HIGH | Cambios de estilo marcados |
| Fuerte | HIGH | Transformación semántica agresiva |

---

## Prompt negativo universal (system prompt interno del modelo)
```
You are an expert image-generation engine. You must ALWAYS produce an image.
Interpret all user input—regardless of format, intent, or abstraction—as literal 
visual directives for image composition. If a prompt is conversational or lacks 
specific visual details, you must creatively invent a concrete visual scenario 
that depicts the concept. Prioritize generating the visual representation above 
any text, formatting, or conversational requests.
```

---

## MIGUEL SILVA — Prompts individuales

### 🟢 NIVEL LEVE (thinking_level: MINIMAL)

**miguel_leve_01_studio.png**
```
Edit this portrait photo with the following precise instructions:
BACKGROUND: Replace the entire background with a seamless professional 
photography studio backdrop in neutral warm gray (#808080). Add subtle 
gradient from slightly lighter at top to darker at bottom.
LIGHTING: Add professional three-point lighting setup — soft key light 
from upper left at 45 degrees, subtle fill light from right, and a rim 
light behind creating a thin bright edge along the left shoulder and hair.
PRESERVE EXACTLY: the person's face, facial structure, skin tone, eye 
color, hair style, hair color, expression, and clothing. Do not alter 
any facial features whatsoever.
QUALITY: photorealistic, sharp focus, high-end portrait photography, 
85mm lens look, shallow depth of field on background only.
```

**miguel_leve_02_golden.png**
```
Edit this portrait photo with the following precise instructions:
BACKGROUND: Replace background with a soft-focus outdoor scene during 
golden hour — blurred warm bokeh of trees and open sky, sun positioned 
low behind and to the right of the subject creating a natural backlight.
LIGHTING: Apply warm golden sunlight (color temperature 3200K) falling 
on the face from the right side, creating soft warm highlights on skin 
and hair. Add subtle atmospheric haze. Natural rim light from the sun 
creating a golden glow around the hair edges.
PRESERVE EXACTLY: the person's face, facial structure, skin tone, hair, 
expression, and clothing unchanged.
QUALITY: photorealistic outdoor portrait, Canon 5D look, natural 
photography, cinematic color grading with warm tones.
```

**miguel_leve_03_oficina.png**
```
Edit this portrait photo with the following precise instructions:
BACKGROUND: Replace background with a modern corporate office environment 
— floor-to-ceiling glass windows behind showing a blurred city skyline, 
clean minimalist workspace, professional environment.
LIGHTING: Natural window light coming from behind and to the left, 
creating soft professional illumination on the face. Cool natural daylight 
temperature. Add subtle reflection of city lights in background.
PRESERVE EXACTLY: the person's face, all facial features, expression, 
skin tone, hair, and clothing completely unchanged.
QUALITY: professional corporate headshot, sharp face, blurred background, 
LinkedIn profile photo aesthetic, photorealistic.
```

---

### 🟡 NIVEL MODERADO (thinking_level: HIGH)

**miguel_moderado_01_futurista.png**
```
Edit this portrait photo with the following precise instructions:
ENVIRONMENT: Place the person inside a cutting-edge futuristic AI research 
laboratory. Background shows multiple holographic blue displays with data 
visualizations, neural network diagrams floating in air, server racks with 
blue LED strips, and a sleek high-tech workstation.
LIGHTING: Dramatic blue-tinted ambient lighting from the holographic 
screens, creating cool blue and cyan highlights on the face and shoulders. 
Add subtle purple accent light from below. Dark atmospheric environment 
with the person lit primarily by screen glow.
CLOTHING: Add a modern tech researcher aesthetic — keep base clothing but 
optionally add a clean white lab coat or smart casual tech company attire.
PRESERVE: the person's face, facial features, skin tone, and identity 
must remain clearly recognizable despite the environmental changes.
QUALITY: cinematic sci-fi photography, shallow depth of field, 
photorealistic, high detail on face, Blade Runner 2049 aesthetic.
```

**miguel_moderado_02_cyberpunk.png**
```
Edit this portrait photo with the following precise instructions:
ENVIRONMENT: Place the person on a rainy cyberpunk city street at night. 
Background shows neon signs in Japanese and English, wet reflective 
pavement, steam rising from grates, dense urban architecture, 
advertisement holograms.
LIGHTING: Apply dramatic mixed neon lighting — strong red neon from the 
left casting red highlights, blue neon from right creating cool contrast. 
Rain droplets visible in foreground light. Wet skin and hair from light 
rain. Reflections of neon lights visible in the eyes.
ATMOSPHERE: Add light rain effect, atmospheric fog, cinematic color 
grading with teal and orange contrast pushed hard.
PRESERVE: the person's face structure and identity must be recognizable — 
same person, same features, transported into this world.
QUALITY: cinematic photography, Blade Runner aesthetic, f/1.4 look, 
photorealistic neon reflections, ultra detailed.
```

**miguel_moderado_03_editorial.png**
```
Edit this portrait photo with the following precise instructions:
ENVIRONMENT: Transform into a high-fashion editorial magazine spread. 
Background is a dramatic dark studio with one strong spotlight creating 
a theatrical circular light pool. Vogue or GQ magazine aesthetic.
LIGHTING: Single dramatic overhead spotlight with hard shadows, creating 
high-contrast chiaroscuro effect. Deep shadows on one side of face, 
strong highlights on the other. Cinematic and bold.
STYLING: Enhance overall image quality to match luxury fashion photography 
standards. Add subtle skin retouching while keeping natural look.
PRESERVE: the person's facial identity, bone structure, and recognizable 
features must remain intact.
QUALITY: medium format camera look, Hasselblad aesthetic, editorial 
fashion photography, sharp, high-end magazine quality.
```

---

### 🔴 NIVEL FUERTE (thinking_level: HIGH)

**miguel_fuerte_01_1920s.png**
```
Edit this portrait photo with the following creative transformation:
ERA: Transform into an authentic 1920s vintage photograph of a scientist.
ENVIRONMENT: Classic early 20th century research laboratory — wooden 
furniture, glass chemistry equipment, antique scientific instruments, 
chalkboard with equations in background.
STYLING: Dress the person in period-appropriate formal attire — white 
dress shirt, suspenders, bow tie, formal vest typical of 1920s academics.
PHOTO TREATMENT: Apply authentic vintage photograph effect — sepia tone, 
subtle grain and film damage, slight vignette, reduced contrast typical 
of period photography. Simulate aged photographic paper texture.
IDENTITY: Push the transformation aggressively toward the 1920s aesthetic 
while attempting to maintain some facial resemblance to the original person.
QUALITY: authentic vintage photograph simulation, historically accurate, 
dramatic and cinematic.
```

**miguel_fuerte_02_inca.png**
```
Edit this portrait photo with the following creative transformation:
ERA & SETTING: Transform into a dramatic scene set in the ancient Inca 
Empire (Tahuantinsuyo), approximately 1400-1500 AD. Location: the sacred 
city of Machu Picchu or Cusco, with massive stone architecture, terraced 
mountains, and dramatic Andean sky with clouds.
STYLING: Dress the person in authentic Inca noble or warrior attire — 
colorful woven tunic (uncu) with geometric patterns in red, gold and 
black, ceremonial golden chest plate (topayauri), elaborate feathered 
headdress, golden ear ornaments (orejones).
LIGHTING: Dramatic natural Andean high-altitude sunlight, strong shadows, 
golden late afternoon light on ancient stone ruins.
ATMOSPHERE: Epic and majestic — convey the grandeur of the Inca 
civilization. Add atmospheric mountain mist in background.
IDENTITY: Transform the person into this historical context, pushing the 
visual style aggressively while exploring identity limits.
QUALITY: cinematic, epic historical drama, photorealistic, National 
Geographic quality photography.
```

**miguel_fuerte_03_luna.png**
```
Edit this portrait photo with the following creative transformation:
SETTING: Place the person on the lunar surface during the Apollo era or 
near-future Moon mission. Barren lunar landscape with grey regolith, 
multiple craters visible, dramatic black space sky with brilliant stars, 
Earth rising on the horizon showing continents and clouds.
SUIT: Dress the person in a detailed NASA-style spacesuit — white EMU 
suit with visible mission patches, gold-visor helmet partially open or 
reflecting the lunar landscape, life support backpack (PLSS).
LIGHTING: Harsh unfiltered sunlight from the side creating extreme 
contrast — very bright highlights on suit, deep black shadows, no 
atmospheric scattering. Earth provides subtle blue fill light.
IDENTITY: This is maximum transformation — the spacesuit dominates but 
the person's face should still be visible through the helmet visor, 
exploring the absolute limit of identity preservation.
QUALITY: NASA photography quality, ultra-realistic, sharp, dramatic 
space photography aesthetic, IMAX quality.
```

---

## KELVIN PALOMINO — Prompts individuales

### 🟢 NIVEL LEVE (thinking_level: MINIMAL)
**kelvin_leve_01_studio.png** → mismo prompt que miguel_leve_01_studio
**kelvin_leve_03_oficina.png** → mismo prompt que miguel_leve_03_oficina

### 🟡 NIVEL MODERADO (thinking_level: HIGH)
**kelvin_moderado_01_futurista.png** → mismo prompt que miguel_moderado_01_futurista
**kelvin_moderado_03_editorial.png** → mismo prompt que miguel_moderado_03_editorial

### 🔴 NIVEL FUERTE (thinking_level: HIGH)
**kelvin_fuerte_01_1920s.png** → mismo prompt que miguel_fuerte_01_1920s
**kelvin_fuerte_03_luna.png** → mismo prompt que miguel_fuerte_03_luna

---

## PAUL SANCHEZ — Prompts individuales

### 🟢 NIVEL LEVE (thinking_level: MINIMAL)
**paul_leve_01_studio.png** → mismo prompt que miguel_leve_01_studio
**paul_leve_03_oficina.png** → mismo prompt que miguel_leve_03_oficina

### 🟡 NIVEL MODERADO (thinking_level: HIGH)
**paul_moderado_01_futurista.png** → mismo prompt que miguel_moderado_01_futurista
**paul_moderado_03_editorial.png** → mismo prompt que miguel_moderado_03_editorial

### 🔴 NIVEL FUERTE (thinking_level: HIGH)
**paul_fuerte_01_1920s.png** → mismo prompt que miguel_fuerte_01_1920s
**paul_fuerte_03_luna.png** → mismo prompt que miguel_fuerte_03_luna

---

## ESCENAS GRUPALES — Prompts

### grupal_01_equipo_ia.png (thinking_level: HIGH)
```
I am providing 3 separate photos of 3 real people. Combine all three 
people into a single coherent group scene as an AI research team in a 
futuristic laboratory.

Place all three people together in one unified image:
- Natural group composition, all three visible and recognizable
- Background: futuristic AI laboratory with holographic blue displays, 
  server racks with LED lights
- All three wearing professional tech researcher attire
- Coherent lighting, scale and perspective across all three people
- They are standing/sitting together as colleagues
- Photorealistic, cinematic quality, sharp faces

IMPORTANT: Preserve the facial identity of each person from their 
respective input photos.
```

### grupal_02_conferenciaV1.png / grupal_02_conferenciaV2.png (thinking_level: HIGH)
```
I am providing 3 separate input photos of 3 real Latin American male 
researchers. Your task is to combine all three people into ONE single 
unified photorealistic scene.

SCENE: International AI academic conference. A professional stage with 
a large LED screen behind displaying "International AI Conference 2025". 
Three podiums with microphones arranged in a row. Professional conference 
hall with audience seats visible in background, dramatic stage lighting.

COMPOSITION: All three men standing behind their respective podiums, 
facing the camera, professional and confident posture. Natural spacing 
between them. They appear as keynote speakers presenting their research.

PEOPLE: Place each of the 3 input persons at one podium each. 
Dress them in formal academic attire — suits or smart blazers.

LIGHTING: Professional stage lighting from above, warm spotlight on 
each speaker, subtle blue ambient from LED screen behind.

IDENTITY: Make maximum effort to preserve the facial features and 
identity of each of the 3 input persons in the final composition.

QUALITY: Photorealistic, sharp faces, 4K quality, professional 
conference photography aesthetic, coherent scale and perspective 
across all three people.
```

### grupal_03_marte.png (thinking_level: HIGH)
```
I am providing 3 separate input photos of 3 real Latin American male 
researchers. Your task is to combine all three people into ONE single 
unified photorealistic scene.

SCENE: The surface of Mars during a near-future crewed mission. 
Dramatic Martian landscape with reddish-orange rocky terrain, 
scattered boulders, and a vast canyon visible in the distance. 
The sky is a hazy pinkish-orange with two small moons visible. 
A base habitat module visible in the far background.

COMPOSITION: All three astronauts standing together as a crew, 
facing the camera for a group portrait. Natural group formation — 
two in front, one slightly behind, or all three side by side. 
They appear proud and heroic, documenting a historic moment.

SPACESUITS: Each person wearing a next-generation NASA/ESA style 
spacesuit — white with mission patches, transparent visor showing 
the face clearly, life support backpack. Each suit has subtle 
color differences to distinguish the crew members.

LIGHTING: Harsh unfiltered Martian sunlight from upper right, 
creating strong directional shadows. Warm orange ambient light 
from the terrain reflecting on the suits. No atmospheric diffusion.

IDENTITY: Make maximum effort to preserve the facial features of 
each of the 3 input persons visible through their helmet visors.

QUALITY: Photorealistic, IMAX cinematic quality, sharp detail on 
faces and suits, epic space exploration photography, coherent 
lighting and scale across all three astronauts, National Geographic 
quality composition.
```
