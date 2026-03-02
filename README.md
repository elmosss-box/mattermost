# 🚀 Despliegue de Mattermost: Tu Propia Plataforma de Colaboración

---

## 📌 1. ¿Qué es Mattermost?

**Mattermost** es una plataforma de comunicación y colaboración en equipo de código abierto.

Imagina que es un "clon" de herramientas como Slack o Microsoft Teams, pero con una diferencia fundamental:

> 🔐 Tú tienes el control total de los datos porque el servidor vive en tu propia infraestructura.

---

### 📜 Historia y Propósito

- **Origen:** Nació como herramienta interna de un estudio de videojuegos llamado *SpinPunch*, que buscaba una alternativa privada a Slack.
- **¿Para qué sirve?** Centraliza chat, archivos y gestión de proyectos en un entorno seguro.
- **Soberanía digital:** A diferencia de WhatsApp, los mensajes se guardan en tu servidor Ubuntu.

---

## ⚙️ 2. Funciones Principales

Mattermost está diseñado para entornos profesionales y técnicos:

| Función | Descripción |
|----------|------------|
| 📂 Canales | Espacios organizados por temas (`#Incidencias`, `#General`) |
| 💬 Mensajería Directa | Comunicación privada entre miembros |
| 🔎 Búsqueda Avanzada | Encuentra mensajes o archivos rápidamente |
| 🖥️ Auto-hospedado | Funciona en redes locales o servidores privados |
| 📱 Multiplataforma | Disponible en navegador, móvil y escritorio |

---

## 🛠️ 3. Guía de Configuración

### 🐳 A. Despliegue con Docker

Para evitar conflictos con otros servicios (como ejabberd), usamos Docker.

Se utilizó la imagen:

```
mattermost/mattermost-preview
```

### ▶️ Comando inicial

```bash
sudo docker run --name mattermost-server -d --publish 8065:8065 mattermost/mattermost-preview
```

📷 **Captura:** `image_168d64 - Descarga de la imagen en terminal`

---

### 📦 B. Configuración con Docker Compose

Archivo `docker-compose.yml`:

```yaml
version: '3'
services:
  mattermost:
    image: mattermost/mattermost-preview
    container_name: mattermost-server
    ports:
      - "8065:8065"
    restart: always
```

📷 **Captura:** `image_15997d - Archivo en nano`

#### ❓ ¿Por qué el puerto 8065?

Porque:
- 80 → Web estándar
- 5222 → Usado por ejabberd
- 8065 → Puerto estándar de Mattermost

---

### 🖥️ C. Ajustes en la Consola de Sistema

Acceso:

```
http://IP-DEL-SERVIDOR:8065
```

Configuraciones realizadas:

- 🌎 Cambio de idioma a español
- 🔗 Configuración de Site URL:
  ```
  http://192.168.109.66:8065
  ```
- 👥 Registro abierto habilitado

📷 `image_161ca3 - Configuración URL`
📷 `image_161507 - Configuración Registro`

---

### 👥 D. Gestión de Equipos

Equipo: **Proyecto Mensajeria**

#### ⚠️ Problema
Los nuevos usuarios veían la pantalla vacía.

#### ✅ Solución
Activar:

> "Permitir que cualquier usuario con cuenta se una a este equipo"

📷 `image_1609dc - Ajustes equipo`  
📷 `image_160986 - Usuario uniéndose`

---

## ✅ 4. Prueba Final de Funcionamiento

Prueba entre:

- 👑 **mossab (Admin)**
- 👤 **alumno2**

| Emisor | Receptor | Mensaje | Estado |
|--------|----------|----------|--------|
| mossab | alumno2 | "¿Recibes este mensaje?" | ✅ Recibido |
| alumno2 | mossab | Confirmación en incógnito | ✅ Enviado |

📷 `image_160622 - Vista Admin`  
📷 `image_1605fa - Vista Alumno2`

---

## 📝 Conclusión

✔️ El despliegue fue exitoso.  
✔️ Mattermost y ejabberd pueden convivir en el mismo servidor Ubuntu.  
✔️ Docker permitió aislamiento y gestión correcta de puertos.  

---

### 🚀 Resultado Final

Sistema de mensajería privado, funcional y auto-hospedado.
