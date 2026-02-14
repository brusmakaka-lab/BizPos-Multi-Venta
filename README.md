# BizPOS - Sistema de Punto de Venta

Sistema de punto de venta (POS) offline-first para Windows, desarrollado en Flutter.

## 🎯 Características Principales

- ✅ **Offline-first**: Funciona sin conexión a internet
- ✅ **Multi-usuario**: Sistema de roles (Owner/Employee) con permisos granulares
- ✅ **Gestión completa**: Productos, ventas, stock, caja, clientes
- ✅ **Auditoría**: Registro de todas las acciones críticas
- ✅ **Reportes**: Dashboard con gráficos y estadísticas
- ✅ **Tickets PDF**: Generación e impresión de comprobantes
- ✅ **Scanner USB**: Soporte para lector de código de barras
- ✅ **Backups**: Sistema automático de respaldo
- ✅ **6 Rubros**: Kiosko, Clothing, Mini E-commerce, Library, Restaurant, Other
- ✅ **Logo del negocio**: Personalización en tickets
- ✅ **Pagos múltiples**: Efectivo, Débito, Crédito, QR, Transferencia

## 🏗️ Arquitectura

### Stack Tecnológico

- **Framework**: Flutter 3.x (Windows Desktop)
- **Estado**: Riverpod
- **Base de datos**: Drift (SQLite local)
- **Routing**: go_router
- **PDF**: pdf + printing
- **Gráficos**: fl_chart

### Estructura del Proyecto

```
lib/
├── main.dart                 # Punto de entrada
├── app.dart                  # Configuración de la app
├── bootstrap.dart            # Inicialización
│
├── core/                     # Núcleo de la aplicación
│   ├── theme/               # Tema y estilos
│   ├── routing/             # Navegación y guards
│   ├── services/            # Servicios (PDF, Backup, CSV)
│   ├── constants/           # Constantes y enums
│   └── models/              # Modelos de datos
│
├── data/                     # Capa de datos
│   ├── db/                  # Provider de base de datos (Drift)
│   └── repositories/        # Acceso a datos
│
├── features/                 # Features por módulo
│   ├── onboarding/          # Primera configuración
│   ├── auth/                # Autenticación
│   ├── pos/                 # Punto de venta
│   ├── products/            # Gestión de productos
│   ├── cash/                # Caja y turnos
│   ├── dashboard/           # Dashboard y reportes
│   ├── customers/           # Gestión de clientes
│   ├── reports/            # Reportes avanzados
│   └── settings/            # Configuración
│
└── shared/                   # Componentes compartidos
    ├── widgets/             # Widgets reutilizables
    └── dialogs/             # Diálogos comunes
```

## 📊 Rubros con Categorías

| Rubro | Categorías por Defecto |
|-------|------------------------|
| **Kiosko** | Golosinas, Bebidas, Cigarrillos, Limpieza, Panadería |
| **Clothing** | Remeras, Pantalones, Abrigos, Accesorios, Vestidos |
| **Mini E-commerce** | Electrónica, Hogar, Ropa, Juguetes, Deportes |
| **Library** | Libros, Escuela, Oficina, Revistas, Regalos |
| **Restaurant** | Platos Principales, Bebidas, Postres, Aperitivos, Delivery |
| **Other** | General, Ofertas, Nuevos |

## 🔐 Sistema de Permisos

### Roles

- **Owner**: Acceso total al sistema
- **Employee**: Acceso limitado según permisos

### Permisos Configurables

- Gestión de productos
- Ver costos y ganancias
- Aplicar descuentos (con límite %)
- Anular ventas
- Manejar caja (retiros/gastos)
- Ver reportes

## 🚀 Instalación y Desarrollo

### Requisitos

- Flutter SDK 3.2.0 o superior
- Windows 10/11
- Git

### Instalación

```bash
# Clonar repositorio
git clone <repo-url>
cd bizpos

# Instalar dependencias
flutter pub get

# Generar código (Drift + Riverpod)
dart run build_runner build

# Ejecutar en debug
flutter run -d windows
```

### Generar código (watch mode)

```bash
dart run build_runner watch
```

## 📦 Build para Producción

```bash
# Build Windows release
flutter build windows --release

# Crear instalador (requiere Inno Setup 6)
"C:\Program Files\Inno Setup 6\ISCC.exe" windows/installer/bizpos-installer.iss
```

## ✅ Estado de Implementación (v1.6.0)

### Fase 1: Fundación
- [x] Setup del proyecto
- [x] Modelos de datos
- [x] Base de datos (Drift/SQLite)
- [x] Servicios base (Logger, Backup, CSV)
- [x] Tema y routing

### Fase 2: Features Core
- [x] Onboarding completo
- [x] Sistema de autenticación
- [x] CRUD de productos
- [x] POS con scanner USB
- [x] Sistema de ventas

### Fase 3: Operaciones
- [x] Gestión de caja
- [x] Devoluciones y anulaciones
- [x] Generación de tickets PDF
- [x] Sistema de clientes

### Fase 4: Reportes y Cierre
- [x] Dashboard con gráficos
- [x] Reportes avanzados
- [x] Sistema de backups completo
- [x] Empaquetado e instalador

## 📝 Cambios en v1.6.0

### Correcciones
- **Archivo pos_page.dart**: Reconstruido y corregido el código duplicado
- **Botones de pago rápido**: Funcionalidad corregida ($500, $1000, $2000, etc.)
- **Sincronización POS**: Los productos se actualizan automáticamente en tiempo real
- **Ajuste de stock**: Botón guardar funciona correctamente

### Mejoras
- Código optimizado y limpio
- Mejora en la gestión de estado entre módulos

## 📝 Notas de Desarrollo

- Los modelos de Drift requieren generación de código con `build_runner`
- El sistema está diseñado para funcionar 100% offline
- Los snapshots en ventas garantizan consistencia de reportes
- El sistema de permisos se valida tanto en UI como en lógica de negocio
- El logo se guarda en `data/logo.png` y se muestra en tickets PDF

## 🤝 Contribución

Este es un proyecto privado. Para cambios mayores, crear un branch feature y solicitar revisión.

## 📄 Licencia

Propietario - Todos los derechos reservados

---

**Versión**: 1.6.0  
**Última actualización**: 2026-02-14
