# 📜 CHANGELOG — Proyecto Gestión de Residuos

---

## 🟢 Sprint 1 — Análisis y Diseño
- Definición del problema y objetivos del sistema.  
- Elaboración del diagrama de casos de uso.  
- Diseño preliminar de la base de datos y diagramas de clases.

---

## 🟡 Sprint 2 — Configuración inicial
- Creación del entorno Django y estructura del backend.  
- Configuración de dependencias (`requirements.txt`) y entorno virtual.  
- Integración inicial del frontend con React y Vite.

---

## 🟠 Sprint 3 — Desarrollo de módulos
- Creación de la app `gestion/` con modelos y vistas base.  
- Configuración de CORS y REST Framework.  
- Validación de endpoints básicos del API.  
- Implementación de la estructura del frontend (componentes y páginas).

---

## 🔵 Sprint 4 — Integración y datos de prueba
- Implementación completa del frontend conectado al backend.  
- Creación del archivo `seed.json` con datos de prueba automáticos.  
- Validación de la API en conjunto con el frontend.  
- Actualización de la documentación (`README.md` por carpeta).  
- Publicación del repositorio GitHub oficial:  
  [https://github.com/evcdess/proyecto-gestion-residuos-sprint4](https://github.com/evcdess/proyecto-gestion-residuos-sprint4)

---

## 🚀 Próximo Sprint (5)
- Implementar autenticación de usuarios (login y registro).  
- Agregar dashboard de análisis de residuos recolectados.  
- Mejorar diseño visual con componentes personalizados.  
- Automatizar la carga de fixtures mediante un comando `python manage.py seed`.

- ---

## 🟠 Sprint 7 — pruebas de aceptación, la optimización visual y técnica
Modo oscuro/claro (toggle 🌙/☀️). 

i18n ES/EN (selector de idioma). 

Dashboard con 3 gráficos en Canvas puro: 

Línea: movimientos por día (filtrable por residuo). 

Barras: distribución por tipo (kg). 

Pastel: estatus de residuos. 

CRUD simulado de movimientos (solo admin/operador) + bitácora de auditoría. 

Exportación de la tabla de residuos a CSV y JSON. 

Tablas de Residuos (búsqueda + filtro por tipo) y Puntos. 

Login simulado por roles: admin@demo.com, op1@demo.com, visor@demo.com (cualquier contraseña). 
