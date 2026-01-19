# 🚀 Sistema de Información de Proyectos Tecnológicos

Sistema web informativo desarrollado con **Astro JS** y **Vue 3** para gestionar, visualizar y filtrar proyectos tecnológicos de forma interactiva.

## 📋 Descripción del Proyecto

Este sistema permite centralizar información sobre proyectos tecnológicos en diferentes áreas (Software, IA, IoT, Web, Redes, Seguridad), mostrando su estado de desarrollo y nivel de impacto. Los usuarios pueden filtrar proyectos dinámicamente sin recargar la página gracias a la reactividad de Vue 3.

## 🛠️ Tecnologías Utilizadas

- **Astro JS 5.16+**: Framework base para generación de sitios estáticos ultra-rápidos
- **Vue 3**: Framework reactivo para componentes interactivos
- **JavaScript ES6+**: Lógica de aplicación y manejo de datos
- **CSS3**: Estilos personalizados con diseño responsive
- **Firebase Hosting**: Plataforma de despliegue (preparado para deploy)

## 📂 Estructura del Proyecto

```
proyectos-tecnologicos/
├── src/
│   ├── pages/
│   │   ├── index.astro          # Página principal
│   │   └── catalogo.astro       # Catálogo interactivo
│   ├── components/
│   │   ├── ProjectCatalog.vue   # Contenedor principal del catálogo
│   │   ├── ProjectFilter.vue    # Componente de filtros
│   │   └── ProjectList.vue      # Lista de proyectos
│   └── data/
│       └── projects.js          # Datos locales (6 proyectos)
├── public/
│   └── favicon.svg
├── astro.config.mjs             # Configuración de Astro con Vue
├── package.json
└── README.md
```

## 🚀 Instalación y Ejecución

### Requisitos previos
- Node.js 18+ 
- npm o yarn

### Comandos

```bash
# Instalar dependencias
npm install

# Ejecutar servidor de desarrollo (localhost:4321)
npm run dev

# Generar build de producción
npm run build

# Previsualizar build antes de desplegar
npm run preview
```

## 🎯 Funcionalidades Implementadas

### ✅ Página Principal (`/`)
- Título y descripción del sistema
- Explicación sobre proyectos tecnológicos
- Lista de tecnologías utilizadas
- Enlace al catálogo

### ✅ Catálogo Interactivo (`/catalogo`)
- Visualización de 6 proyectos tecnológicos
- Filtros dinámicos por:
  - **Área**: Software, IA, IoT, Web, Redes, Seguridad
  - **Estado**: Propuesto, En Desarrollo, Finalizado
  - **Impacto**: Alto, Medio, Bajo
- Actualización en tiempo real sin recargar página
- Diseño responsive (mobile-first)
- Contador de resultados

### ✅ Componentes Vue
- **ProjectCatalog.vue**: Componente contenedor que maneja estado
- **ProjectFilter.vue**: Selectores de filtro con eventos reactivos
- **ProjectList.vue**: Grid de tarjetas con estilos dinámicos

### ✅ Datos Locales
Archivo `src/data/projects.js` con 6 proyectos estructurados:
- Sistema de Gestión Académica (Software - Finalizado - Alto)
- Chatbot Educativo con IA (IA - En Desarrollo - Alto)
- Sistema de Iluminación Inteligente (IoT - Propuesto - Medio)
- Portal Web Institucional (Web - Finalizado - Medio)
- Monitor de Redes (Redes - En Desarrollo - Alto)
- Auditor de Seguridad Informática (Seguridad - Propuesto - Bajo)

## 🤖 Uso de Inteligencia Artificial en el Desarrollo

### Herramientas de IA Utilizadas
- **GitHub Copilot**: Asistente de código en VS Code
- **Claude AI**: Generación de estructura y lógica de componentes

### Áreas donde la IA contribuyó:
1. **Estructura de componentes Vue**: Generación de template, script y styles con mejores prácticas
2. **Lógica de filtrado reactivo**: Implementación de computed properties y event handling
3. **Estilos CSS**: Diseño de sistema de colores, grid layouts y estados hover
4. **Documentación**: Generación de comentarios claros y este README
5. **Configuración de Astro**: Integración correcta de Vue 3 con directiva `client:load`

### 💭 Reflexión sobre el Valor de la IA

La inteligencia artificial aceleró significativamente el proceso de desarrollo al proporcionar código base estructurado y siguiendo convenciones modernas. Permitió enfocarse en la lógica de negocio en lugar de sintaxis repetitiva, reduciendo errores comunes y mejorando la calidad del código mediante sugerencias contextuales. La IA no reemplazó la toma de decisiones arquitectónicas, pero actuó como un excelente copiloto que optimizó tiempos y garantizó consistencia en todo el proyecto.

## 🔥 Despliegue en Firebase Hosting

### Preparación
El proyecto está listo para desplegarse en Firebase Hosting:

```bash
# 1. Instalar Firebase CLI (si no lo tienes)
npm install -g firebase-tools

# 2. Iniciar sesión en Firebase
firebase login

# 3. Inicializar proyecto Firebase
firebase init hosting

# Configuración recomendada:
# - Public directory: dist
# - Single-page app: No
# - Automatic builds: No

# 4. Generar build de producción
npm run build

# 5. Desplegar a Firebase
firebase deploy
```

### Notas Importantes
- El build genera la carpeta `dist/` con archivos estáticos optimizados
- No se requiere base de datos ni autenticación
- Los componentes Vue se hidratan en el cliente con `client:load`
- Tiempo de carga optimizado gracias a Astro (islands architecture)

## 📝 Características Técnicas

### Arquitectura
- **Islands Architecture**: Astro renderiza páginas estáticas y Vue solo donde se necesita interactividad
- **Hidratación selectiva**: `client:load` carga Vue al cargar la página del catálogo
- **Zero JS por defecto**: La página principal es HTML puro (ultra-rápida)

### Buenas Prácticas Implementadas
- Código modular y reutilizable
- Componentes Vue con Single File Component (SFC)
- Props tipadas con validación
- CSS scoped para evitar colisiones de estilos
- Diseño responsive con mobile-first
- Comentarios explicativos en código
- Separación de datos y lógica de presentación

## 👨‍💻 Desarrollo

Este proyecto fue desarrollado siguiendo los principios de:
- Clean Code
- Component-driven development
- Responsive design
- Accesibilidad web básica

## 📄 Licencia

Proyecto educativo - 2026
firebase hosting
https://proyectos-tecnologicos-astro.web.app/
