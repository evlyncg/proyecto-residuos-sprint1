# 🖥️ Frontend `frontend/` — React + Vite

Interfaz web del **Sistema de Gestión de Residuos** construida con **React 18** y **Vite**.  
Consume la API del backend Django REST.

---

## 📂 Estructura de la carpeta

```text
📁 frontend/
│
├── 📁 public/
│   └── 📄 index.html
│
├── 📁 src/
│   ├── 📁 components/
│   │   ├── 📄 Navbar.jsx
│   │   └── 📄 Footer.jsx
│   ├── 📁 pages/
│   │   ├── 📄 Home.jsx
│   │   └── 📄 About.jsx
│   ├── 📁 services/
│   │   └── 📄 api.js          # Configuración Axios (baseURL a la API)
│   ├── 📄 App.jsx
│   ├── 📄 App.css
│   ├── 📄 main.jsx
│   └── 📄 index.css
│
├── 📄 package.json
├── 📄 vite.config.js
└── 📄 README.md
```

> [!NOTE]
> La ruta de la API se configura en `src/services/api.js` o con la variable `VITE_API_BASE_URL` (ver más abajo).

---

## 🚀 Pasos de instalación y ejecución

1. **Entrar a la carpeta del frontend**
   ```bash
   cd frontend
   ```

2. **Instalar dependencias**
   ```bash
   npm install
   ```

3. **Variables de entorno (opcional pero recomendado)**
   - Crea un archivo `.env` en `frontend/` con:
   ```env
   VITE_API_BASE_URL=http://127.0.0.1:8000/api/
   ```

4. **Levantar entorno de desarrollo**
   ```bash
   npm run dev
   ```

5. **Construir para producción**
   ```bash
   npm run build
   ```

6. **Previsualizar el build**
   ```bash
   npm run preview
   ```

---

## 🔌 Conexión con el backend (Axios)

**`src/services/api.js`** 

```javascript
import axios from "axios";

const api = axios.create({
  baseURL: import.meta.env.VITE_API_BASE_URL || "http://127.0.0.1:8000/api/",
});

// Ejemplos de uso
export const getResiduos = () => api.get("/residuos/");
export const createResiduo = (data) => api.post("/residuos/", data);
export const getPuntos = () => api.get("/puntos/");

export default api;
```

---

## 🧭 Rutas básicas (React Router)

```bash
npm i react-router-dom
```

**`src/App.jsx`** (mínimo viable):
```jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";
import Home from "./pages/Home";
import About from "./pages/About";

export default function App() {
  return (
    <BrowserRouter>
      <nav style={{ padding: 12 }}>
        <Link to="/">Inicio</Link> | <Link to="/about">Acerca de</Link>
      </nav>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

**`src/pages/Home.jsx`**:
```jsx
import { useEffect, useState } from "react";
import { getResiduos } from "../services/api";

export default function Home() {
  const [data, setData] = useState([]);

  useEffect(() => {
    getResiduos().then((res) => setData(res.data)).catch(console.error);
  }, []);

  return (
    <main style={{ padding: 16 }}>
      <h1>Gestión de Residuos</h1>
      <ul>
        {data.map((item) => (
          <li key={item.id}>{item.nombre} — {item.tipo}</li>
        ))}
      </ul>
    </main>
  );
}
```

**`src/pages/About.jsx`**:
```jsx
export default function About() {
  return (
    <main style={{ padding: 16 }}>
      <h1>Acerca del proyecto</h1>
      <p>Frontend en React + Vite consumiendo Django REST API.</p>
    </main>
  );
}
```

---

## 📦 `package.json` mínimo sugerido

```json
{
  "name": "frontend",
  "version": "1.0.0",
  "private": true,
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "axios": "^1.7.2",
    "react": "^18.3.1",
    "react-dom": "^18.3.1",
    "react-router-dom": "^6.23.0"
  },
  "devDependencies": {
    "@vitejs/plugin-react": "^4.2.0",
    "vite": "^5.2.0"
  }
}
```

---

## 🔒 CORS y URL de la API

- En desarrollo, el backend debe permitir `http://localhost:5173` en CORS/CSRF.  
- Ajusta `CORS_ALLOWED_ORIGINS` y `CSRF_TRUSTED_ORIGINS` en `residuos/settings.py` si cambias el puerto/URL.

---

## ✅ Checklist rápido

- [ ] `.env` con `VITE_API_BASE_URL` configurado  
- [ ] API del backend corriendo en `:8000`  
- [ ] `npm run dev` levantado en `:5173`  
- [ ] Prueba un fetch en `/api/residuos/`
