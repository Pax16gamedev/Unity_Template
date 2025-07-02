# Unity Template Repository

## Descripción
Este repositorio es una plantilla diseñada para agilizar el inicio de nuevos proyectos en Unity. Incluye configuraciones predefinidas, workflows de CI/CD mediante GitHub Actions y buenas prácticas para el desarrollo.

---

## Características principales
- ✨ **Estructura básica del proyecto**: Configuraciones iniciales para Unity.
- 🚀 **Workflows preconfigurados**: Automatización de builds para WebGL y Standalone Windows.
- 🌐 **Compatibilidad con GitHub Pages**: Despliegue directo de builds WebGL.
- 🔔 **Integración con Discord**: Notificaciones automáticas sobre el estado de las builds.
- 🛠 **.gitignore optimizado**: Diseñado para Unity para evitar archivos innecesarios en el control de versiones.
- 🕹️ **Despliegue opcional a directamente a Itch.io**: Sube automáticamente las builds generadas con WebGL directamente a tu proyecto de Itch.io

---

## Uso de la plantilla

### 1. Crear un nuevo repositorio desde esta plantilla
1. 🖱 Haz clic en el botón **"Use this template"** en la página principal del repositorio.
2. 📝 Asigna un nombre a tu nuevo repositorio y selecciona si quieres que sea público o privado.
3. 🚀 Haz clic en **"Create repository from template"**.
4. 🚫 No clonar con todas las ramas, porque se van a ejecutar todos los actions.
   1. La rama default y principal debe llamarse "**DESARROLLO**"
   2. Crear a posteriori las ramas de "**PRE_PRODUCCION**", "**PRODUCCION**"

### 2. Clonar el repositorio
En tu terminal, clona el nuevo repositorio:
```bash
git clone https://github.com/<tu_usuario>/<tu_repositorio>.git
```

### 3. Abrir en Unity
1. 🎮 Abre Unity Hub.
2. 📂 Selecciona **Add project** y navega hasta la carpeta donde clonaste el repositorio.
3. ▶️ Selecciona el proyecto y ábrelo.

### 4. Dar permisos a los actions de los workflows
- Settings > Actions > General
  - Actions permissions > Allow all actions and reusable workflows
  - Workflow permissions > Read and write permissions

### 5. Configurar Workflows
Si deseas utilizar los workflows de CI/CD:
1. ⚙️ Ve a **Settings > Secrets and variables > Actions - Secrets** en GitHub.
2. 🔑 Agrega los siguientes secretos:
   - `UNITY_EMAIL`:Email de acceso a Unity para activación.
   - `UNITY_PASSWORD`: Contraseña de acceso a Unity para activación.
   - `UNITY_LICENSE`: Licencia de Unity para activación.
   - `DISCORD_WEBHOOK_URL`: URL del webhook del canal de texto para notificaciones en Discord.
3. También se recomienda(aunque opcional) establecer las variables (Actions - Variables)
   - `UNITY_VERSION`
   - `PROJECT_NAME`
4. Opcionalmente, para la build de **WebGL**, se puede configurar para que se suba directamente a Itch.io. Para ello:
   1. Se debe generar y guardar la API Key [Generar API Key](https://itch.io/user/settings/api-keys)
   2. Añadir como secreto `ITCHIO_API_KEY`
   3. Añadir como variable `ITCHIO_CHANNEL` en formato **usuario/juego:canal**. 
      Por defecto: *pax16/test_devops:webgl*. Esto subirá el proyecto al canal webgl del juego roguelike, en la cuenta pax16.
   4. Se generará automáticamente la URL pública del juego como: https://usuario.itch.io/juego

> [!IMPORTANT]  
> Para que el juego se suba, el proyecto ya debe estar creado en la página de Itch.io.

>[¿Cómo consigo `UNITY_LICENSE`?](https://game.ci/docs/github/activation#personal-license)
---

## Workflows disponibles

### 1. **Build para Standalone Windows**
Este workflow genera una build para Windows y la sube como un artefacto descargable.

#### Descarga del artefacto:
1. 🛠 Ve a la sección **Actions** en GitHub.
2. 📂 Selecciona el flujo ejecutado.
3. ⬇️ Descarga el archivo de la build desde los artefactos generados.

### 2. **Build para WebGL**
Este workflow genera una build de Unity para WebGL y la despliega automáticamente en GitHub Pages.

- 🔗 El enlace estará disponible en:
  ```
  https://<tu_usuario>.github.io/<tu_repositorio>/$nombre_proyecto
  ```

#### Ejecución manual:
Puedes ejecutar el workflow desde la pestaña **Actions** en GitHub seleccionando el flujo **WebGL Build**.

### 3. **Notificaciones a Discord**
Recibe notificaciones en Discord con información sobre el estado de las builds, incluyendo:
- 📊 Estado: Éxito o fallo.
- ⏱ Tiempo de ejecución.
- 🔗 Enlace directo a la build (en el caso de WebGL).

### 4. Auto-assign reviewers
Configura automáticamente revisores para los Pull Requests abiertos en el repositorio. Esto asegura que cada cambio propuesto sea evaluado de manera eficiente.

### 5. Labeler de etiquetas
Este workflow asigna automáticamente etiquetas relevantes a los Pull Requests según su contenido. Por ejemplo: bugfix, enhancement, etc.

> [!IMPORTANT]  
> Los labels deben estar creados en la pestaña de *Issues*.
> Labels: documentation, feature, bugfix, enhancement, release
> Las etiquetas se aplican automáticamente si las ramas siguen el formato `feature/`, `bugfix/`, etc.


### 6. Plantilla de Pull Requests

El repositorio incluye un archivo predefinido para estandarizar las descripciones de los Pull Requests y facilitar la comunicación entre los desarrolladores.

### 7. Release Drafter

Automatiza la creación de notas de lanzamiento al generar un borrador con todos los cambios incluidos desde la última versión publicada. Esto agiliza el proceso de documentación de nuevas versiones.

---

## Estructura del proyecto
```
.github/            # Configuraciones de workflows de GitHub Actions
.github/workflows   # Configuraciones de workflows de GitHub Actions
```

---

## Propuesta de trabajo
### Pull Requests
🗺️ Pasos

1. **Crea una rama** con prefijos como `feature/`, `bugfix/`, etc. Ejemplo: `feature/add-controller` (De modo que las ramas se autoetiqueten con *labeler*).
2. **Haz commits descriptivos**: `Add player controller with new input system`.
3. **Mantén tu rama actualizada con DESARROLLO**.
4. **Abre una PR** con detalles claros y enfocado en un solo cambio.
5. Responde a los comentarios de los revisores, dado el caso.
6. La PR se fusionará tras pasar verificaciones (no impiden el merge). 🚀


## Licencia
Este proyecto utiliza la licencia MIT. Consulta el archivo [LICENSE](./LICENSE) para más detalles.

---

## Contribuciones
¡🌟 Las contribuciones son bienvenidas! Si tienes sugerencias o mejoras, crea un Issue o un Pull Request. 🛠

---

## Autor
Plantilla creada por [pax16gamedev](https://github.com/Pax16gamedev).

---
## Errores conocidos con despliegue de WebGL en GH Pages
> [!IMPORTANT]  
> No olvidar que para funcione GH Pages el repositorio debe ser público.

### Error de parseo
> Unable to parse Build/Roguelike.framework.js.br! This can happen if build compression was enabled but web server hosting the content was misconfigured to not serve the file with HTTP Response Header "Content-Encoding: br" present. Check browser Console and Devtools Network tab to debug.

#### Posibles soluciones: 

##### Deshabilitar la compresión en Unity
Esta es la solución más sencilla si no puedes configurar los encabezados HTTP en el servidor (como ocurre con GitHub Pages).

1. Abre tu proyecto de Unity.
2. Ve a File > Build Settings > Player Settings.
3. En la sección Publishing Settings, busca la opción Compression Format.
4. Selecciona Disabled en lugar de Brotli o Gzip.
5. Vuelve a generar la build y sube los nuevos archivos a GitHub Pages.

##### Habilitar Unity Loader para manejar compresión
Unity puede manejar la descompresión de los archivos si activas la opción de "Decompression Fallback". Esto requiere un pequeño ajuste en Unity:

1. Abre File > Build Settings > Player Settings.
2. En Publishing Settings, habilita la opción Decompression Fallback.
3. Genera nuevamente la build.
4. Sube los nuevos archivos a GitHub Pages.
5. Esto permite que Unity descargue los archivos comprimidos y los descomprima directamente en el navegador, eliminando la dependencia del encabezado Content-Encoding.
