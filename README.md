# Aplicación Hola Mundo con Docker Compose

Aplicación web simple en Flask que se conecta a una base de datos MySQL usando Docker Compose.

## 📋 Requisitos Previos

- Docker instalado
- Docker Compose instalado
- Git (para clonar el repositorio)

## 🚀 Estructura del Proyecto

```
mi-app-docker/
├── src/
│   ├── app.py              # Código de la aplicación Flask
│   └── requirements.txt    # Dependencias Python
├── docker-compose.yml      # Configuración de servicios Docker
├── Dockerfile             # Imagen de la aplicación
└── README.md              # Este archivo
```

## 🔧 Instalación y Ejecución

### 1. Clonar el repositorio

```bash
git clone <tu-repositorio>
cd mi-app-docker
```

### 2. Construir y ejecutar los contenedores

```bash
docker-compose up --build
```

### 3. Acceder a la aplicación

Abre tu navegador y visita:
- **Aplicación principal:** http://localhost:5000
- **Health check:** http://localhost:5000/health

## 📊 Servicios

### Aplicación Flask (Puerto 5000)
- Framework: Flask
- Lenguaje: Python 3.11
- Base de datos: MySQL 8.0

### MySQL (Puerto 3306)
- Usuario: `usuario`
- Password: `password123`
- Base de datos: `miapp_db`
- Root password: `rootpassword`

## 🔍 Funcionalidades

- ✅ Conexión a base de datos MySQL
- ✅ Registro de visitas automático
- ✅ Contador de visitas
- ✅ Health check endpoint
- ✅ Reintentos automáticos de conexión

## 🛠️ Comandos Útiles

### Ver logs
```bash
docker-compose logs -f
```

### Detener los servicios
```bash
docker-compose down
```

### Detener y eliminar volúmenes
```bash
docker-compose down -v
```

### Reconstruir las imágenes
```bash
docker-compose up --build --force-recreate
```

### Acceder al contenedor de MySQL
```bash
docker exec -it mysql_db mysql -u usuario -ppassword123 miapp_db
```

## 📝 Endpoints

### GET /
Endpoint principal que muestra "Hola Mundo", se conecta a MySQL y registra la visita.

**Respuesta exitosa:**
```json
{
  "mensaje": "¡Hola Mundo!",
  "estado": "Conectado a MySQL exitosamente",
  "total_visitas": 5
}
```

### GET /health
Verifica el estado de salud de la aplicación y la conexión a la base de datos.

**Respuesta exitosa:**
```json
{
  "status": "healthy",
  "database": "connected",
  "mysql_version": "8.0.35"
}
```

## 🐛 Troubleshooting

### La aplicación no puede conectarse a MySQL
- Espera unos segundos, MySQL tarda en inicializarse
- La aplicación tiene reintentos automáticos
- Verifica los logs: `docker-compose logs mysql`

### Puerto ya en uso
Si el puerto 5000 o 3306 está ocupado, modifica los puertos en `docker-compose.yml`:
```yaml
ports:
  - "8080:5000"  # Cambia 5000 por otro puerto
```

## 📄 Licencia

Este proyecto es de código abierto y está disponible bajo la licencia MIT.

## 👨‍💻 Autor

Anddy Josue Jara 
