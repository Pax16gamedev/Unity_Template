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

---

## Uso de la plantilla

### 1. Crear un nuevo repositorio desde esta plantilla
1. 🖱 Haz clic en el botón **"Use this template"** en la página principal del repositorio.
2. 📝 Asigna un nombre a tu nuevo repositorio y selecciona si quieres que sea público o privado.
3. 🚀 Haz clic en **"Create repository from template"**.

### 2. Clonar el repositorio
En tu terminal, clona el nuevo repositorio:
```bash
git clone https://github.com/<tu_usuario>/<tu_repositorio>.git
```

### 3. Abrir en Unity
1. 🎮 Abre Unity Hub.
2. 📂 Selecciona **Add project** y navega hasta la carpeta donde clonaste el repositorio.
3. ▶️ Selecciona el proyecto y ábrelo.

### 4. Configurar Workflows
Si deseas utilizar los workflows de CI/CD:
1. ⚙️ Ve a **Settings > Secrets and variables > Actions** en GitHub.
2. 🔑 Agrega los siguientes secretos:
   - `UNITY_EMAIL`:Email de acceso a Unity para activación.
   - `UNITY_PASSWORD`: Contraseña de acceso a Unity para activación.
   - `UNITY_LICENSE`: Licencia de Unity para activación.
   - `DISCORD_WEBHOOK_URL`: URL del webhook para notificaciones en Discord.

>[¿Cómo consigo `UNITY_LICENSE`?](https://game.ci/docs/github/activation#personal-license)
---

## Workflows disponibles

### 1. **Build para WebGL**
Este workflow genera una build de Unity para WebGL y la despliega automáticamente en GitHub Pages.

- 🔗 El enlace estará disponible en:
  ```
  https://<tu_usuario>.github.io/<tu_repositorio>/$nombre_proyecto
  ```

#### Ejecución manual:
Puedes ejecutar el workflow desde la pestaña **Actions** en GitHub seleccionando el flujo **WebGL Build**.

### 2. **Build para Standalone Windows**
Este workflow genera una build para Windows y la sube como un artefacto descargable.

#### Descarga del artefacto:
1. 🛠 Ve a la sección **Actions** en GitHub.
2. 📂 Selecciona el flujo ejecutado.
3. ⬇️ Descarga el archivo de la build desde los artefactos generados.

### 3. **Notificaciones a Discord**
Recibe notificaciones en Discord con información sobre el estado de las builds, incluyendo:
- 📊 Estado: Éxito o fallo.
- ⏱ Tiempo de ejecución.
- 🔗 Enlace directo a la build (en el caso de WebGL).

### 4. Auto-assign reviewers

Configura automáticamente revisores para los Pull Requests abiertos en el repositorio. Esto asegura que cada cambio propuesto sea evaluado de manera eficiente.

### 5. Labeler de etiquetas

Este workflow asigna automáticamente etiquetas relevantes a los Pull Requests según su contenido. Por ejemplo: bugfix, enhancement, etc.

### 6. Plantilla de Pull Requests

El repositorio incluye un archivo predefinido para estandarizar las descripciones de los Pull Requests y facilitar la comunicación entre los desarrolladores.

### 7. Release Drafter

Automatiza la creación de notas de lanzamiento al generar un borrador con todos los cambios incluidos desde la última versión publicada. Esto agiliza el proceso de documentación de nuevas versiones.

---

## Estructura del proyecto
```
.github/         # Configuraciones de workflows de GitHub Actions
```

---

## Licencia
Este proyecto utiliza la licencia MIT. Consulta el archivo [LICENSE](./LICENSE) para más detalles.

---

## Contribuciones
¡🌟 Las contribuciones son bienvenidas! Si tienes sugerencias o mejoras, crea un Issue o un Pull Request. 🛠

---

## Autor
Plantilla creada por [pax16gamedev](https://github.com/Pax16gamedev).

