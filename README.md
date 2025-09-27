cd backend

# Crear entorno virtual
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows

# Instalar dependencias
pip install -r requirements.txt

# Migrar base de datos
python manage.py makemigrations
python manage.py migrate

# Ejecutar servidor
python manage.py runserver

