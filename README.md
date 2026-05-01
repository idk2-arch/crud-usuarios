# CRUD Usuarios — Proyecto Colaborativo MVC

Aplicación web CRUD completa con arquitectura MVC.
Desarrollada colaborativamente usando Git/GitHub con ramas separadas.

## 🏗️ Estructura del proyecto

```
crud-usuarios/
├── backend/                  ← Persona 1 (rama: feature/backend)
│   ├── api/
│   │   └── usuarios.php      ← Punto de entrada de la API REST
│   ├── config/
│   │   ├── database.php      ← Conexión PDO a MySQL
│   │   └── database.sql      ← Script para crear la base de datos
│   ├── controllers/
│   │   └── UsuarioController.php  ← Lógica de rutas y respuestas
│   └── models/
│       └── Usuario.php       ← Modelo y consultas SQL
│
└── frontend/                 ← Persona 2 (rama: feature/frontend)
    ├── index.html            ← Página principal
    ├── css/
    │   └── styles.css        ← Estilos
    └── js/
        ├── model.js          ← Peticiones fetch a la API
        ├── view.js           ← Manipulación del DOM
        └── controller.js     ← Coordinación y eventos
```

## 🚀 Cómo ejecutar

1. Copia la carpeta `crud-usuarios/` dentro de `C:/xampp/htdocs/`
2. Abre phpMyAdmin (`http://localhost/phpmyadmin`)
3. Ejecuta el archivo `backend/config/database.sql`
4. Abre `http://localhost/crud-usuarios/frontend/index.html`

## 👥 Ramas de trabajo

| Rama              | Responsable | Qué contiene   |
|-------------------|-------------|----------------|
| `main`            | Ambos       | Código final   |
| `feature/backend` | Persona 1   | PHP + MySQL    |
| `feature/frontend`| Persona 2   | HTML + CSS + JS|

## 🛠️ Tecnologías

- **Backend**: PHP 8, PDO, MySQL, API REST
- **Frontend**: HTML5, CSS3, JavaScript ES6 (MVC vanilla)
- **Servidor**: XAMPP (Apache + MySQL)
