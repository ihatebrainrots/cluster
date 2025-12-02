[🇪🇸 Español](README.es.md) | [🇬🇧 English](README.en.md) | [🇮🇹 Italiano](../README.md) | [🇩🇪 Deutsch](README.de.md)

---

# 🚗 Cyberpandino Cluster - PandaOS

[![Licencia: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Versión](https://img.shields.io/badge/version-0.9.0-green.svg)](https://github.com/cyberpandino/cluster/releases)
[![Node](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen.svg)](https://nodejs.org/)
[![Plataforma](https://img.shields.io/badge/platform-Raspberry%20Pi%204B%2F5-red.svg)](https://www.raspberrypi.com/)
[![PRs Bienvenidos](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/cyberpandino/cluster/blob/main/.github/CONTRIBUTING.en.md)

Cuadro de instrumentos digital para Fiat Panda 141 basado en Raspberry Pi 4B.

## 📋 Descripción

Sistema de cuadro de instrumentos completamente digital que reemplaza la instrumentación analógica original del Fiat Panda 141. El sistema se conecta a la ECU mediante el protocolo OBD-II (ELM327) y lee las luces de advertencia y sensores externos.

### Características Principales (v0.9.0)

- ✅ **Lectura de datos OBD-II**: Velocidad, RPM, temperatura, presión de aceite, etc.
- ✅ **Detección de luces de advertencia del vehículo**: Largas, cortas, intermitentes, nivel de aceite, etc.
- ✅ **Sensores externos**:
  - Temperatura exterior (DS18B20)
  - Nivel de combustible (ADS1115)
- ✅ **Gestión de encendido**: Sistema automático de ahorro de energía
- ✅ **Interfaz moderna**: Tablero 3D con modelo interactivo de Panda
- ✅ **Modo demo**: Para desarrollo sin hardware

---

## 📸 Vista previa

### Tablero Principal

El cuadro de instrumentos digital reemplaza completamente el tablero analógico original por una interfaz moderna y personalizable.

<div align="center">
  <img src="images/dashboard-main.png" alt="Tablero principal" width="800"/>
  <p><em>Tablero principal con modelo 3D interactivo</em></p>
</div>

---

### 🗺️ Funciones Futuras

Descubre lo que planeamos: [Hoja de ruta & Lista de deseos](ROADMAP.en.md)

Algunas ideas en la lista:
- 📹 Cámara trasera y sensores de aparcamiento
- 🚪 Animaciones 3D avanzadas (puertas, luces)
- 🎨 Tableros y temas personalizables
- 🌍 Internacionalización
- 📱 App compañera para móviles
- ¡Y mucho más!

¿Quieres contribuir? ¡Toda ayuda es bienvenida! Consulta la [guía de contribución](.github/CONTRIBUTING.en.md).

---

## 📚 Índice de Documentación

### 🚀 Empieza Aquí
- **[Inicio Rápido](QUICK_START.en.md)** - Guía rápida para empezar
- **[Hardware](HARDWARE.en.md)** - Lista completa de componentes y diagrama de montaje

### 📖 Documentación Técnica
- **[Arquitectura](ARCHITETTURA.en.md)** - Arquitectura completa del sistema
- **[Documentación General](DOCUMENTAZIONE.en.md)** - Visión general del proyecto
- **[Configuración del Cliente](client/CONFIGURAZIONE.en.md)** - Configuración del frontend
- **[Configuración del Servidor](server/CONFIGURAZIONE_SERVER.en.md)** - Configuración del backend
- **[Configuración de entorno](client/config/README.en.md)** - Variables y parámetros de entorno

### 🤝 Contribución
- **[Cómo contribuir](.github/CONTRIBUTING.en.md)** - Guía completa para contribuir al proyecto

### 📋 Otros
- **[Hoja de ruta](ROADMAP.en.md)** - Plan de desarrollo y lista de deseos
- **[Autores](AUTHORS.en.md)** - Quién ha contribuido al proyecto
- **[Licencia](../LICENSE)** - Licencia GNU GPL v3.0

---

## ⚠️ Descargo de responsabilidad

PandaOS es un proyecto experimental y de aficionado, nacido de la curiosidad técnica y el espíritu de aventura digital. No es un producto certificado, ni está pensado para producción, ni pretende cum[...]

Todo el material de este repositorio, incluyendo código, guías, diagramas e ideas más o menos sensatas, se proporciona "TAL CUAL", sin garantías de funcionamiento, fiabilidad o compatibilidad con tu vehículo.

Los autores y colaboradores no asumen ninguna responsabilidad en caso de:

* fallos eléctricos o electrónicos
* comportamiento anómalo del vehículo
* cortocircuitos inesperados
* daños a personas, bienes, animales o similares
* cualquier efecto secundario derivado del uso del software o siguiendo las instrucciones de esta documentación

Se desaconseja encarecidamente el uso de PandaOS en vehículos en circulación o en cualquier contexto donde puedan ser necesarias homologaciones, certificaciones o sentido común. Cualquier instalación [...]

---

## 🏗️ Arquitectura

El proyecto consta de tres módulos principales:

```
cluster/
├── client/          → Interfaz gráfica (React + Vite + Electron)
├── server/          → Backend comunicación OBD-II y GPIO (Node.js)
└── main.js          → Electron wrapper para la app de escritorio
```

### Tecnologías Utilizadas

- **Frontend**: React 18, TypeScript, Three.js, Socket.IO Client
- **Backend**: Node.js, Socket.IO Server, SerialPort, GPIO (onoff)
- **Escritorio**: Electron 36
- **Hardware**: Raspberry Pi 4B, ELM327, DS18B20, ADS1115

### 🤔 ¿React + Electron en automoción? ¿Estás loco?

Sí, lo sabemos. Cualquier ingeniero embebido viendo este proyecto probablemente se lleve las manos a la cabeza.

**Cómo se haría correctamente:**
- **C/C++** - Porque JavaScript en el coche es como ponerle ruedas cuadradas
- **Qt/QML** - El estándar de la industria (Tesla, Audi, BMW...)
- **Yocto/Buildroot** - Linux hecho para embebidos, no Raspberry Pi OS con todo el lastre
- **Framebuffer directo** - No Electron ejecutando un navegador solo para mostrar 4 números

**¿Entonces por qué React/Electron/Node.js?**

Porque es un **proyecto de hobby** y queremos **divertirnos**, no volvernos locos.

**Ventajas de nuestro enfoque dudoso**:
- ⚡ **Rápido de desarrollar** - ¿Has visto Three.js? Modelo 3D en 5 minutos. Prueba con OpenGL nativo.
- 🎨 **Librerías por todos lados** - npm tiene todo. C++ tiene... bueno... boost.
- 🧑‍💻 **Accesible** - ¿Sabes React? Bienvenido. ¿Sabes CMake? Mis condolencias.
- 🐛 **Depuración** - F12 y ves todo. GDB, en cambio, es... una experiencia.
- 🚀 **Diversión** - Más tiempo trasteando, menos peleando con toolchains
- 💡 **Prueba de concepto** - ¿Funciona? ¡Perfecto! Luego ya veremos.

**Desventajas (que aceptamos a conciencia)**:
- 💾 **Come RAM** como si fueran tapas (~500MB vs ~50MB)
- 🐌 **Arranca lento** (~30s vs ~3s), pero con modo standby es casi instantáneo
- 🔋 **Consume** más de lo que debería (pero en standby consume solo 0.4W, despreciable)
- 📊 **JavaScript** - Sí, JavaScript. En un coche. Acéptalo.

**La cuestión es:** Hablamos de un **Panda de 1990**. No es un F-35, no va a ir a la Luna.
Solo debe mostrarte las revoluciones de forma chula mientras escuchas Pink Floyd. Y eso lo hace muy bien. 🚗💨

> 💡 **¿Quieres rehacerlo en C++/Qt “en condiciones”?** Genial, ¡nos encantaría ver un port nativo y te ayudamos encantados!

---

## ⚙️ Requisitos del Sistema

### Prerrequisitos de software

| Software | Versión mínima | Recomendada |
|----------|----------------|-------------|
| **Node.js** | 18.0.0 | 20.x LTS |
| **npm** | 9.0.0 | 10.x |
| **Git** | 2.0+ | Última |

```bash
# Comprobación rápida
node --version  # >= v18.0.0
npm --version   # >= 9.0.0
git --version   # >= 2.0.0
```

⚠️ **Raspberry Pi**: No uses `apt install nodejs` (versión obsoleta). Consulta [CONFIGURAZIONE_SERVER.en.md](server/CONFIGURAZIONE_SERVER.en.md#2-instalando-nodejs-y-npm) para NodeSource/nvm.

---

### Para Raspberry Pi (Producción)

- **Hardware**:
  - Raspberry Pi 4B (se recomienda 4GB o más) o Raspberry Pi 5
  - Adaptador USB ELM327 (puerto serie `/dev/ttyUSB0`)
  - Optoacopladores para luces de advertencia (PC817 o similar)
  - Pantalla LCD ultra-wide (1920×480 recomendado)
  - Sensor de temperatura DS18B20 (opcional)
  - Convertidor ADC ADS1115 (opcional, para sensor de combustible)

📋 **Lista completa de hardware**: Consulta [HARDWARE.en.md](HARDWARE.en.md) para detalles de todos los componentes

- **Sistema Operativo**:
  - Raspberry Pi OS Lite (64-bit) - basado en Debian recomendado
  - Tiempo de arranque: ~30s (optimizable a ~20s o instantáneo con standby)
  - Arquitectura ARM/ARM64

  > 📘 **Elección de SO y tiempo de arranque**: Consulta [CONFIGURAZIONE_SERVER.en.md](server/CONFIGURAZIONE_SERVER.en.md#1-instalación-del-sistema-operativo) para detalles sobre la elección, opti[...]

- **Software**: Consulta [CONFIGURAZIONE_SERVER.en.md](server/CONFIGURAZIONE_SERVER.en.md#2-instalando-nodejs-y-npm) para instrucciones de Raspberry Pi

### Para desarrollo local (Mac/Windows/Linux)

- Node.js 18+ (se recomienda 20 LTS)
- npm 9+ (se recomienda 10.x)
- Git 2.0+

> 💡 **Instalación rápida**: Consulta las instrucciones en la sección [Prerrequisitos de software](#prerrequisitos-de-software) arriba

⚠️ **NOTA**: Ejecutar el proyecto en sistemas que no sean Raspberry Pi hará que el servidor falle por dependencias de hardware faltantes (GPIO, sensores, puerto OBD). Puedes usar el **modo mock** para d[...]

---

## 🚀 Puesta en marcha del proyecto

### 1. Clonar el repositorio

```bash
git clone https://github.com/cyberpandino/cluster
cd cluster
```

### 2. Instalar dependencias

El proyecto proporciona un script de instalación que configura todas las dependencias:

```bash
npm run install:all
```

Esto instala dependencias de:
- Raíz (Electron + concurrently)
- Cliente (React + dependencias frontend)
- Servidor (Node.js + dependencias hardware)

### 3. Configuración

#### a) Configuración del cliente

Edita el archivo de configuración del cliente:

**Archivo**: `client/src/config/environment.ts`

```typescript
export const environment: EnvironmentConfig = {
  websocket: {
    url: 'http://127.0.0.1:3001',  // URL del servidor WebSocket
    mock: true,                      // true = modo demo | false = conexión real
    reconnectionAttempts: 3,
    reconnectionDelay: 1000,
    timeout: 5000,
  },
  debug: {
    enabled: true,                   // Activar modo debug
    showConsoleViewer: true,         // Mostrar consola (tecla 'd')
  },
  app: {
    name: "PandaOS Cluster",
    version: "0.9.0",
    locale: "es",
    timezone: "Europe/Madrid",
    timeFormat: "24h",
  },
};
```

**Parámetros clave**:
- `websocket.url`: Dirección del servidor WebSocket (por defecto: `http://127.0.0.1:3001`)
- `websocket.mock`:
  - `true` = Modo demo con animaciones simuladas (desarrollo local)
  - `false` = Conexión real al servidor (producción en Raspberry Pi)
- `debug.enabled`: Activa funciones de depuración
- `debug.showConsoleViewer`: Muestra consola (tecla `d`)

#### b) Configuración del servidor

Edita el archivo de configuración GPIO y sensores:

**Archivo**: `server/config/gpio-mapping.js`

Consulta la sección [Configuración de GPIO y Sensores](#-configuración-de-gpio-y-sensores) para detalles completos.

---

## 🎯 Inicio del proyecto

### Modo completo (Raspberry Pi)

Inicia cliente, servidor y Electron a la vez:

```bash
npm start
```

Este comando ejecuta:
1. Servidor OBD-II en puerto 3001
2. Cliente React/Vite en puerto 5173
3. App de escritorio Electron

### Modo desarrollo (local sin Raspberry)

#### Opción 1: Solo cliente (modo demo)

1. Asegúrate de que `websocket.mock = true` en `client/src/config/environment.ts`
2. Solo inicia el cliente:

```bash
npm run client
```

La app estará disponible en `http://localhost:5173` con datos simulados.

#### Opción 2: Cliente + Electron

```bash
npm run client    # En una terminal
npm run electron  # En otra terminal
```

### Comandos individuales

```bash
# Solo servidor (requiere Raspberry Pi)
npm run server

# Solo cliente
npm run client

# Solo Electron (espera al cliente en el puerto 5173)
npm run electron
```

---

## 🔌 Configuración de GPIO y sensores

### Mapeo GPIO para luces de advertencia del vehículo

El archivo `server/config/gpio-mapping.js` contiene el mapeo completo de pines GPIO.

> 📘 **Diagrama eléctrico del vehículo**: Para identificar el cableado correcto de las luces en el panel original, consulta el [diagrama oficial Fiat Panda 141](http://www.bunkeringe...)

#### Pines utilizados

| Luz/Función            | Pin GPIO (BCM) | Descripción                   |
|------------------------|----------------|-------------------------------|
| Intermitentes          | 17             | Indicadores de dirección      |
| Alternador             | 27             | Carga de batería              |
| Presión aceite         | 22             | Presión de aceite motor       |
| Freno                  | 23             | Frenos                        |
| Inyectores             | 24             | Sistema de inyección          |
| Llave ON               | 25             | Llave insertada               |
| Largas                 | 5              | Faros largos                  |
| Cortas                 | 6              | Faros cortos                  |
| Warning/Hazard         | 12             | Luces de emergencia           |
| Antiniebla             | 13             | Luz antiniebla trasera        |
| Temp refrigerante      | 16             | Líquido refrigerante          |
| Luneta térmica trasera | 19             | Desempañador trasero          |
| Reserva de combustible | 20             | Nivel bajo de combustible     |
| Encendido              | 21             | Detección on/off              |

#### Configuración de optoacopladores

```javascript
config: {
  mode: 'BCM',              // Numeración Broadcom
  pullMode: 'PUD_DOWN',     // Pull-down interno
  debounceTime: 50,         // Filtro antirrebote (ms)
  pollingInterval: 100,     // Frecuencia de lectura (ms)
}
```

**Lógica de funcionamiento**:
- `HIGH (1)` = Luz de advertencia encendida
- `LOW (0)` = Luz apagada

### Gestión de encendido

```javascript
ignition: {
  enabled: true,
  pin: 21,                  // Pin dedicado
  activeOn: 0,              // 0 = activo bajo | 1 = activo alto
  scripts: {
    lowPower: './scripts/low-power.sh',   // Cuando se apaga el encendido
    wake: './scripts/wake.sh',             // Cuando se enciende
  },
}
```

Puedes personalizar los scripts para:
- Apagar pantalla
- Reducir brillo
- Desactivar servicios no esenciales
- Iniciar apagado controlado

### Sensor de temperatura exterior (DS18B20)

```javascript
temperature: {
  enabled: true,
  sensorId: null,           // null = autoselecciona
  basePath: '/sys/bus/w1/devices',
  readInterval: 5000,       // Intervalo de lectura (ms)
  pin: 4,                   // GPIO 4 (por defecto para 1-Wire)
}
```

**Instalación hardware**:
1. Conectar DS18B20 a GPIO 4
2. Activar 1-Wire: `sudo raspi-config` → Interfaz → 1-Wire
3. Verifica: `ls /sys/bus/w1/devices/`

### Sensor de combustible (ADS1115 - ADC I2C)

```javascript
fuel: {
  enabled: true,
  chip: 0,                  // 0 = ADS1115 | 1 = ADS1015
  channel: 0,               // Canal A0 (0-3)
  gain: 4096,               // ±4.096V
  sampleRate: 250,          // Tasa de muestreo (SPS)
  readInterval: 500,        // Intervalo de lectura (ms)
  
  // Divisor resistivo
  voltageDivider: {
    r1: 100000,             // 100kΩ
    r2: 33000,              // 33kΩ
  },
  
  // Calibración voltaje → porcentaje
  calibration: {
    voltageEmpty: 0.5,      // Voltaje depósito vacío (V)
    voltageFull: 4.0,       // Voltaje depósito lleno (V)
  },
  
  pins: {
    sda: 2,                 // GPIO 2 (SDA)
    scl: 3,                 // GPIO 3 (SCL)
  },
}
```

**Instalación hardware**:
1. Conectar ADS1115:
   - VDD → 3.3V
   - GND → GND
   - SDA → GPIO 2
   - SCL → GPIO 3
   - A0 → Sensor combustible (con divisor)
2. Activa I2C: `sudo raspi-config` → Interfaz → I2C
3. Verifica: `sudo i2cdetect -y 1`

### Puerto serie OBD-II

**Archivo**: `server/services/OBDCommunicationService.js`

```javascript
constructor() {
  this.portPath = '/dev/ttyUSB0';  // Puerto del ELM327
  this.port = null;
  this.baudRate = 38400;            // Velocidad de comunicación
}
```

**Pasos hardware**:
1. Conecta el adaptador ELM327 por USB
2. Verifica el puerto: `ls -l /dev/ttyUSB*`
3. Permisos: `sudo usermod -a -G dialout $USER`
4. Reinicia o vuelve a iniciar sesión

**Configurar puerto alternativo**:

Si el adaptador OBD usa otro puerto (ej. `/dev/ttyUSB1`, `/dev/ttyACM0`):

```javascript
// En server/services/OBDCommunicationService.js (línea 7)
this.portPath = '/dev/ttyUSB1';  // Cambia aquí
```

---

## 🔧 Configuración PM2 (arranque automático)

Para ejecutar el servidor como servicio en Raspberry Pi:

### 1. Instalar PM2

```bash
sudo npm install -g pm2
```

### 2. Configurar ecosistema

Edita `server/ecosystem.config.js`:

```javascript
module.exports = {
  apps: [{
    name: 'obd-server',
    script: './server.js',
    cwd: '/home/pi/cockpit/server',  // ⚠️ CAMBIA ESTA RUTA
    instances: 1,
    autorestart: true,
    watch: false,
    max_memory_restart: '200M',
    restart_delay: 2000,
    max_restarts: 15,
    min_uptime: '10s',
    exp_backoff_restart_delay: 100,
    env: {
      NODE_ENV: 'production',
      PORT: 3001
    },
    log_file: './logs/obd-combined.log',
    out_file: './logs/obd-out.log',
    error_file: './logs/obd-error.log',
    log_date_format: 'YYYY-MM-DD HH:mm:ss Z',
    merge_logs: true
  }]
};
```

### 3. Arrancar con PM2

```bash
cd server
mkdir -p logs
pm2 start ecosystem.config.js
pm2 save
pm2 startup
```

### 4. Comandos útiles PM2

```bash
pm2 status              # Estado del servicio
pm2 logs obd-server     # Ver logs
pm2 restart obd-server  # Reiniciar servicio
pm2 stop obd-server     # Parar servicio
pm2 monit               # Monitor en tiempo real
```

---

## 🛠️ Solución de problemas

### El servidor no arranca en sistema que no es Raspberry

**Error**:
```
❌ ERROR: Essential Raspberry Pi dependencies not available
Unsupported platform: darwin arm64 - Linux ARM required
```

**Solución**:
- Usa el modo demo en el cliente (`websocket.mock = true`)
- O ejecuta el servidor solo en Raspberry Pi

### Error instalación: Python 3.13 / node-gyp incompatible

**Error** (al instalar en `server`):
```
gyp ERR! stack TypeError: Cannot assign to read only property 'cflags'
gyp info using node-gyp@7.1.2
gyp info using Python version 3.13.5
```

**Causa**: Dependencia `epoll` (de `onoff` para GPIO) usa versión antigua de `node-gyp` no compatible con Python 3.13+.

**Soluciones**:

**Opción 1: Instalar con --ignore-scripts (recomendado en desarrollo)**
```bash
cd server
npm install --ignore-scripts
```

Así saltas la compilación de dependencias nativas (GPIO, SerialPort). Perfecto para:
- ✅ Desarrollo en portátil/PC
- ✅ CI/CD
- ✅ Sistemas con Python 3.13+
- ❌ NO funciona en Raspberry Pi (requiere compilación)

**Opción 2: Downgrade Python (solo si es necesario en Raspberry)**
```bash
# Instala Python 3.11 (compatible con node-gyp)
sudo apt install python3.11
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.11 1
```

**Opción 3: DEV_MODE (solo desarrollo)**
```bash
cd server
npm install --ignore-scripts
DEV_MODE=true node server.js
```

⚠️ En DEV_MODE el servidor arranca pero no es funcional (sin GPIO/OBD). Solo para pruebas.

**Nota**: Las dependencias de hardware (`onoff`, `serialport`, `ads1x15`) son `optionalDependencies` - fallan sin impedir otras instalaciones.

### ELM327 no encontrado

**Error**:
```
Port /dev/ttyUSB0 not found
```

**Solución**:
1. Verifica el puerto: `ls -l /dev/ttyUSB*`
2. Comprueba permisos: `sudo usermod -a -G dialout $USER`
3. Cambia el puerto en `OBDCommunicationService.js` si es distinto

### Sensor de temperatura no encontrado

**Advertencia**:
```
⚠️ DS18B20 temperature sensor not available (1-Wire not found)
```

**Solución**:
1. Activa 1-Wire: `sudo raspi-config` → Interfaz → 1-Wire
2. Reinicia: `sudo reboot`
3. Verifica: `ls /sys/bus/w1/devices/`
4. Si no lo usas, desactiva en `gpio-mapping.js`: `temperature.enabled = false`

### Sensor de combustible no responde

**Advertencia**:
```
⚠️ ADS1115 fuel sensor not available
```

**Solución**:
1. Activa I2C: `sudo raspi-config` → Interfaz → I2C
2. Verifica: `sudo i2cdetect -y 1`
3. Revisa cableado
4. Si no lo usas, desactiva en `gpio-mapping.js`: `fuel.enabled = false`

### Electron no arranca

**Error**:
```
Error: connect ECONNREFUSED 127.0.0.1:5173
```

**Solución**:
El cliente Vite debe estar arrancado antes. Usa `npm start` que gestiona el orden.

### GPIO no responde

**Problema**: Las luces de advertencia no se detectan

**Solución**:
1. Verifica cableado del optoacoplador
2. Testea el pin: `gpio readall` (instala wiringpi si hace falta)
3. Comprueba mapeo de pines en `gpio-mapping.js`
4. Verifica lógica activo alto/bajo del optoacoplador

---

## 📱 Uso de la aplicación

### Controles de teclado

- **`d`**: Abrir consola debug
- **`ESC`**: Cerrar consola debug
- **`r`**: Recargar aplicación

### Consola debug

Pulsa `d` para ver consola interactiva con:
- Logs WebSocket
- Errores de conexión
- Datos OBD-II en tiempo real
- Estado de GPIO y sensores

---

## 📦 Compilación para producción

### Compilar cliente

```bash
cd client
npm run build
```

Salida en `client/dist/`

### Compilar Electron

Para crear la app instalable:

1. Instala electron-builder: `npm install --save-dev electron-builder`
2. Añade script en `package.json`:

```json
"scripts": {
  "build:electron": "electron-builder"
}
```

3. Ejecuta: `npm run build:electron`

---

## 📝 Estructura principal de archivos

```
cockpit/
├── client/
│   ├── src/
│   │   ├── config/
│   │   │   └── environment.ts          ← Configuración del cliente
│   │   ├── components/                 ← Componentes React
│   │   ├── routes/
│   │   │   └── Cockpit/               ← Tablero principal
│   │   ├── services/
│   │   │   └── WebSocketService.ts    ← Gestión de WebSocket en el cliente
│   │   └── store/                     ← Gestión de estados (Valtio)
│   └── package.json
│
├── server/
│   ├── config/
│   │   └── gpio-mapping.js            ← ⚙️ Configuración GPIO y sensores
│   ├── services/
│   │   ├── OBDServer.js               ← Servidor principal
│   │   ├── OBDCommunicationService.js ← Comunicación ELM327
│   │   ├── GPIOService.js             ← Gestión GPIO de luces
│   │   ├── IgnitionService.js         ← Gestión de encendido
│   │   ├── TemperatureSensorService.js← Sensor temperatura DS18B20
│   │   └── FuelSensorService.js       ← Sensor combustible ADS1115
│   ├── scripts/
│   │   ├── low-power.sh               ← Script ahorro energía
│   │   └── wake.sh                    ← Script activación
│   ├── ecosystem.config.js            ← Configuración PM2
│   └── package.json
│
├── main.js                            ← Electron wrapper
└── package.json                       ← Scripts principales
```

---

## 🔒 Seguridad y notas

- ⚠️ **No ejecutes como root**: Usa un usuario normal con grupos `dialout` y `gpio`
- 🔋 **Ahorro de energía**: Los scripts de encendido protegen frente a descargas de batería
- 🧪 **Pruebas**: Usa siempre el modo demo para testear sin hardware
- 📊 **Monitorización**: Usa PM2 para monitorizar el servidor en producción

---

## 📄 Licencia

Este proyecto se publica bajo la **Licencia Pública General GNU v3.0 o posterior**.

```
PandaOS
Copyright (C) 2025  Cyberpandino

Este programa es software libre: puedes redistribuirlo y/o modificarlo
bajo los términos de la Licencia Pública General GNU, versión 3.

Este programa se distribuye con la esperanza de que sea útil, pero
SIN GARANTÍA ALGUNA, incluso sin la garantía implícita de
COMERCIALIZACIÓN o IDONEIDAD PARA UN PROPÓSITO PARTICULAR. Consulta la
Licencia Pública General GNU para más detalles.
```

El texto completo está en [LICENSE](../LICENSE) y en https://www.gnu.org/licenses/gpl-3.0.html

---

## 👥 Contribuidores

¡Toda contribución es bienvenida! Código, documentación, reportes de bugs o sugerencias.

### 🚀 ¿Cómo empezar?

1. Lee la [guía de contribución](.github/CONTRIBUTING.en.md)
2. Elige cómo contribuir:
   - 🐛 [Reportar un bug](.github/ISSUE_TEMPLATE/bug_report.md)
   - ✨ [Proponer una mejora](.github/ISSUE_TEMPLATE/feature_request.md)
   - ❓ [Hacer una pregunta](.github/ISSUE_TEMPLATE/question.md)
   - 💻 Contribuir con código
   - 💡 Buscar inspiración en la [hoja de ruta & lista de deseos](.github/CONTRIBUTING.en.md#-quieres-contribuir-pero-no-tienes-ideas)

### 📝 Flujo de contribución

1. **Haz un fork** del repositorio
2. **Crea una rama**: `git checkout -b feature/nombre-feature`
3. **Haz los cambios** siguiendo el [estilo de código](.github/CONTRIBUTING.en.md#-code-style)
4. **Añade cabecera GPL-3.0** a archivos nuevos de código fuente
5. **Commit**: `git commit -m 'feat: nueva funcionalidad'` ([Commits convencionales](https://www.conventionalcommits.org/))
6. **Push**: `git push origin feature/nombre-feature`
7. **Abre un Pull Request** usando la [plantilla](.github/PULL_REQUEST_TEMPLATE.md)

### 📋 Plantillas disponibles

- [🐛 Reporte de bugs](.github/ISSUE_TEMPLATE/bug_report.md)
- [✨ Petición de funcionalidad](.github/ISSUE_TEMPLATE/feature_request.md)
- [❓ Pregunta](.github/ISSUE_TEMPLATE/question.md)
- [🔀 Pull Request](.github/PULL_REQUEST_TEMPLATE.md)

### 💡 ¿Buscas ideas?

¿No sabes por dónde empezar? Tenemos [hoja de ruta & lista de deseos](.github/CONTRIBUTING.en.md#-quieres-contribuir-pero-no-tienes-ideas):
- Cámara trasera y sensores de aparcamiento
- Animaciones 3D avanzadas (puertas, luces en modelo)
- Tableros y temas personalizables
- Tutoriales fotográficos y de vídeo
- Internacionalización
- ¡Y mucho más!

Consulta la [guía de contribución](.github/CONTRIBUTING.en.md) para más detalles.

---

## 📞 Soporte

Para dudas o problemas, abre un issue en GitHub.

---

## 👨‍💻 Autores

PandaOS es desarrollado y mantenido por:

- **[Matteo Errera](https://github.com/matteoerrera)**
- **[Roberto Zaccardi](https://github.com/rzaccardi)**
- **[Ludovico Verde](https://www.instagram.com/ludovico.verdee/)**

```
