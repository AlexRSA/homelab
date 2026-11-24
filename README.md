# Homelab | Infraestructura, seguridad y automatización

En este homelab diseño, despliego y administro servicios e infraestructura. Lo uso para experimentar con virtualización, servicios self-hosted, identidad centralizada, controles de acceso, observabilidad, respuesta a incidentes asistida por IA y desarrollo de aplicaciones.

## Plataforma

| Componente | Detalle |
| --- | --- |
| Virtualización | Proxmox VE 9.x |
| Sistemas invitados | Contenedores LXC y máquinas virtuales |
| Aplicaciones | Docker y servicios Linux dedicados |
| Acceso remoto | Cloudflare Access, proxy inverso y VPN |
| Identidad | Authentik |
| Seguridad | CrowdSec, bouncers, notificaciones y aprobación manual |
| IA local | Ollama y agentes de IA |

He organizado las cargas por función y combino contenedores con máquinas virtuales para mantener los servicios separados y facilitar su administración.

## Lo que tengo montado

### Servicios y capacidades

| Área | Servicios / tecnologías | Para qué los utilizo |
| --- | --- | --- |
| Identidad y acceso | Authentik, Cloudflare Access, NPMplus, WireGuard | Identidad centralizada, control de acceso y publicación de servicios |
| Seguridad | CrowdSec, bouncers y bot de notificaciones | Detección de actividad sospechosa, aplicación de decisiones y avisos |
| Operaciones | Proxmox VE, Docker, Uptime Kuma, Prometheus PVE Exporter, Homepage | Virtualización, gestión de cargas, disponibilidad y visibilidad operativa |
| IA y automatización | Ollama, Open WebUI, Hermes Agent, SearXNG, servicio de voz | Ejecución local de modelos y herramientas de asistencia |
| Nube personal | Nextcloud, Collabora, Immich | Archivos, colaboración y gestión de fotografías |
| Multimedia | Jellyfin, Navidrome, Tunarr, Prowlarr, Sonarr, Lidarr, qBittorrent | Gestión de biblioteca, descargas y reproducción multimedia |
| Otros servicios | Home Assistant, Pelican, Agent DVR, Samba, NocoDB, Scrutiny, Speedtest Tracker | Automatización doméstica, gestión de servidores, vídeo, datos y diagnóstico |

## Cómo funcionan mis servicios

### Acceso e identidad centralizada

1. Publico los servicios que necesito mediante dominios protegidos por Cloudflare Access.
2. Aplico políticas de acceso según la aplicación, el origen de la conexión y la ubicación geográfica, sin publicar los valores ni las reglas concretas.
3. Centralizo la identidad y la autenticación de las aplicaciones integradas con Authentik.
4. Completo el acceso con NPMplus como proxy inverso y WireGuard para la conectividad VPN.

Así separo la entrada desde Internet, la autenticación de los usuarios y el acceso privado a mi infraestructura.

### Detección y respuesta asistida a incidentes

1. Uso CrowdSec para analizar actividad sospechosa y sus bouncers para aplicar decisiones en tiempo real en los puntos de control correspondientes.
2. Un bot me notifica los ataques y las alertas para que pueda revisarlos.
3. Un agente de IA que ejecuto localmente resume la actividad y me ayuda a detectar patrones entre los eventos.
4. La IA me propone una acción, pero soy yo quien decide. Antes de aplicar un bloqueo, confirmo la acción manualmente y me autentico con una passkey.

Mantengo los bloqueos bajo control humano: la IA me ayuda a analizar los eventos, pero no ejecuta esas acciones de forma autónoma. No publico reglas, umbrales ni indicadores de detección.

### Invitaciones, biblioteca y reproducción multimedia

1. Gestiono las invitaciones de usuarios a Jellyfin.
2. Organizo la biblioteca y las descargas con herramientas como Prowlarr, Sonarr, Lidarr y qBittorrent.
3. Uso Jellyfin, Navidrome y Tunarr para reproducir y distribuir contenido multimedia.

### IA local y agentes

- Ejecuto modelos localmente con Ollama y accedo a ellos mediante Open WebUI. También tengo SearXNG y un servicio de voz dentro de este entorno.
- Utilizo agentes de IA para resumir alertas e identificar patrones, con revisión humana para las decisiones sensibles.
- Mantengo Hermes Agent como parte de mis pruebas de agentes y automatización.

### Operación y observabilidad

- Administro con Proxmox VE los servicios que tengo aislados en contenedores y máquinas virtuales, y utilizo Docker para desplegar aplicaciones y sus componentes.
- Reviso disponibilidad y métricas con Uptime Kuma y Prometheus PVE Exporter.
- Tengo Nextcloud, Collabora e Immich para archivos, colaboración y fotografía.
- Mantengo almacenamiento separado para datos cloud, copias de seguridad y contenido multimedia. También he configurado acceso a dispositivos GPU para mis cargas locales de IA.

## Trabajo y proyectos personales

Actualmente alojo y administro la base de datos de una empresa mediante NocoDB y PostgreSQL.

| Proyecto | Descripción |
| --- | --- |
| Habitos | Aplicación web desplegada con frontend Nginx y backend. |
| Watch Party | Proyecto personal en el que trabajo para crear una experiencia de reproducción compartida. |
| Moodle | Entorno de plataforma educativa que utilizo para aprender y experimentar. |

## Experiencia técnica que he desarrollado

- Diseño y administración de un entorno virtualizado con Proxmox VE, LXC, máquinas virtuales y Docker.
- Publicación de servicios self-hosted mediante dominios, Cloudflare Access y proxy inverso.
- Centralización de identidad con Authentik y uso de passkeys para aprobar acciones sensibles.
- Detección y respuesta a amenazas con CrowdSec, bouncers, notificaciones y análisis local asistido por IA.
- Despliegue y operación de servicios de colaboración, almacenamiento, multimedia y automatización.
- Administración de una base de datos empresarial mediante NocoDB y PostgreSQL.
- Desarrollo y despliegue de aplicaciones web con frontend y backend.
- Monitorización de disponibilidad y métricas operativas.

## Privacidad y alcance

En este README he omitido direcciones IP, nombres de host internos, dominios, identificadores de instancias, puertos y detalles de las reglas de seguridad. Describo los flujos a nivel funcional y no publico credenciales, configuraciones sensibles ni datos de usuarios.
