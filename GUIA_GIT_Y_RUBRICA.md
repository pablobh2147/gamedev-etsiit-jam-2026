# 🛠️ Guía Técnica y Criterios de Evaluación (Git)

Bienvenidos a la **ETSIIT Game Jam 2026**. El uso de control de versiones es **obligatorio y evaluable**. Este documento resume cómo configurar el repositorio en el minuto 1, cómo evitar conflictos trabajando 4 personas a la vez y qué se tendrá en cuenta en la nota técnica.

---

## 🚀 Paso 0: Inicialización (Hacer ANTES de crear el proyecto)

1. Id a la carpeta `gitignore-templates/` de este repositorio.
2. Copiad el archivo correspondiente a vuestro motor/lenguaje (`Unity.gitignore`, `Godot.gitignore` o `Cpp.gitignore`) a la **raíz del repositorio** y renombradlo exactamente a `.gitignore` (con el punto delante y **sin** extensión `.txt`).
   ```bash
   # Ejemplo por terminal (para Godot):
   cp gitignore-templates/Godot.gitignore .gitignore
   ```
3. Borrad la carpeta `gitignore-templates/`:
   ```bash
   rm -rf gitignore-templates/
   ```
4. **No borréis el archivo `.gitattributes`** que ya viene en la raíz: evita que Git rompa archivos binarios o cree conflictos falsos de saltos de línea entre Windows y Linux/macOS.
5. Haced vuestro primer commit y subidlo a `main`:
   ```bash
   git add .gitignore .gitattributes gitignore-templates/
   git commit -m "chore: configurar gitignore inicial del proyecto"
   git push origin main
   ```
6. **IMPORTANTE (Especialmente en Unity):**
   * Cread el proyecto directamente en la raíz de este repositorio (o aseguraos de que el `.gitignore` esté configurado antes del primer `git add`).
   * En Unity, comprobad en `Edit > Project Settings > Editor` que **Asset Serialization Mode** esté en **`Force Text`** y **Version Control Mode** en **`Visible Meta Files`** (viene así por defecto en versiones recientes).
   * **Subid siempre los archivos `.meta`** junto con cada carpeta, script o sprite. Si ignoráis o no subís los `.meta`, a vuestros compañeros se les romperán todos los enlaces e iconos en el editor.

---

## 🌿 Normas de Flujo de Trabajo durante la Jam

* **`main` es sagrada:** La rama `main` siempre debe compilar y ejecutar sin errores.
* **Trabajo en ramas:** Cread ramas breves para cada tarea (ej. `feat/movimiento`, `fix/menu-pausa`, `art/sprites-jugador`) e integradlas en `main` mediante **Pull Requests (PR)** o merges limpios.
* **Mensajes de commit con sentido:** Usad mensajes cortos que expliquen qué habéis hecho. Se recomienda usar prefijos:
  * `feat:` nueva mecánica o funcionalidad.
  * `fix:` corrección de un bug.
  * `art:` / `audio:` subida de recursos visuales o sonoros.
  * `docs:` cambios en el `README.md`, `CREDITS.md` o documentación.
  * `chore:` configuración del proyecto o limpieza.
* **Archivos pesados:** No subáis archivos fuente pesados (`.psd`, `.blend`, proyectos de audio brutos) al repositorio. Guardadlos en Drive y subid a Git únicamente los assets finales exportados (`.png`, `.ogg`, `.fbx`, `.glb`).

---

## 🎮 Supervivencia en Equipos de 4: Cómo NO romper las Escenas

El problema número 1 en una Game Jam es que **dos personas editen la misma escena (`.unity` o `.tscn`) a la vez**. Aunque sean archivos de texto, fusionar una escena a mano suele corromperla.

1. **Una escena de pruebas por persona (al principio):** Mientras programáis mecánicas separadas (movimiento, enemigos, UI), trabajad en escenas separadas (ej. `test_jugador.tscn`, `test_enemigos.tscn`).
2. **Todo es un Prefab (Unity) o una Sub-escena (Godot):**
   * El jugador, el HUD, los enemigos y los obstáculos deben ser sus propios **Prefabs** (`.prefab`) o **Escenas instanciadas** (`.tscn`) independientes.
   * Así, una persona puede editar el prefab del enemigo mientras otra edita el prefab de la interfaz sin tocar el nivel principal al mismo tiempo.
3. **Regla del micrófono / aviso:** Antes de tocar la escena principal (`Main.unity` / `main.tscn`) o el `project.godot` / `ProjectSettings`, avisad al equipo: *"Voy a tocar la escena principal 5 minutos, no la editéis hasta que haga push"*.

---

## 🛟 Chuleta de Git y "Botón del Pánico"

### Flujo habitual de una tarea
```bash
# 1. Asegurarte de tener lo último de main
git switch main
git pull origin main

# 2. Crear tu rama para la tarea
git switch -c feat/sistema-puntos

# 3. Ver qué archivos vas a subir (¡revisa que no haya basura!)
git status

# 4. Guardar cambios y subir la rama
git add .
git commit -m "feat: implementar sistema de puntuación al perder vida"
git push -u origin feat/sistema-puntos
# -> Ahora abre el Pull Request en GitHub y haz Merge a main
```

### 🚨 "¡Socorro! He subido `Library/`, `.godot/` o `build/` sin querer"
Si olvidasteis el `.gitignore` y habéis subido una carpeta de caché a Git:
```bash
# 1. Asegúrate de que el .gitignore ya está bien puesto en la raíz
# 2. Borra la carpeta del seguimiento de Git (SIN borrarla de tu disco duro):
git rm -r --cached Library/      # En Unity (o .godot/ en Godot, o build/ en C++)
git commit -m "chore: eliminar carpeta de cache del repositorio"
git push
```

### 🚨 "¡Socorro! Tengo un conflicto (CONFLICT) en una escena o archivo binario"
No intentéis resolver a mano las marcas `<<<<<<< HEAD` dentro de un archivo `.unity`, `.prefab` o `.tscn` complejo, porque el motor dejará de abrirlo. Elegid cuál de las dos versiones conservar y rehaced el cambio pequeño en el editor:
```bash
# Opción A: Quedarme con la versión que había en mi rama actual
git checkout --ours ruta/a/la/escena.tscn
git add ruta/a/la/escena.tscn

# Opción B: Quedarme con la versión que viene de la otra rama (ej. main)
git checkout --theirs ruta/a/la/escena.tscn
git add ruta/a/la/escena.tscn
```

### 📦 Cómo entregar el Ejecutable en GitHub Releases (Antes del 20 de diciembre a las 23:59 h)
> ⚠️ **MUY IMPORTANTE:** Únicamente se evaluará lo que esté publicado en la **Release** antes del cierre (**20 de diciembre a las 23:59 h, hora peninsular**). Al publicar una Release en GitHub, se congela automáticamente una copia del código fuente en ese tag (`v1.0.0`); cualquier commit posterior fuera de la Release no entrará en la evaluación.

**NUNCA** subáis el `.zip` o binario final haciendo `git add` al código. Para entregar:
1. Aseguraos de que todos vuestros cambios, `README.md` y `CREDITS.md` están subidos a la rama `main`.
2. **Requisito de plataforma:** El juego **debe poder jugarse en Linux**, para lo cual **vale tanto una versión Web como un binario directo para Linux**. Exportad/compilad vuestro juego en una carpeta limpia fuera del repo y comprimid todos los archivos necesarios en un `.zip`.
   * *Ojo en Unity:* Instalad el módulo *Linux Build Support* o *WebGL* en Unity Hub. Si exportáis binario para Linux, el `.zip` debe incluir tanto el ejecutable como la carpeta `Nombre_Data/` y `MonoBleedingEdge/` (si existe).
   * *Ojo en Godot:* Exportad con el preset de *Linux* (incluyendo el binario y el `.pck`, o activando *Embed PCK*) o *Web*.
3. En la página de vuestro repositorio de GitHub, id a la columna derecha -> **Releases** -> **Create a new release**.
4. En **Choose a tag**, escribid `v1.0.0` (apuntando a `main`) y pulsad **Create new tag: v1.0.0 on publish**.
5. Poned título a la entrega, arrastrad vuestro archivo `.zip` a la caja de binarios y pulsad **Publish release**.

---

## 📊 Rúbrica de Evaluación de la Jam

La evaluación combina la valoración general del jurado sobre el juego y la evaluación técnica del repositorio y flujo de trabajo con Git.

### 1. Criterios Generales del Jurado `[BORRADOR — PESOS EDITABLES]`

> *Nota: Los pesos de los bloques generales son orientativos (`[EDITAR SEGÚN ACUERDO DEL JURADO]`).*

| Bloque | Peso Global Sugerido | ¿Qué valora el jurado? | Preguntas guía |
| :--- | :---: | :--- | :--- |
| **1. Temática: «Ganar Perdiendo»** | **[25%]** | Integración real del tema en las mecánicas o en el núcleo del juego (no solo como excusa en el texto inicial). | *¿Perder recursos, vida, habilidades o partidas es realmente la forma de progresar o ganar? ¿Es ingeniosa la interpretación?* |
| **2. Jugabilidad y Diversión (*Game Feel*)** | **[25%]** | Controles cómodos, claridad del objetivo, curva de dificultad razonable y satisfacción al jugar. | *¿Se entiende qué hay que hacer sin leer un manual largo? ¿Responde bien el control?* |
| **3. Originalidad y Diseño de Juego** | **[15%]** | Creatividad de la propuesta, diseño de niveles/retos y frescura de la idea dentro del tiempo límite. | *¿Aporta algún giro sorprendente o mecánica memorable?* |
| **4. Arte, Audio y Ambientación** | **[15%]** | Cohesión visual, interfaz legible (UI), efectos de sonido (feedback al jugador) y música. | *¿Tiene personalidad visual/sonora? ¿El sonido y los efectos ayudan a entender qué pasa en pantalla?* |
| **5. Evaluación Técnica y Git** | **[20%]** | Uso de Git en equipo, higiene del repositorio, documentación (`README`/`CREDITS`) y entrega en Releases. | *Evaluado según el desglose técnico de la tabla siguiente.* |

### 2. Desglose de la Evaluación Técnica (Git y Limpieza)

| Criterio Técnico | Peso (sobre nota técnica) | ¿Qué se revisa exactamente? |
| :--- | :---: | :--- |
| **2.1. Higiene del Repo** | **30%** | Que el `.gitignore` y `.gitattributes` estén activos desde el inicio y no existan carpetas de caché o compilación subidas (`Library/`, `.godot/`, `venv/`, `build/`, `.vs/`, ejecutables o `.zip` sueltos en el árbol de código). |
| **2.2. Participación** | **30%** | Que el historial refleje commits reales de los integrantes técnicos del grupo (no vale que una sola persona suba el trabajo de todos desde su PC al final). |
| **2.3. Historial y Ramas** | **20%** | Commits frecuentes e incrementales (no un único commit gigante el último día), mensajes descriptivos (evitar *"asdf"*, *"cambios"*, *"ahora si"*) y uso básico de ramas/PRs. |
| **2.4. Entrega y Documentación** | **20%** | `README.md` y `CREDITS.md` completados (controles, integrantes, cómo abrir/compilar el juego) y entrega final **jugable en Linux (versión Web o binario directo)** subida en el apartado **Releases** de GitHub bajo un tag (ej. `v1.0.0`) antes del 20 de diciembre a las 23:59 h. |