# Automatizacion de registro y clasificacion de incidencias con n8n, Docker y GitHub

## Descripcion
Este proyecto implementa un workflow de automatizacion desarrollado en n8n, desplegado localmente mediante Docker Compose, que permite registrar y clasificar incidencias segun su nivel de prioridad.

## Tecnologias utilizadas
- Docker
- Docker Compose
- n8n
- Git
- GitHub
- PowerShell

## Despliegue del proyecto

Para levantar el proyecto localmente:

```powershell
docker compose up -d
```

Verificar que el contenedor este corriendo:

```powershell
docker ps
```

Acceder a n8n desde el navegador:http://localhost:5678

## Estructura del proyecto

```
proyecto-n8n-docker/
├── docker-compose.yml
├── .gitignore
├── README.md
├── evidencias/
└── workflows/
    └── registro-incidencias.json
```

## Funcionamiento del workflow

Webhook
|
Edit Fields
|
IF
/
TRUE FALSE
| |
URGENTE NORMAL

El webhook recibe los datos de la incidencia, el nodo Edit Fields normaliza la informacion recibida, y el nodo IF evalua la prioridad: si es alta, el flujo toma la rama TRUE y clasifica la incidencia como URGENTE; si es baja, toma la rama FALSE y la clasifica como NORMAL.

## Evidencias

### Docker ejecutandose correctamente
![Docker corriendo](evidencias/02-docker-funcionando.png)

### n8n funcionando en localhost:5678
![n8n funcionando](evidencias/06-n8n-interfaz.png)

### Workflow completo
![Workflow completo](evidencias/25-workflow-completo.png)

### Webhook recibiendo los datos
![Webhook recibiendo datos](evidencias/27-webhook-recibiendo-datos.png)

### Prueba con prioridad alta
Se envio una solicitud con el campo de prioridad configurado como "alta". El nodo IF evaluo la condicion y tomo la rama TRUE, devolviendo el estado URGENTE.

![Prueba prioridad alta](evidencias/31-if-true.png)
![Resultado urgente](evidencias/32-respuesta-urgente-funcionando.png)

### Prueba con prioridad baja
Se envio una solicitud con el campo de prioridad configurado como "baja". El nodo IF evaluo la condicion y tomo la rama FALSE, devolviendo el estado NORMAL.

![Prueba prioridad baja](evidencias/33-if-false.png)
![Resultado normal](evidencias/34-respuesta-normal-funcionando.png)

## Matriz de incidencias tecnicas

Durante el desarrollo del proyecto se presentaron los siguientes inconvenientes:

| Error | Causa | Solucion |
|-------|-------|----------|
| Docker no lograba conectarse con el daemon al ejecutar comandos | Docker Desktop no se encontraba en ejecucion en el equipo | Se inicio Docker Desktop manualmente y se verifico nuevamente con el comando docker ps |
| n8n mostraba el error "An expression is used in Fields to Set" en varios campos del nodo Edit Fields | Las expresiones se habian configurado en el selector general del nodo en lugar de configurarse unicamente en el valor de cada campo | Se cambio el selector general a Fixed y se aplico la opcion Expression solo en el campo Value de cada uno de los valores necesarios |

![Error Docker](evidencias/01-error-docker.png)
![Error n8n Edit Fields](evidencias/29-error-edit-fields.png)


## Requisitos previos y verificación de la instalación

Para ejecutar el proyecto correctamente, el equipo debe contar con Docker Desktop instalado y en ejecución, además de Git para obtener el repositorio.

### Verificación de Docker

Antes de levantar n8n, se debe comprobar que Docker Desktop esté ejecutándose mediante:

docker --version
docker compose version
docker ps

## Resultado final

El workflow fue probado localmente de forma completa. Ambas rutas de decision del nodo IF funcionaron correctamente: la ruta TRUE clasifico las incidencias de prioridad alta como URGENTE, y la ruta FALSE clasifico las de prioridad baja como NORMAL, confirmando que la logica de clasificacion automatica opera segun lo esperado.
