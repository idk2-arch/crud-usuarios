# 📘 Guía Completa — Git Colaborativo desde Cero

> **Proyecto:** CRUD Usuarios  
> **Personas:** Persona 1 (backend) y Persona 2 (frontend)  
> Esta guía asume que tienes Git instalado. Si no, descárgalo en https://git-scm.com

---

## 🧠 ¿Qué es Git? (explicación simple)

Git es como un historial de guardados de tu proyecto.  
Cada vez que "guardas" en Git, se llama un **commit**.  
GitHub es donde subes ese historial a internet para que otros lo vean.

Una **rama (branch)** es como una copia paralela del proyecto donde puedes trabajar sin afectar el trabajo del otro.

---

## 📋 FASE 0 — Configuración inicial (una sola vez)

Abre la terminal (CMD en Windows o Terminal en Mac/Linux) y escribe:

```bash
# Decirle a Git quién eres (reemplaza con tus datos reales)
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"
```

---

## 📋 FASE 1 — Crear el repositorio en GitHub

> **Lo hace cualquiera de los dos, una sola vez.**

### Paso 1.1 — Crear el repo en GitHub.com

1. Ve a https://github.com y haz login
2. Clic en el botón verde **"New"** (arriba a la izquierda)
3. Completa:
   - **Repository name:** `crud-usuarios`
   - **Description:** `Proyecto CRUD MVC colaborativo`
   - Selecciona **Public**
   - ✅ Marca "Add a README file"
4. Clic en **"Create repository"**

### Paso 1.2 — Clonar el repo en tu computadora

```bash
# Ir a la carpeta donde quieres el proyecto (ejemplo: escritorio)
cd C:/Users/TuUsuario/Desktop

# Clonar el repositorio (copia el link de TU repo en GitHub)
git clone https://github.com/TU-USUARIO/crud-usuarios.git

# Entrar a la carpeta del proyecto
cd crud-usuarios
```

### Paso 1.3 — Copiar los archivos del proyecto

Copia todos los archivos que te dí (backend/, frontend/, README.md, .gitignore) dentro de la carpeta `crud-usuarios` que se creó.

### Paso 1.4 — Primer commit (subir la estructura base)

```bash
# Ver qué archivos detecta Git (aparecerán en rojo = sin guardar)
git status

# Agregar TODOS los archivos al área de preparación
git add .

# Guardar un commit con mensaje descriptivo
git commit -m "feat: estructura inicial del proyecto MVC"

# Subir a GitHub (rama principal)
git push origin main
```

> ✅ Ahora el código base está en GitHub. Ambas personas pueden verlo.

---

## 📋 FASE 2 — Invitar al colaborador

> **Lo hace la Persona 1 (dueña del repo)**

1. En GitHub, ve a tu repo → **Settings** → **Collaborators**
2. Clic en **"Add people"**
3. Escribe el usuario de GitHub de la Persona 2
4. La Persona 2 recibirá un email y debe aceptar la invitación

La Persona 2 ahora clona el repo igual que en el Paso 1.2.

---

## 📋 FASE 3 — Persona 1 trabaja en el Backend

```bash
# ── En la computadora de la Persona 1 ──────────────────────────

# Asegurarse de estar en main y tenerlo actualizado
git checkout main
git pull origin main

# Crear y cambiar a la rama del backend
git checkout -b feature/backend
```

> **¿Qué hizo eso?**  
> `checkout -b` crea una rama nueva Y se mueve a ella al mismo tiempo.  
> Ahora cualquier cambio que hagas NO afecta a `main`.

```bash
# La Persona 1 trabaja en los archivos de backend/
# (ya están en su carpeta, no hace falta crear nada)

# Ver el estado de los archivos
git status

# Agregar los archivos del backend
git add backend/

# Guardar el trabajo con un mensaje claro
git commit -m "feat(backend): API REST usuarios con PHP y PDO"

# Subir la rama a GitHub
git push origin feature/backend
```

---

## 📋 FASE 4 — Persona 2 trabaja en el Frontend

```bash
# ── En la computadora de la Persona 2 ──────────────────────────

# Primero clonar el repo (si no lo hizo aún)
git clone https://github.com/TU-USUARIO/crud-usuarios.git
cd crud-usuarios

# Crear y cambiar a la rama del frontend
git checkout -b feature/frontend

# La Persona 2 trabaja en los archivos de frontend/
git add frontend/

git commit -m "feat(frontend): interfaz MVC con HTML CSS y JS vanilla"

# Subir la rama a GitHub
git push origin feature/frontend
```

---

## 📋 FASE 5 — Pull Request (unir el trabajo)

> Un **Pull Request (PR)** es una solicitud para mezclar tu rama con `main`.  
> Es el momento donde el otro revisa tu código antes de aprobarlo.

### Crear el PR de Backend (Persona 1):

1. Ve a GitHub → tu repo
2. Verás un banner amarillo: **"feature/backend had recent pushes"** → clic en **"Compare & pull request"**
3. Completa:
   - **Title:** `feat: implementar API REST del backend`
   - **Description:** explica brevemente qué hiciste
4. Clic en **"Create pull request"**
5. La Persona 2 lo revisa y hace clic en **"Merge pull request"** → **"Confirm merge"**

### Crear el PR de Frontend (Persona 2):

Mismos pasos pero para la rama `feature/frontend`.  
La Persona 1 revisa y hace el merge.

---

## 📋 FASE 6 — Actualizar tu copia local después del merge

```bash
# Ambas personas deben hacer esto después de cada merge

# Volver a la rama principal
git checkout main

# Descargar los cambios que se mergearon en GitHub
git pull origin main
```

---

## 📋 FASE 7 — Flujo de trabajo diario (repetir siempre)

```bash
# 1. Antes de trabajar, siempre actualizar main
git checkout main
git pull origin main

# 2. Ir a tu rama
git checkout feature/backend   # o feature/frontend

# 3. Traer los últimos cambios de main a tu rama (evita conflictos)
git merge main

# 4. Trabajar... editar archivos...

# 5. Guardar tu trabajo
git add .
git commit -m "fix: corregir validación de email"

# 6. Subir tus cambios
git push origin feature/backend
```

---

## 🔥 Comandos Git más usados — Referencia rápida

| Comando | ¿Qué hace? |
|---------|------------|
| `git status` | Ver qué archivos cambiaron |
| `git add .` | Preparar TODOS los cambios |
| `git add archivo.php` | Preparar UN archivo |
| `git commit -m "mensaje"` | Guardar los cambios con descripción |
| `git push origin rama` | Subir tu rama a GitHub |
| `git pull origin main` | Bajar los últimos cambios de main |
| `git checkout -b nueva-rama` | Crear y cambiar a nueva rama |
| `git checkout main` | Volver a la rama principal |
| `git branch` | Ver todas las ramas |
| `git log --oneline` | Ver historial de commits |

---

## 🚨 ¿Qué hacer si hay un conflicto?

Un **conflicto** ocurre cuando dos personas editan la misma línea del mismo archivo. Git lo marca así:

```
<<<<<<< HEAD
  Tu versión del código
=======
  La versión del otro
>>>>>>> feature/frontend
```

**Solución:**
1. Abre el archivo conflictivo en tu editor
2. Decide qué versión conservar (o combina ambas)
3. Borra las líneas `<<<<<<<`, `=======` y `>>>>>>>`
4. Guarda el archivo
5. `git add .` → `git commit -m "fix: resolver conflicto en styles.css"`

---

## 🗺️ Diagrama del flujo completo

```
main ──────────────────────────────────────── (producción)
  │                                    ↑    ↑
  ├─── feature/backend ────────────────┤    │
  │    (Persona 1: PHP, SQL)     merge │    │
  │                                    │    │
  └─── feature/frontend ───────────────┘────┘
       (Persona 2: HTML, CSS, JS)   merge
```

---

## ✅ Checklist final

- [ ] Repositorio creado en GitHub
- [ ] Ambas personas clonaron el repo
- [ ] Persona 1 creó rama `feature/backend` y subió el código PHP
- [ ] Persona 2 creó rama `feature/frontend` y subió el código JS/CSS/HTML
- [ ] PR de backend creado y mergeado
- [ ] PR de frontend creado y mergeado
- [ ] Base de datos creada en phpMyAdmin con `database.sql`
- [ ] App funcionando en `http://localhost/crud-usuarios/frontend/index.html`
