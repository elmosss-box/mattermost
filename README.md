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

<img width="816" height="514" alt="image" src="https://github.com/user-attachments/assets/29bbc696-5cfb-4dc7-af22-f57359a49649" />


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

<img width="537" height="214" alt="image" src="https://github.com/user-attachments/assets/e3c1eaaa-36ce-4a65-b868-8e47b0240997" />


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

<img width="741" height="466" alt="image" src="https://github.com/user-attachments/assets/3b252632-b70e-4f33-a6bd-417f53b90774" />

<img width="714" height="623" alt="image" src="https://github.com/user-attachments/assets/385ac9f3-675d-4c41-ba99-b901eda6a6af" />


---

### 👥 D. Gestión de Equipos

Equipo: **Proyecto Mensajeria**

#### ⚠️ Problema
Los nuevos usuarios veían la pantalla vacía.

#### ✅ Solución
Activar:

> "Permitir que cualquier usuario con cuenta se una a este equipo"

<img width="808" height="677" alt="image" src="https://github.com/user-attachments/assets/1cd52164-e90e-48a0-9b46-1bef39a113de" />

<img width="1278" height="826" alt="image" src="https://github.com/user-attachments/assets/50dfcc7e-e0c9-4903-9a99-29fa65d3e466" />


---

## ✅ 4. Prueba Final de Funcionamiento

Prueba entre:

- 👑 **mossab (Admin)**
- 👤 **alumno2**

| Emisor | Receptor | Mensaje | Estado |
|--------|----------|----------|--------|
| mossab | alumno2 | "¿Recibes este mensaje?" | ✅ Recibido |
| alumno2 | mossab | Confirmación en incógnito | ✅ Enviado |

<img width="909" height="915" alt="image" src="https://github.com/user-attachments/assets/9cd387df-dc88-4b20-add0-b95dba422fbc" />

<img width="862" height="825" alt="image" src="https://github.com/user-attachments/assets/10e0bf02-0a73-4f2a-bce3-f3e624fdbe3b" />


---

## 📝 Conclusión

✔️ El despliegue fue exitoso.  
✔️ Mattermost y ejabberd pueden convivir en el mismo servidor Ubuntu.  
✔️ Docker permitió aislamiento y gestión correcta de puertos.  

---

### 🚀 Resultado Final

Sistema de mensajería privado, funcional y auto-hospedado.
