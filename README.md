# 🎮 ETSIIT Game Jam 2026

> **Temática oficial:** 🏆 **«Ganar Perdiendo»** 💀  
> **Organiza:** GameDevClub — ETSIIT, Universidad de Granada  
> **Fechas:** 28 de octubre de 2026 – 20 de diciembre de 2026 *(Presentaciones en enero de 2027)*  
> **Modalidad y reuniones:** Híbrida (Presencial / Online) — Sesiones presenciales los **miércoles a las 19:30 h** en la ETSIIT (Aula 1.7)

¡Bienvenidos al repositorio central de la **ETSIIT Game Jam 2026**! Aquí encontraréis toda la información del evento, la plantilla oficial para los repositorios de los equipos, la guía de supervivencia con Git y los criterios de evaluación del jurado.

---

## 💡 La Temática: «Ganar Perdiendo»

El tema de esta edición es **«Ganar Perdiendo»**. Buscamos juegos donde la derrota, el sacrificio o la pérdida no sean un simple *Game Over*, sino la clave para avanzar o alzarse con la victoria.

---

## 🗂️ ¿Qué hay en este repositorio y cómo empezar?

Este repositorio actúa como **portal central de la Jam** y contiene en la carpeta [`template/`](./template) los archivos base que **todo equipo debe tener en la raíz de su repositorio**:

```text
gamedev-etsiit-jam-2026/
├── README.md                        # Este documento (información general y enlaces a equipos)
├── GUIA_GIT_Y_RUBRICA.md            # Guía de Git, chuleta de comandos y rúbrica completa de evaluación
└── template/                        # 📂 ARCHIVOS BASE PARA EL REPOSITORIO DE CADA EQUIPO
    ├── .gitattributes               # Normalización de saltos de línea y protección de binarios
    ├── README.md                    # Plantilla de README que debe rellenar cada equipo
    ├── CREDITS.md                   # Plantilla de créditos y licencias de assets de terceros
    └── gitignore-templates/         # Plantillas de .gitignore listas para usar
        ├── Unity.gitignore          # Para proyectos en Unity
        ├── Godot.gitignore          # Para proyectos en Godot 4.x / 3.x
        └── Cpp.gitignore            # Para proyectos en C/C++ (Raylib, SDL, SFML, CMake, VS)
```

### 🚀 Pasos en el Minuto 1 para los Equipos
1. Entrad al repositorio asignado a vuestro equipo (que tendrá el contenido de la carpeta [`template/`](./template) en su raíz).
2. **Leed obligatoriamente [`GUIA_GIT_Y_RUBRICA.md`](./GUIA_GIT_Y_RUBRICA.md)** antes de abrir Unity, Godot o vuestro IDE.
3. Seguid el **Paso 0**: elegid vuestro archivo dentro de `gitignore-templates/`, movedlo a la raíz de vuestro repositorio renombrado a `.gitignore`, borrad la carpeta `gitignore-templates/` y haced vuestro primer commit en `main`.

---

## 👥 Equipos Participantes y Proyectos

Participan **4 equipos de 4 integrantes**. A medida que empiece la Jam, se actualizarán aquí los enlaces a cada repositorio y su entrega final:

| Equipo | Nombre del Juego | Motor / Tecnología | Integrantes | Repositorio | Ejecutable (Release) |
| :--- | :--- | :---: | :--- | :---: | :---: |
| **Equipo 1** | *[Por anunciar]* | `[Unity / Godot / C++]` | `@NuMeRo-999`, `@ArekkMirMun`, `@darson1777`, `@fonchimango` | [🔗 Repo](#) | [📦 Release](#) |
| **Equipo 2** | *[Por anunciar]* | `[Unity / Godot / C++]` | `@leodct`, `@Rotwo`, `@MaestroDiablo`, `@TheAlacor` | [🔗 Repo](#) | [📦 Release](#) |
| **Equipo 3** | *[Por anunciar]* | `[Unity / Godot / C++]` | `@lmaoguy123`, `@ZeKuruu`, `@alvaro-co`, `@alopejin` | [🔗 Repo](#) | [📦 Release](#) |
| **Equipo 4** | *[Por anunciar]* | `[Unity / Godot / C++]` | `@DPR-code`, `@Jsangal`, `@Poxtax18`, `@MjrSheba` | [🔗 Repo](#) | [📦 Release](#) |

---

## 📅 Calendario e Hitos de la Jam

* **Miércoles 28 de octubre (19:30 h, Aula 1.5) — Inicio oficial y preparación de repositorios:** Arranca la Jam y configuramos los repositorios de los equipos en la sesión del GameDevClub.
* **Todos los miércoles (a partir de las 19:30 h, Aula 1.7) — Sesiones de trabajo y tutorías:** Reuniones presenciales en el GameDevClub para avanzar con el equipo, resolver dudas técnicas y revisar el estado de Git con el profesorado.
* **Domingo 20 de diciembre (hasta las 23:59 h, hora peninsular) — Fecha límite de entrega (`Release`):**
  * Último día para publicar la **Release final** en GitHub con el juego listo para **jugar en Linux** (vale tanto **versión Web** como **binario directo para Linux**).
  * ⚠️ **Importante:** **Únicamente se evaluará lo que esté publicado en la Release dentro de plazo** (al crear una Release en GitHub se adjunta automáticamente una copia exacta del repositorio en ese instante; cualquier commit posterior fuera de esa Release no será tenido en cuenta).
* **Enero de 2027 *(fecha exacta por confirmar)* — Presentaciones y Veredicto:** Exposición de los proyectos ante el jurado y anuncio de ganadores.

---

## 📜 Reglas Oficiales

1. **Temática:** Todos los proyectos deben basarse en la temática oficial: **«Ganar Perdiendo»**, cuya interpretación queda a libre criterio y creatividad de cada equipo.
2. **Fecha de inicio y desarrollo:** No está permitido presentar proyectos comenzados antes de la fecha de inicio oficial (**28 de octubre**). No obstante, se permite la reutilización de código base genérico o librerías/assets previamente existentes.
3. **Repositorio y entrega:** Los proyectos deben alojarse obligatoriamente en una plataforma basada en Git (como GitHub o GitLab) con el repositorio e historial de commits visible al profesorado para verificar el proceso de desarrollo. La entrega final en **Releases** debe poder **jugarse en Linux** (vale tanto **versión Web** como **binario directo para Linux**).
4. **Originalidad, juego limpio y trabajo en equipo:**
   * Queda terminantemente prohibido copiar código o assets de otros participantes, así como cualquier tipo de sabotaje hacia otros proyectos.
   * **La autoría debe ser estrictamente interna:** únicamente pueden colaborar en el proyecto los integrantes asignados al equipo por los profesores. Está prohibida la ayuda o desarrollo por parte de personas externas.
5. **Uso de assets y código externo:** Se permite el uso de código o recursos multimedia (modelos 3D, sprites, música, SFX) de terceros siempre que cuenten con la debida atribución y créditos a sus autores originales en `CREDITS.md`.
6. **Política de Inteligencia Artificial Generativa:**
   * **Código:** Se puede usar IA generativa como apoyo, pero la arquitectura, el diseño y la implementación deben ser ideados y comprendidos por el equipo.
   * **Arte y audio:** Se permite el uso de IA únicamente para ideación inicial, bocetos, *concept art* o *placeholders*. Todo asset incluido en la entrega final del proyecto debe contar con intervención y autoría humana, bajo la dirección creativa de los participantes.
7. **Conducta y privacidad:** Queda estrictamente prohibido cualquier contenido discriminatorio (por motivos de género, etnia, raza, religión, identidad u orientación sexual), así como la inclusión de datos personales o imágenes de personas reales sin su consentimiento explícito (salvo figuras públicas).

> ⚠️ **Penalización:** El incumplimiento de cualquiera de estas reglas supondrá la **descalificación inmediata** del equipo durante la evaluación.

---

## 💡 Recomendaciones para la Jam

1. **Aprendizaje colaborativo:** Los equipos han sido configurados para que los perfiles menos experimentados aprendan de aquellos con más recorrido en el uso de motores y herramientas. Recomendamos que sean los miembros con menos experiencia quienes tomen el teclado y utilicen directamente el software, contando con la mentoría y guía de sus compañeros.
2. **Uso pedagógico de la IA:** De igual modo, animamos a los participantes en formación a evitar el uso automático de IA generativa para maximizar la comprensión práctica del código, las mecánicas y los flujos de trabajo.
3. **Tutorías y resolución de dudas:** El profesorado estará disponible presencialmente para asesoraros, resolver problemas técnicos y revisar conceptos. Os recomendamos asistir al **Aula 1.7** los **miércoles a las 19:30 h**. ¡No tengáis reparo en preguntar!

---

## 📊 Evaluación y Jurado

La evaluación combina la valoración del jurado sobre el juego (Temática *«Ganar Perdiendo»*, Jugabilidad, Originalidad, Arte/Audio y Calidad Técnica) y una **evaluación técnica específica del uso de Git y limpieza del proyecto**.

* 🛠️ **[Guía de Git y Rúbrica de Evaluación Completa (`GUIA_GIT_Y_RUBRICA.md`)](./GUIA_GIT_Y_RUBRICA.md):** Incluye la configuración recomendada del repositorio, consejos para evitar conflictos en escenas, la rúbrica general del jurado y el desglose técnico de Git.