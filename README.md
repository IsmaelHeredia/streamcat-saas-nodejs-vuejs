# StreamCat

Aplicación SaaS de streaming de audio full-stack construida con **Node.js + Express + Prisma** en el backend y **Vue 3 + Vite + Tailwind CSS + Pinia** en el frontend, con **PostgreSQL** como base de datos.

---

## Repositorios

El proyecto está dividido en tres repositorios independientes:

| Repositorio | Descripción |
|---|---|
| [`streamcat-saas-nodejs-vuejs`](https://github.com/IsmaelHeredia/streamcat-saas-nodejs-vuejs) | Este repositorio — documentación general e instalación conjunta |
| [`streamcat-backend-nodejs`](https://github.com/IsmaelHeredia/streamcat-backend-nodejs) | API REST con Node.js + Express + Prisma |
| [`streamcat-frontend-vuejs`](https://github.com/IsmaelHeredia/streamcat-frontend-vuejs) | Interfaz web con Vue 3 + Vite + Tailwind CSS |

---

## Funcionalidades

- **Autenticación completa**: Registro, inicio de sesión con JWT, verificación de cuenta por correo, recuperación y restablecimiento de contraseña.
- **Roles de usuario**: Rol `USER` y rol `ADMIN` con rutas protegidas según permisos.
- **Gestión de streams**: Los usuarios pueden crear, editar y eliminar sus propios streams con URL, cover e imagen. Los administradores gestionan todos los streams.
- **Gestión de géneros**: CRUD completo de géneros musicales (solo admin).
- **Gestión de covers**: Subida y administración de imágenes de portada mediante **Cloudinary** (solo admin).
- **Gestión de usuarios**: Panel de administración para ver y gestionar cuentas (solo admin).
- **Reproductor de audio**: Reproductor integrado con visualizador de audio, control de volumen, shuffle, repeat y navegación entre tracks.
- **Filtros y paginación**: Búsqueda por nombre y filtro por género con paginación del lado del servidor.
- **Correos transaccionales**: Verificación de cuenta y recuperación de contraseña vía **Resend**.
- **Personalización de perfil**: Cambio de nombre, avatar y contraseña con cierre de sesión automático al cambiar la contraseña.
- **Modo claro / oscuro**: Alternancia de tema persistente.

---

## Stack

### Backend

| Tecnología | Uso |
|---|---|
| Node.js 20+ | Runtime |
| Express | Framework HTTP |
| Prisma | ORM |
| PostgreSQL 15+ | Base de datos |
| JWT | Autenticación |
| Cloudinary | Almacenamiento de imágenes |
| Resend | Correos transaccionales |
| Vitest + Supertest | Pruebas de integración |
| Vercel | Deploy (serverless) |

### Frontend

| Tecnología | Uso |
|---|---|
| Vue 3 (Composition API) | Framework UI |
| Vite | Bundler |
| Tailwind CSS | Estilos |
| Pinia | Estado global |
| Playwright | Pruebas E2E |
| Vercel | Deploy |

---

## Arquitectura

El backend sigue el patrón **Domain-Driven Design (DDD)**, organizado por módulos bajo `src/modules/`. Cada módulo maneja sus propias rutas, controladores, servicios y repositorios. La base de datos se gestiona con **Prisma ORM** sobre **PostgreSQL**.

```
streamcat-backend-nodejs/
├── api/                    # Punto de entrada Vercel (serverless)
├── prisma/                 # Schema, migraciones y seed
└── src/
    ├── @types/
    ├── config/
    ├── modules/
    │   ├── users/
    │   ├── streams/
    │   ├── genres/
    │   └── covers/
    ├── shared/             # Middlewares, utilidades, mailer, cloudinary
    └── tests/

streamcat-frontend-vuejs/
├── public/
└── src/
    ├── api/
    ├── assets/
    ├── components/
    ├── layouts/
    ├── router/
    ├── services/
    ├── stores/             # Pinia
    ├── types/
    ├── utils/
    └── views/
```

---

## Capturas de pantalla

![screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjZv5asolkf7ESjIDGXoPeQAD942w5Ogkzyqlmkv6_6fH664LnodNJHdjvCKLrr3CMfyT70DNqHJ8tVA8iwQvmAAtq-VB8m75ugz-C2a8dNtPwvcRFtsBIxXKOgIm6nKg-hxC0V1Id0Se8xqxv7PzXOdzO1JapC4X6qi7H_U-Sh9Qc3RNSWh8XFq8texOs/s1843/1.png)

![screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgoA8qf_jqobb6NI8CdiQ610bG7GW7wwN3Cp64w4Aw8GIj6cjCcqtm2PDSh2KvShT3ARPpsbPcJp-AATVDUZEU4snZXxSXihKDNjYQz4hzIDxP_0wS6kdxPOE6rIOAoIwVGYhRM_kaOqRh-MVo_1iiIU_uKnr_Vr4wFMxI1SuEuH3pW70rbsOKHEE6OOig/s1846/2.png)

![screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhUwShrN7XVDDOZc0PNU3XGsBddH08RblORh31qGXjzuTONhNRf0Qb43umAC1tb9peTIVC6cUYJG4KMIIzv20biOBzG5dGG5rze6z8jkbBjviBjbSWVzyINmZviRRunm1RCWh-2I2NcAMkpNGTcA8zKk-1_YxNMffX-UYuxce_8E7Sv4XCK5szQEv9PLmo/s1846/3.png)

![screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEinC9c6Zkk9JgUyL60bRUza82rq3prG5ZaDU3fynKREdeyIJ_1sXiWPOFxPtubTAfmXf1aDNBzBGfXErEp0vaEaIrh16imGY9lFXxRbOavZ89oH2yoKPDvScZDyTAJNH8pKi1B43wSH7qLbYrbrektWpRtx4xyslUyy6VPQHFdCM7NQaBqze92q4zpTmMk/s1843/4.png)

![screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEghdTtlXne2IvCO4meIAbsQBwHSTWcT-68w0k1t1q8FgFBU6UuBhFS9omg7a-WiUAZAw4uP5S9PbvGvKQ1dppV4smAhgrpHp6kMPQ9Qnr9QP3J1iLrG2Yqnk_P_cwOFu4RhZWgmkfGb3KTwYOvwjruL5hN3ooCO20GLMnfEy_HF81CzL49HlgumjUla4jY/s1844/5.png)

![screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEipzAdaL5e_nCRg41q9I5r0PSr2RETZGBAKpkKWUWA5XtAGyv1AI5z6Lsp-iGnFIPJUN8dtiQtkzz9JgtGjtpoos6yeRVfHL987M985gcQKv5cYRGWIdYdUa8aKt45mwVlrKev0NBHmoRUDUYqg6UIfjjfCPqoNbf6bacSOdQHzz3yh-wipatGcRNAOVoM/s1845/6.png)

![screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjytVw5Hy6Y7zG5gBvfNSFTvBG_arum_Z3uy8QNYnWllxcOMuW-tKjxBboIwQ3mMDNboUPbMbP1QUI6ZCtlxLa4eV7suzx4PCio6JkhKwAjkVkC5vadj_yJGZKFp17onXkJhSCHlkzdfg3Ltm24ZEZqM0cDnHC20OehrNYsNSLf6-JEpy8FKW2o0U9U-H0/s1847/7.png)

![screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh2JLR194HkbZqiJVfdQvsS7gITuifE7HH5J6vcP_5gJpisvSLpxIFoAbnljUYH4VjpLf6aFLx5PSbWf2csUYrd1VJNJ37GfKZ4Y36fEAd3Oqr6I6eTpWULO1uSSGK4Et62IKImqLRBqmmeiC9KM2XqJZvpSBmspAx31osU6fpr8iaSVjBdiKf9pyfHN1c/s1839/8.png)

![screenshot](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiJUPiSyYKUN55UE1ByGihzmhgL9zKQDS4GrDsCe2St0ZVv8yQMyOBFHQSYUbBGmPKYg6AUVrmA2WmFH9Z3Mrgm8AIwu86ZWqIMpHxVEuLFp_RnBAMswtP6f7-0Pgoo3Tv3CAbh1HYe2X9O_i6_Nf_Bkxxs6aN_MPy1D3caq-12LXdzeRiZAh727h6U_lU/s1844/9.png)

---

# Desarrollo local

## Requisitos

- Node.js 20+
- PostgreSQL 15+
- Cuenta en [Cloudinary](https://cloudinary.com) (para imágenes)
- Cuenta en [Resend](https://resend.com) (para correos)

---

## 1 — Clonar los repositorios

```bash
git clone https://github.com/IsmaelHeredia/streamcat-backend-nodejs.git
git clone https://github.com/IsmaelHeredia/streamcat-frontend-vuejs.git
```

---

## 2 — Backend

### Variables de entorno

Entrá al directorio del backend y renombrá `.env.example` a `.env`:

```bash
cd streamcat-backend-nodejs
```

```env
PORT=7777
NODE_ENV=development

DATABASE_URL="postgresql://user:pass@localhost:5432/streams"
DIRECT_URL="postgresql://user:pass@localhost:5432/streams"

JWT_SECRET="super-secret-key-change-this"
JWT_EXPIRES_IN="1d"
BCRYPT_ROUNDS=10

RESEND_API_KEY=re_xxxxxxxxxxxx
EMAIL_FROM=onboarding@resend.dev

CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

FRONTEND_URL=http://localhost:5173
```

### Instalar dependencias y preparar la base de datos

```bash
npm install
npx prisma migrate dev
npm run seed
```

### Levantar el servidor

```bash
npm run dev        # Modo desarrollo (tsx watch)
npm start          # Modo producción
```

El backend va a estar disponible en `http://localhost:7777`.

---

### Testing — Backend (Vitest + Supertest)

Las pruebas corren contra su propia base de datos para no pisar la de desarrollo.

#### 1 — Configurar el entorno de test

Renombrá `.env.test.example` a `.env.test`:

```env
DATABASE_URL="postgresql://testuser:testpass@localhost:5432/testdb"
```

#### 2 — Preparar la BD y ejecutar las pruebas

```bash
npm run test:migrate    # Resetea y migra la BD de test
npm test                # Corre todas las pruebas
npm run test:watch      # Modo watch
npm run test:coverage   # Con reporte de cobertura
```

También podés correr las pruebas por módulo:

```bash
npm run test:users
npm run test:streams
npm run test:genres
npm run test:covers
```

---

## 3 — Frontend

### Variables de entorno

Abrí una nueva terminal, entrá al directorio del frontend y renombrá `.env.example` a `.env`:

```bash
cd streamcat-frontend-vuejs
```

```env
VITE_API_URL="http://localhost:7777/api"
VITE_SESSION_NAME="app_session"
```

### Instalar dependencias e iniciar

```bash
npm install
npm run dev
```

El frontend va a estar disponible en `http://localhost:5173`.

---

### Testing E2E — Frontend (Playwright)

#### 1 — Configurar el entorno de test

Renombrá `.env.test.example` a `.env.test`:

```env
E2E_API_URL=http://localhost:7777/api
E2E_SESSION_NAME=streams_e2e_session
E2E_USER_EMAIL=admin@localhost.com
E2E_USER_PASSWORD=tu_password
```

#### 2 — Ejecutar las pruebas

```bash
npm run test:e2e           # Headless
npm run test:e2e:headed    # Con navegador visible
npm run test:e2e:ui        # Con UI interactiva de Playwright
```

---

# Docker

## Requisitos

- Docker y Docker Compose instalados.

---

## Backend

Entrá al directorio del backend:

```bash
cd streamcat-backend-nodejs
```

Renombrá `.env.docker.example` a `.env.docker` y completá los valores. Luego:

```bash
npm run docker:up      # Levanta todo (backend + PostgreSQL) con rebuild
npm run docker:dev     # Levanta sin rebuild
npm run docker:down    # Detiene los servicios
npm run docker:clean   # Detiene y elimina volúmenes
```

Servicios disponibles:

| Servicio | URL |
|---|---|
| Backend | `http://localhost:7777` |
| PostgreSQL | `localhost:5432` |

Comandos útiles dentro del contenedor:

```bash
npm run docker:seed       # Ejecutar seed
npm run docker:migrate    # Aplicar migraciones
npm run docker:shell      # Abrir shell en el contenedor
npm run docker:logs       # Ver logs del backend
npm run docker:db:logs    # Ver logs de PostgreSQL
npm run docker:psql       # Abrir psql en el contenedor
```

### Pruebas en Docker — Backend

Renombrá `.env.test.docker.example` a `.env.test.docker` y ejecutá:

```bash
npm run test:docker          # Levanta BD de test + corre pruebas
npm run test:docker:clean    # Limpia contenedores y volúmenes
npm run test:docker:logs     # Ver logs del test runner
```

---

## Frontend

Entrá al directorio del frontend:

```bash
cd streamcat-frontend-vuejs
```

Renombrá `.env.docker.example` a `.env.docker` y `.env.e2e.docker.example` a `.env.e2e.docker`. Luego:

```bash
npm run docker:up      # Levanta con rebuild
npm run docker:dev     # Levanta sin rebuild
npm run docker:down    # Detiene los servicios
npm run docker:clean   # Detiene y elimina volúmenes
```

El frontend va a estar disponible en `http://localhost:8888`.

### Pruebas E2E en Docker — Frontend

```bash
npm run e2e:docker:up      # Levanta el entorno E2E
npm run e2e:docker:test    # Corre las pruebas contra el entorno Docker
npm run e2e:docker:down    # Apaga los servicios
npm run e2e:docker:clean   # Apaga y limpia volúmenes
```

---

# CI/CD — GitHub Actions

Cada repositorio tiene su propio pipeline en `.github/workflows/ci.yml` que se dispara en cada push o PR a `main`.

## Backend

**Etapas:**

1. **Test**: Levanta un PostgreSQL efímero, crea `.env.test` automáticamente, aplica las migraciones y corre `npm test`.
2. **Deploy** *(solo en push a `main`)*: Aplica las migraciones de producción, corre el seed inicial y despliega en Vercel con `vercel deploy --prod`.

**Secrets requeridos:**

| Secret | Descripción |
|---|---|
| `DATABASE_URL` | URL de la BD de producción |
| `DIRECT_URL` | URL directa de la BD (requerida por Prisma en serverless) |
| `VERCEL_TOKEN` | Token de la CLI de Vercel |
| `VERCEL_ORG_ID` | ID de la organización en Vercel |
| `VERCEL_PROJECT_ID` | ID del proyecto backend en Vercel |

---

## Frontend

**Etapas:**

1. **Test E2E**: Instala Playwright + Chromium, crea los archivos `.env` y `.env.test` con los secrets necesarios y corre `npx playwright test`. Si falla, sube el reporte HTML como artefacto (retención de 7 días).
2. **Deploy** *(solo en push a `main`)*: Despliega en Vercel con `vercel deploy --prod`.

**Secrets requeridos:**

| Secret | Descripción |
|---|---|
| `VITE_API_URL` | URL del backend en producción |
| `VITE_SESSION_NAME` | Nombre de la sesión |
| `E2E_API_URL` | URL del backend para E2E |
| `E2E_SESSION_NAME` | Nombre de sesión para E2E |
| `E2E_USER_EMAIL` | Usuario de prueba |
| `E2E_USER_PASSWORD` | Contraseña del usuario de prueba |
| `VERCEL_TOKEN` | Token de la CLI de Vercel |
| `VERCEL_ORG_ID` | ID de la organización en Vercel |
| `VERCEL_PROJECT_ID` | ID del proyecto frontend en Vercel |