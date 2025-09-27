# ⚙️ Configuración del proyecto `residuos/` (Django)

Este módulo contiene la configuración principal del backend en **Django REST Framework**, encargado de manejar la API y la conexión a la base de datos.

---

## 📂 Estructura de la carpeta

```text
📁 residuos/
│
├── 📄 __init__.py     # Inicializa el proyecto
├── 📄 settings.py     # Configuración principal (apps, BD, CORS, REST)
├── 📄 urls.py         # Rutas del proyecto
├── 📄 wsgi.py         # Configuración WSGI (deploy tradicional)
└── 📄 asgi.py         # Configuración ASGI (deploy con websockets)
```

---

## 🚀 Pasos para levantar el backend

1. **Moverse a la carpeta del backend**
   ```bash
   cd backend
   ```

2. **Crear entorno virtual e instalar dependencias**
   ```bash
   python -m venv .venv
   source .venv/bin/activate   # En Windows: .venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. **Configurar variables de entorno**
   - Copiar el archivo `.env.example` y renombrarlo a `.env`
   - Editar valores como `SECRET_KEY`, `DEBUG`, `ALLOWED_HOSTS` y base de datos
   ```bash
   cp .env.example .env
   ```

4. **Aplicar migraciones**
   ```bash
   python manage.py migrate
   ```

5. **Crear superusuario**
   ```bash
   python manage.py createsuperuser
   ```

6. **Levantar el servidor**
   ```bash
   python manage.py runserver
   ```

---

## 🔐 Variables de entorno principales

| Variable              | Ejemplo / Valor por defecto   | Descripción                              |
|-----------------------|-------------------------------|------------------------------------------|
| `SECRET_KEY`          | `clave-segura`               | Clave secreta de Django                   |
| `DEBUG`               | `True`                       | Activa modo desarrollo                    |
| `ALLOWED_HOSTS`       | `localhost,127.0.0.1`        | Hosts permitidos                          |
| `DB_ENGINE`           | `django.db.backends.sqlite3` | Motor de base de datos                    |
| `DB_NAME`             | `db.sqlite3`                 | Nombre de la base de datos (SQLite)       |
| `DB_USER`             | *(si usas Postgres/MySQL)*   | Usuario de la base de datos               |
| `DB_PASSWORD`         | *(si usas Postgres/MySQL)*   | Contraseña de la base de datos            |
| `DB_HOST`             | *(si usas Postgres/MySQL)*   | Host de la base de datos                  |
| `DB_PORT`             | *(si usas Postgres/MySQL)*   | Puerto de la base de datos                |
| `CORS_ALLOW_ALL_ORIGINS` | `True`                    | Permitir cualquier origen (modo dev)      |
| `CORS_ALLOWED_ORIGINS`   | `http://localhost:5173`    | Orígenes permitidos (modo producción)     |
| `CSRF_TRUSTED_ORIGINS`   | `http://localhost:5173`    | Orígenes confiables para CSRF             |

---

> [!NOTE]  
> El backend corre por defecto en:  
> 🔗 `http://127.0.0.1:8000/`  
> La API está disponible en:  
> 🔗 `http://127.0.0.1:8000/api/`
