# 🍽️ SIGR — Sistema Integral de Gestión de Restaurante

> Aplicación web para la gestión de pedidos, reservas, menú digital, usuarios y reportes de ventas en restaurantes.

---

## 📋 Descripción General

El **SIGR** es una plataforma web diseñada para centralizar y optimizar las operaciones de un restaurante. Permite gestionar los pedidos por mesa, las reservas de clientes, el menú digital con sus categorías y platos, el cierre de caja diario y la generación de reportes de ventas.

El sistema contempla tres roles de usuario con permisos diferenciados:

| Rol | Descripción |
|---|---|
| **Administrador** | Acceso total: gestión de usuarios, menú, reportes y configuración general |
| **Mesero** | Registro y seguimiento de pedidos, visualización del menú |
| **Cliente** | Consulta del menú y registro de reservas |

---

## 🛠️ Stack Tecnológico

| Capa | Tecnología |
|---|---|
| **Frontend** | React.js (Vite) |
| **Backend** | FastAPI — Python 3.12+ |
| **ORM** | SQLAlchemy 2.x |
| **Base de datos** | AzureSQL |
| **Entorno virtual** | uv |
| **Autenticación** | JWT (python-jose) + bcrypt |
| **Control de versiones** | Git / GitHub |

---

## 🧩 Módulos del Sistema

- **Autenticación:** Registro, login y control de acceso por roles con JWT.
- **Menú Digital:** CRUD de platos y categorías.
- **Pedidos:** Registro, seguimiento de estado y gestión por mesa.
- **Reservas:** Registro por fecha, hora y número de comensales con validación de disponibilidad.
- **Caja y Reportes:** Cierre de caja diario y reportes de ventas exportables en PDF/CSV.

---

### Instalar uv

```bash
# macOS / Linux
curl -LsSf https://astral.sh/uv/install.sh | sh

# Windows (PowerShell)
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```

---

## 🚀 Instalación y Ejecución Local

### 1. Clonar el repositorio

```bash
git clone https://github.com/luisruro/linea_base_sigr.git
cd linea_base_sigr
```

---

### 2. Backend — FastAPI

```bash
cd backend

# Crear entorno virtual e instalar dependencias con uv
uv venv
uv sync
```

Contenido de `.env`:

```
DATABASE_URL=azuresql+asyncpg://usuario:contraseña@localhost:5432/sigr_db
SECRET_KEY=tu_clave_secreta_muy_larga
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
```

| Recurso | URL |
|---|---|
| API REST | http://localhost:8000 |
| Docs interactivos (Swagger) | http://localhost:8000/docs |


---

### 4. Frontend — React.js

```bash
cd ../frontend

npm install

cp .env.example .env
```

Contenido de `.env` del frontend:

```
VITE_API_URL=http://localhost:8000/api/v1
```

```bash
npm run dev
```

Frontend disponible en: `http://localhost:5173`

---

## 📁 Estructura de Carpetas

```
linea_base_sigr/
├── backend/
│   ├── app/
│   │   ├── main.py                 # Punto de entrada FastAPI
│   │   ├── core/
│   │   │   ├── config.py           # Variables de entorno y settings
│   │   │   └── security.py         # JWT, hashing de contraseñas
│   │   ├── db/
│   │   │   ├── base.py             # Base declarativa SQLAlchemy
│   │   │   └── session.py          # Sesión async de base de datos
│   │   └── modules/
│   │       ├── auth/               # Modelos, schemas, rutas, servicios
│   │       ├── menu/
│   │       ├── orders/
│   │       ├── reservations/
│   │       └── reports/             # Archivos de migración
│   ├── .env.example          
│   └── pyproject.toml  # Metadatos del proyecto Python
├── frontend/
│   ├── public/
│   └── src/
│       ├── components/             # Componentes reutilizables React
│       ├── pages/                  # Vistas por módulo
│       ├── services/               # Llamadas a la API
│       ├── context/                # Estado global (AuthContext, etc.)
│       └── main.jsx
├── database/
│   └── seeds.py                    # Script de datos de prueba
├── docs/
│   └── arquitectura.md
└── README.md
```

---

## 🏷️ Versión Actual

**v1.0** — Línea base oficial del proyecto.  
Rama estable: `main`

---

## 👥 Equipo de Desarrollo

- Luis Eugenio Rubio Romero