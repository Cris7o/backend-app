# Backend App

API REST desarrollada con Node.js + Express, contenedorizada con Docker y desplegada mediante pipeline CI/CD con GitHub Actions.

## Tecnologías
- Node.js + Express
- Docker
- GitHub Actions (CI/CD)

## Estructura del proyecto
backend-app/
├── .github/workflows/deploy.yml  # Pipeline CI/CD
├── data/                         # Carpeta de persistencia (volumen Docker)
├── index.js                      # Servidor Express
├── Dockerfile                    # Imagen Docker
└── package.json

## Cómo ejecutar localmente
```bash
docker build -t backend-app .
docker run -p 3000:3000 backend-app
```
Verificar: http://localhost:3000

## Pipeline CI/CD
El pipeline se activa con push a la rama `deploy` y realiza:
1. Build de la imagen Docker
2. Push a Docker Hub (`cris7o/backend-app:latest`)

## Persistencia de datos
Se utiliza un **named volume** (`backend_data`) montado en `/app/data`.
Esto asegura que los datos no se pierdan al reiniciar el contenedor.

## Imagen Docker Hub
docker pull cris7o/backend-app:latest
