\# Automatización de registro y clasificación de incidencias con n8n, Docker y GitHub



\## Descripción

Este proyecto implementa un workflow de automatización desarrollado en n8n, desplegado localmente mediante Docker Compose, que permite registrar y clasificar incidencias según su nivel de prioridad.



\## Tecnologías utilizadas

\- Docker

\- Docker Compose

\- n8n

\- Git

\- GitHub

\- PowerShell



\## Despliegue del proyecto



Para levantar el proyecto localmente:



```powershell

docker compose up -d

```



Verificar que el contenedor esté corriendo:



```powershell

docker ps

```



Acceder a n8n desde el navegador: http://localhost:5678 



\## Estructura del proyecto



proyecto-n8n-docker/

│

├── docker-compose.yml

├── .gitignore

├── README.md

└── workflows/

└── registro-incidencias.json



\## Funcionamiento del workflow

Webhook

↓

Edit Fields

↓

IF

↙️ ↘️

TRUE FALSE

↓ ↓

URGENTE NORMAL



\## Evidencias



\*(Aquí se agregarán las capturas del proyecto funcionando: Docker ejecutándose, n8n funcionando, workflow completo, pruebas con prioridad alta/baja y sus resultados)\*



\## Matriz de incidencias técnicas



| Error | Causa | Solución |

|-------|-------|----------|

| \*(pendiente)\* | | |

