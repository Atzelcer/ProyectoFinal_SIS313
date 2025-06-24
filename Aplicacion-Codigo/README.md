# 🚀 TechStore Galáctico - Centro de Comando Estelar

> **Sistema de gestión de útiles escolares con interfaz galáctica épica y efectos audiovisuales espectaculares**

![Versión](https://img.shields.io/badge/versión-3.0.0-blue?style=for-the-badge)
![Node.js](https://img.shields.io/badge/Node.js-18+-green?style=for-the-badge)
![Express](https://img.shields.io/badge/Express-4.18+-red?style=for-the-badge)
![MySQL](https://img.shields.io/badge/MySQL-8.0+-orange?style=for-the-badge)

## ✨ Características Galácticas Épicas

### 🎨 Diseño Visual Espectacular
- 🌟 **Interfaz futurista** con efectos de partículas y nebulosas animadas
- 🎨 **Diseño holográfico** con gradientes espaciales y efectos de neón
- ✨ **Sistema de partículas** dinámico usando Canvas 2D
- 🌌 **Fondo espacial** con estrellas titilantes y nubes cósmicas
- � **Animaciones 3D** y transiciones espectaculares

### 🎵 Sistema de Audio Galáctico
- 🔊 **Música de fondo** galáctica generativa con osciladores
- � **Efectos de sonido** láser, éxito, error y validación
- 🎛️ **Control de volumen** integrado en header con icono temático
- 🌊 **Audio espacial** con filtros y modulación LFO
- 🎪 **Sonidos interactivos** en clicks y validaciones

### 🛸 Modal de Agregar Mega-Épico
- 🚀 **Botón mega-cuántico** en header superior derecho
- 🌟 **Modal galáctico** con animaciones 3D espectaculares
- 🔍 **Escáner holográfico** animado durante uso
- ✅ **Validación en tiempo real** con indicadores visuales/sonoros
- ⚡ **Efectos de partículas** y transiciones cósmicas

### 📊 Gestión de Inventario Avanzada

## 🛠️ Tecnologías del Futuro

### Backend
- **Node.js** - Runtime de JavaScript
- **Express.js** - Framework web minimalista
- **MySQL2** - Conector de base de datos
- **CORS** - Middleware para solicitudes cross-origin
- **dotenv** - Gestión de variables de entorno

### Frontend
- **HTML5** - Estructura semántica
- **CSS3** - Animaciones y efectos avanzados
- **JavaScript ES6+** - Lógica interactiva
- **Canvas API** - Sistema de partículas
- **Web Audio API** - Efectos sonoros

## 🚀 Instalación Rápida

### Prerrequisitos
- Node.js 14+ instalado
- MySQL/MariaDB corriendo
- Git (opcional)

### Pasos de Instalación

1. **Clonar el repositorio**
```bash
git clone https://github.com/tu-usuario/techstore-galactico.git
cd techstore-galactico
```

2. **Instalar dependencias**
```bash
npm install
```

3. **Configurar base de datos**
```sql
-- Crear base de datos
CREATE DATABASE techstore_galactico;
USE techstore_galactico;

-- Crear tabla de suministros
CREATE TABLE supplies (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  type_id INT NOT NULL,
  quantity INT NOT NULL,
  price DECIMAL(10,2) NOT NULL,
  status_id INT NOT NULL,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
  updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

-- Insertar datos de ejemplo
INSERT INTO supplies (name, type_id, quantity, price, status_id) VALUES
('Lápiz Cuántico', 1, 100, 1.50, 1),
('Cuaderno Holográfico', 3, 50, 5.99, 1),
('Calculadora Galáctica', 4, 25, 29.99, 1),
('Marcadores de Neón', 2, 75, 8.50, 1),
('Regla Dimensional', 1, 30, 3.25, 2);
```

4. **Configurar variables de entorno**
```bash
cp .env.example .env
# Editar .env con tus credenciales de base de datos
```

5. **Ejecutar la aplicación**
```bash
# Modo desarrollo
npm run dev

# Modo producción
npm start
```

6. **Acceder a la aplicación**
   - Abrir navegador en `http://localhost:3000`
   - ¡Disfrutar de la experiencia galáctica! 🌌

## 📋 API Endpoints

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/` | Página principal |
| GET | `/supplies` | Obtener todos los suministros |
| POST | `/supplies` | Crear nuevo suministro |
| PUT | `/supplies/:id` | Actualizar suministro |
| DELETE | `/supplies/:id` | Eliminar suministro |
| GET | `/diagnostic` | Diagnóstico de conexión DB |

## 🏗️ Arquitectura de Infraestructura Galáctica

### 🌌 Visión General del Sistema
TechStore Galáctico está diseñado con una arquitectura distribuida de alta disponibilidad que garantiza tolerancia a fallos, escalabilidad horizontal y rendimiento óptimo bajo cargas masivas de tráfico intergaláctico.

### 🎯 Topología de Red

```
                    🌐 Internet
                         |
                    🔄 DNS Round Robin
                   /                 \
            🌍 DNS1 (Principal)   🌎 DNS2 (Secundario)
                         |
                    🚪 Load Balancer
                  (HAProxy/Nginx)
                         |
        ┌────────────────┼────────────────┐
        |                |                |
    🖥️ Aplicación1   🖥️ Aplicación2   🖥️ Aplicación3
   (Node.js:3000)  (Node.js:3001)  (Node.js:3002)
        |                |                |
        └────────────────┼────────────────┘
                         |
                🔄 Database Cluster
               /                    \
        🗄️ DB Master            🗄️ DB Slave
       (MySQL Principal)      (MySQL Replica)
         Puerto 3306           Puerto 3307
```

### 🗄️ Arquitectura de Base de Datos Maestro-Esclavo

#### 📊 Configuración Master-Slave
El sistema implementa una arquitectura de replicación MySQL master-slave para garantizar alta disponibilidad y distribución de carga de lectura:

**🎯 Servidor Maestro (Master)**
- **Función**: Maneja todas las operaciones de escritura (INSERT, UPDATE, DELETE)
- **Puerto**: 3306
- **Responsabilidades**:
  - Procesar transacciones de escritura
  - Mantener el binlog para replicación
  - Sincronizar cambios con servidores esclavos
  - Gestionar integridad referencial

**📖 Servidor Esclavo (Slave)**
- **Función**: Maneja operaciones de solo lectura (SELECT)
- **Puerto**: 3307
- **Responsabilidades**:
  - Replicar datos desde el master
  - Distribuir carga de consultas de lectura
  - Servir como backup en tiempo real
  - Proporcionar datos para reportes y analytics

#### 🔄 Proceso de Replicación

```sql
-- Configuración del Master
[mysqld]
server-id = 1
log-bin = mysql-bin
binlog-format = ROW
binlog-do-db = techstore_galactico

-- Configuración del Slave
[mysqld]
server-id = 2
relay-log = relay-log
read-only = 1
replicate-do-db = techstore_galactico
```

#### ⚡ Estrategia de Distribución de Carga

```javascript
// Configuración de conexiones en app.js
const masterDB = mysql.createPool({
  host: process.env.DB_MASTER_HOST,
  port: 3306,
  user: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  database: process.env.DB_NAME,
  connectionLimit: 10
});

const slaveDB = mysql.createPool({
  host: process.env.DB_SLAVE_HOST,
  port: 3307,
  user: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  database: process.env.DB_NAME,
  connectionLimit: 20
});

// Función de enrutamiento de consultas
function getDBConnection(operation) {
  return operation.toLowerCase().startsWith('select') 
    ? slaveDB 
    : masterDB;
}
```

### 🔄 Balanceador de Carga

#### 🚀 HAProxy Configuration
```bash
# /etc/haproxy/haproxy.cfg
global
    daemon
    maxconn 4096

defaults
    mode http
    timeout connect 5000ms
    timeout client 50000ms
    timeout server 50000ms

frontend galactic_frontend
    bind *:80
    default_backend galactic_backend

backend galactic_backend
    balance roundrobin
    option httpchk GET /health
    server app1 192.168.1.10:3000 check
    server app2 192.168.1.11:3001 check
    server app3 192.168.1.12:3002 check
```

#### 🎛️ Algoritmos de Balanceo
- **Round Robin**: Distribución equitativa secuencial
- **Least Connections**: Dirigir a servidor con menos conexiones activas
- **IP Hash**: Mantener sesiones pegajosas por IP
- **Health Checks**: Monitoreo automático de salud de servidores

### 🌐 Configuración DNS

#### 🎯 DNS Primario (dns1)
```bind
; Zona principal para techstore-galactico.com
$TTL 300
@   IN  SOA dns1.techstore-galactico.com. admin.techstore-galactico.com. (
        2024062401  ; Serial
        3600        ; Refresh
        1800        ; Retry
        604800      ; Expire
        300         ; Minimum TTL
    )

@           IN  NS      dns1.techstore-galactico.com.
@           IN  NS      dns2.techstore-galactico.com.
@           IN  A       192.168.1.100  ; Load Balancer IP
www         IN  CNAME   @
api         IN  A       192.168.1.100
```

#### 🌍 DNS Secundario (dns2)
- **Función**: Respaldo del DNS primario
- **Sincronización**: Transferencias de zona automáticas
- **Failover**: Activación automática si dns1 falla

### 🖥️ Servidores de Aplicación

#### 📦 Instancias de Node.js
```yaml
# docker-compose.yml
version: '3.8'
services:
  app1:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
      - APP_INSTANCE=1
    volumes:
      - ./logs:/app/logs

  app2:
    build: .
    ports:
      - "3001:3000"
    environment:
      - NODE_ENV=production
      - APP_INSTANCE=2
    volumes:
      - ./logs:/app/logs

  app3:
    build: .
    ports:
      - "3002:3000"
    environment:
      - NODE_ENV=production
      - APP_INSTANCE=3
    volumes:
      - ./logs:/app/logs
```

#### 🔧 Variables de Entorno por Servidor
```env
# Aplicación 1
PORT=3000
DB_MASTER_HOST=192.168.1.20
DB_SLAVE_HOST=192.168.1.21
INSTANCE_ID=app1
LOG_LEVEL=info

# Aplicación 2
PORT=3001
DB_MASTER_HOST=192.168.1.20
DB_SLAVE_HOST=192.168.1.21
INSTANCE_ID=app2
LOG_LEVEL=info

# Aplicación 3
PORT=3002
DB_MASTER_HOST=192.168.1.20
DB_SLAVE_HOST=192.168.1.21
INSTANCE_ID=app3
LOG_LEVEL=info
```

### 📊 Monitoreo y Métricas

#### 🔍 Health Checks
```javascript
// Endpoint de salud en cada aplicación
app.get('/health', async (req, res) => {
  try {
    // Verificar conexión a base de datos
    const masterStatus = await checkDBConnection(masterDB);
    const slaveStatus = await checkDBConnection(slaveDB);
    
    res.json({
      status: 'healthy',
      instance: process.env.INSTANCE_ID,
      timestamp: new Date().toISOString(),
      database: {
        master: masterStatus,
        slave: slaveStatus
      },
      uptime: process.uptime()
    });
  } catch (error) {
    res.status(503).json({
      status: 'unhealthy',
      error: error.message
    });
  }
});
```

#### 📈 Métricas de Rendimiento
- **Latencia de respuesta**: < 100ms promedio
- **Throughput**: 1000+ requests/segundo
- **Disponibilidad**: 99.9% uptime
- **Replicación**: Lag < 1 segundo

### 🚀 Despliegue y Escalabilidad

#### 🔄 Estrategia de Despliegue
1. **Blue-Green Deployment**: Cero downtime en actualizaciones
2. **Rolling Updates**: Actualización gradual de instancias
3. **Canary Releases**: Liberación progresiva de nuevas funcionalidades

#### 📈 Auto-Scaling
```bash
# Configuración de auto-scaling basado en métricas
if cpu_usage > 80% for 5 minutes:
  spawn_new_instance()
  update_load_balancer_config()

if cpu_usage < 30% for 10 minutes:
  terminate_instance()
  update_load_balancer_config()
```

### 🔐 Seguridad y Respaldos

#### 🛡️ Medidas de Seguridad
- **SSL/TLS**: Certificados Let's Encrypt renovación automática
- **Firewall**: iptables con reglas restrictivas
- **Rate Limiting**: Protección contra ataques DDoS
- **SQL Injection**: Prepared statements y validación de entrada

#### 💾 Estrategia de Respaldos
```bash
# Backup automático diario
#!/bin/bash
# backup_script.sh
DATE=$(date +%Y%m%d_%H%M%S)
mysqldump -h $DB_MASTER_HOST -u $DB_USER -p$DB_PASSWORD \
  techstore_galactico > backup_${DATE}.sql
aws s3 cp backup_${DATE}.sql s3://techstore-backups/
```

### 📋 Lista de Puertos Utilizados

| Servicio | Puerto | Protocolo | Descripción |
|----------|---------|-----------|-------------|
| DNS1 | 53 | UDP/TCP | Servidor DNS primario |
| DNS2 | 53 | UDP/TCP | Servidor DNS secundario |
| Load Balancer | 80/443 | HTTP/HTTPS | HAProxy frontend |
| Aplicación 1 | 3000 | HTTP | Node.js instance 1 |
| Aplicación 2 | 3001 | HTTP | Node.js instance 2 |
| Aplicación 3 | 3002 | HTTP | Node.js instance 3 |
| MySQL Master | 3306 | TCP | Base de datos principal |
| MySQL Slave | 3307 | TCP | Base de datos replica |
| Monitoring | 9090 | HTTP | Prometheus metrics |
| Grafana | 3000 | HTTP | Dashboard de métricas |

### 🤖 Scripts de Automatización

El proyecto incluye una suite completa de scripts de automatización para facilitar el despliegue, mantenimiento y monitoreo de la infraestructura galáctica.

#### 🚀 Scripts de Despliegue

**📁 `scripts/deploy.sh`** - Script principal de despliegue
```bash
#!/bin/bash
# Script de despliegue automatizado
set -e

echo "🚀 Iniciando despliegue galáctico..."

# Verificar prerrequisitos
./scripts/check-prerequisites.sh

# Configurar servidores DNS
./scripts/setup-dns.sh

# Desplegar bases de datos
./scripts/deploy-databases.sh

# Configurar replicación master-slave
./scripts/setup-replication.sh

# Desplegar aplicaciones
./scripts/deploy-applications.sh

# Configurar balanceador de carga
./scripts/setup-loadbalancer.sh

# Ejecutar pruebas de integración
./scripts/run-tests.sh

echo "✅ Despliegue completado exitosamente!"
```

**📁 `scripts/setup-replication.sh`** - Configuración de replicación MySQL
```bash
#!/bin/bash
# Configuración automática de replicación MySQL

# Configurar servidor master
mysql -h $DB_MASTER_HOST -e "
CREATE USER 'replica'@'%' IDENTIFIED BY 'secure_password';
GRANT REPLICATION SLAVE ON *.* TO 'replica'@'%';
FLUSH PRIVILEGES;
FLUSH TABLES WITH READ LOCK;
SHOW MASTER STATUS;
"

# Configurar servidor slave
mysql -h $DB_SLAVE_HOST -e "
CHANGE MASTER TO
  MASTER_HOST='$DB_MASTER_HOST',
  MASTER_USER='replica',
  MASTER_PASSWORD='secure_password',
  MASTER_LOG_FILE='mysql-bin.000001',
  MASTER_LOG_POS=0;
START SLAVE;
SHOW SLAVE STATUS\G;
"
```

#### 🔧 Scripts de Mantenimiento

**📁 `scripts/maintenance.sh`** - Rutinas de mantenimiento
```bash
#!/bin/bash
# Script de mantenimiento del sistema

echo "🔧 Ejecutando mantenimiento del sistema..."

# Limpiar logs antiguos
find /var/log/techstore -name "*.log" -mtime +7 -delete

# Optimizar bases de datos
mysql -h $DB_MASTER_HOST -e "OPTIMIZE TABLE supplies;"

# Verificar estado de replicación
./scripts/check-replication-health.sh

# Actualizar certificados SSL
certbot renew --quiet

# Restart servicios si es necesario
./scripts/restart-services.sh

echo "✅ Mantenimiento completado"
```

#### 📊 Scripts de Monitoreo

**📁 `scripts/monitor-health.sh`** - Monitoreo de salud del sistema
```bash
#!/bin/bash
# Script de monitoreo continuo

while true; do
  # Verificar aplicaciones
  for port in 3000 3001 3002; do
    if ! curl -f http://localhost:$port/health > /dev/null 2>&1; then
      echo "❌ Aplicación en puerto $port no responde"
      ./scripts/restart-app.sh $port
    fi
  done
  
  # Verificar replicación de BD
  lag=$(mysql -h $DB_SLAVE_HOST -e "SHOW SLAVE STATUS\G" | grep Seconds_Behind_Master | awk '{print $2}')
  if [ "$lag" -gt 10 ]; then
    echo "⚠️ Replicación retrasada: ${lag}s"
    ./scripts/alert-admin.sh "Replication lag: ${lag}s"
  fi
  
  sleep 30
done
```

### 📦 Archivos de Configuración

Los archivos de configuración están organizados en el directorio `Archivos de configuracion de los servicios/`:

```
Archivos de configuracion de los servicios/
├── aplicacion1/
│   ├── .env                    # Variables de entorno App1
│   ├── ecosystem.config.js     # PM2 config
│   └── nginx.conf             # Proxy reverso
├── aplicacion2/
│   ├── .env                    # Variables de entorno App2
│   ├── ecosystem.config.js     # PM2 config
│   └── nginx.conf             # Proxy reverso
├── balanceador/
│   ├── haproxy.cfg            # Configuración HAProxy
│   ├── ssl/                   # Certificados SSL
│   └── scripts/               # Scripts de failover
├── basedatos1/ (Master)
│   ├── my.cnf                 # Configuración MySQL Master
│   ├── init.sql               # Script de inicialización
│   └── backup/                # Scripts de respaldo
├── basedatos2/ (Slave)
│   ├── my.cnf                 # Configuración MySQL Slave
│   └── replication.sql        # Setup de replicación
├── dns1/
│   ├── named.conf             # Configuración BIND9
│   ├── zones/                 # Archivos de zona
│   └── techstore-galactico.com.zone
└── dns2/
    ├── named.conf             # Configuración BIND9 secundario
    └── zones/                 # Zonas replicadas
```

#### 🔧 Configuración de PM2 para Aplicaciones
```javascript
// ecosystem.config.js
module.exports = {
  apps: [{
    name: 'techstore-app1',
    script: './app.js',
    instances: 2,
    exec_mode: 'cluster',
    env: {
      NODE_ENV: 'production',
      PORT: 3000,
      INSTANCE_ID: 'app1'
    },
    error_file: './logs/err.log',
    out_file: './logs/out.log',
    log_file: './logs/combined.log',
    time: true,
    watch: false,
    max_memory_restart: '1G',
    restart_delay: 4000
  }]
};
```

#### 🌐 Configuración Nginx como Proxy Reverso
```nginx
# nginx.conf para aplicaciones
upstream techstore_backend {
    server 127.0.0.1:3000;
    server 127.0.0.1:3001;
    server 127.0.0.1:3002;
}

server {
    listen 80;
    server_name techstore-galactico.com;
    
    location / {
        proxy_pass http://techstore_backend;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_cache_bypass $http_upgrade;
    }
}
```

### 🚀 Comandos de Despliegue Rápido

```bash
# Despliegue completo desde cero
./scripts/full-deployment.sh

# Actualización de aplicaciones sin downtime
./scripts/rolling-update.sh

# Configuración inicial de infraestructura
./scripts/infrastructure-setup.sh

# Verificación de estado del sistema
./scripts/system-status.sh

# Respaldo completo del sistema
./scripts/full-backup.sh

# Restauración desde respaldo
./scripts/restore-backup.sh <backup_date>
```

## 🎨 Características Visuales

### Efectos Incluidos
- ⭐ **Fondo animado** con estrellas en movimiento
- 🌈 **Texto con gradientes** que cambian de color
- 💫 **Partículas flotantes** generadas dinámicamente
- 🔮 **Efectos holográficos** en tablas y paneles
- ⚡ **Animaciones de hover** en todos los elementos
- 🎵 **Sonidos ambientales** para feedback de usuario

### Paleta de Colores
- **Cyan primario**: `#00ffff`
- **Magenta secundario**: `#ff00ff`
- **Amarillo de acento**: `#ffff00`
- **Verde de estado**: `#00ff00`
- **Rojo de alerta**: `#ff0000`

## 🔧 Configuración Avanzada

### Variables de Entorno
```env
# Base de datos
DB_HOST=localhost
DB_USER=tu_usuario
DB_PASSWORD=tu_contraseña
DB_NAME=techstore_galactico

# Servidor
PORT=3000
NODE_ENV=development
```

### Personalización de Efectos
```javascript
// En script.js - Ajustar cantidad de partículas
const particleCount = Math.min(150, Math.floor(window.innerWidth * window.innerHeight / 10000));

// Cambiar velocidad de animaciones en style.css
animation: move-twink-back 200s linear infinite;
```

## 📱 Compatibilidad

- ✅ Chrome 70+
- ✅ Firefox 65+
- ✅ Safari 12+
- ✅ Edge 79+
- ✅ iOS Safari 12+
- ✅ Android Chrome 70+

## 🤝 Contribuir

1. Fork el proyecto
2. Crear rama de feature (`git checkout -b feature/nueva-caracteristica`)
3. Commit cambios (`git commit -am 'Agregar nueva característica'`)
4. Push a la rama (`git push origin feature/nueva-caracteristica`)
5. Crear Pull Request

## 📄 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

## 🆘 Soporte

Si tienes problemas o preguntas:

1. **Issues**: Crear un issue en GitHub
2. **Documentación**: Revisar este README
3. **Debug**: Usar `/diagnostic` para verificar conexión DB

## 🌟 Créditos

- **Fuentes**: [Google Fonts (Orbitron, Exo 2)](https://fonts.google.com/)
- **Iconos**: Emojis nativos del sistema
- **Inspiración**: Ciencia ficción y interfaces futuristas

---

**¡Que la fuerza del código esté contigo! 🚀✨**

*Desarrollado con 💙 para la comunidad galáctica*
