# 💸 Summo — Wallet Personal de Ingresos, Gastos y Ahorro

<p align="center">
  <img src="brand-summo.png" alt="Summo Logo" width="220" style="border-radius: 28px;" />
</p>

> **Control financiero personal inteligente, privado y en tiempo real.**  
> Aplicación Web Progresiva (PWA) de alto rendimiento, diseñada con arquitectura *Zero-Build* (Vanilla HTML5 / CSS3 / ES6+) y respaldada en la nube por **Google Firebase**.

---

## 🌐 Enlaces de Producción

- **Dominio Principal**: [https://summo-wallet.web.app](https://summo-wallet.web.app)
- **Dominio Alternativo**: [https://summo-wallet.firebaseapp.com](https://summo-wallet.firebaseapp.com)
- **Dominio de Proyecto**: [https://wallet-personal-73c03.web.app](https://wallet-personal-73c03.web.app)

---

## 📋 Arquitectura y Características Principales

### 1. 🔐 Autenticación de Usuarios (Google Sign-In)
- **Proveedor OAuth**: Inicio de sesión seguro mediante Firebase Authentication con Google.
- **SDK Integrado**: `firebase-auth-compat.js` (v10.13.1).
- **Flujo de Acceso**: Ventana emergente (*Popup*) con mecanismo de contingencia automática (*Redirect*) para navegadores móviles con bloqueo de ventanas emergentes.
- **Manejo de Sesión**: Cierre de sesión seguro con liberación de escuchadores en tiempo real de Firestore en memoria.

### 2. 🗄️ Aislamiento y Privacidad Multi-Usuario en Cloud Firestore
- Cada usuario autenticado cuenta con un espacio de datos **100% aislado** bajo su propio identificador único (`UID`) de Google:
  ```text
  users/{userId}                         <- Perfil, tema visual y categorías personalizadas
  users/{userId}/transactions/{txId}     <- Movimientos financieros exclusivos del usuario
  ```

### 3. 🛡️ Reglas de Seguridad en Cloud Firestore (`firestore.rules`)
- Reglas de seguridad de nivel de producción auditadas:
  - **Propiedad Estricta**: Solo el propietario autenticado puede leer, crear, modificar o eliminar sus propios documentos (`request.auth.uid == userId`).
  - **Validación de Esquema**: Verificación estricta de tipos de datos, montos numéricos positivos, tipos de movimiento válidos (`income`, `expense`, `savings`), método de pago (`cash`, `card`) y límites de longitud.
  - **Denegación por Defecto**: Cualquier intento de acceso no autenticado o cruzado entre cuentas queda denegado automáticamente.

### 4. 🎨 Identidad Visual y Marca: "Summo"
- **Concepto**: Del latín *summo / summa* (*sumatoria, totalidad y punto más alto*), integrando visualización analítica y control de flujo financiero.
- **Activos Gráficos**:
  - `logo.png` / `icon.png` (`512x512`): Isotipo oficial "S+" entrelazado en verde esmeralda/turquesa 3D sobre fondo oscuro `#0D111C`.
  - `icon-192.png` (`192x192`): Ícono optimizado para instalación PWA en dispositivos móviles.
  - `brand-summo.png`: Logotipo completo con marca tipográfica oficial.

### 5. ✨ Experiencia de Usuario y Visualización Analítica (UI/UX)
- **Gráficos Vectoriales Dinámicos (SVG)**:
  - Curva interactiva de evolución histórica del saldo con cálculo acumulado, escalamiento lineal afín y tooltips detallados por movimiento.
  - Gráfico de anillo (*Donut Chart*) y barras proporcionales para distribución porcentual del gasto por categoría.
- **Diseño Adaptable Mobile & Desktop**: Barra superior compacta en móviles y barra de navegación lateral (*Sidebar*) en pantallas de escritorio, con 8 temas de color personalizables.
- **Registro Ágil**: Selector de fechas pasadas, teclado numérico táctil y atajos de teclado físico en escritorio (`0-9`, `.`, `Backspace`, `Enter`, `Esc`).
- **Portabilidad y Seguridad Cliente**: Exportación local de respaldos en formato JSON (`summo_backup_YYYY-MM-DD.json`) y sanitización HTML contra XSS.

---

## 📁 Estructura del Proyecto

```text
summo/
├── index.html        # Aplicación SPA completa (HTML5, estilos CSS3 y lógica JS cliente)
├── manifest.json     # Manifiesto PWA para instalación móvil y escritorio (Summo)
├── icon.png          # Ícono oficial PWA de alta resolución (512x512)
├── icon-192.png      # Ícono PWA estándar móvil (192x192)
├── logo.png          # Isotipo centrado para interfaz de usuario
├── brand-summo.png   # Logotipo completo con wordmark Summo
├── firebase.json     # Configuración de despliegue en Firebase Hosting (summo-wallet) y OAuth
├── firestore.rules   # Reglas de seguridad auditadas de Cloud Firestore
└── README.md         # Documentación técnica del proyecto
```

---

## 🚀 Comandos de Despliegue y Mantenimiento

```bash
# Desplegar cambios de interfaz/hosting en Firebase:
npx firebase-tools deploy --only hosting

# Desplegar actualizaciones en las reglas de Firestore:
npx firebase-tools deploy --only firestore:rules
```

---

*Diseñado y desarrollado por **Matías Pozas (Zeykox)**.*
