# Copilot Instructions for proyectos-tecnologicos

## Project Overview
Sistema de Información de Proyectos Tecnológicos - An interactive web system built with Astro JS 5.16+ and Vue 3 for managing and filtering technology projects. Content and UI are in Spanish.

## Architecture & Structure

### Core Stack
- **Astro 5.16+**: Static site generator with islands architecture
- **Vue 3**: Interactive components with Composition API
- **TypeScript**: Strict mode enabled (`astro/tsconfigs/strict`)
- **Firebase Hosting**: Deployment target (configured for `/dist` output)

### Directory Layout
```
src/
  pages/
    index.astro         # Landing page with project info (static)
    catalogo.astro      # Interactive catalog page (Vue hydration)
  components/
    ProjectCatalog.vue  # Main container component
    ProjectFilter.vue   # Filter controls (area, estado, impacto)
    ProjectList.vue     # Project cards grid with reactive filtering
  data/
    projects.js         # Local data source (6 projects)
public/
  favicon.svg
```

## Key Architectural Decisions

### Islands Architecture Pattern
- **Pages are static by default**: `index.astro` is pure HTML/CSS (zero JS)
- **Selective hydration**: `catalogo.astro` uses `client:load` directive for Vue components
- **Data flow**: Astro passes data as props to Vue → Vue handles reactivity internally

### Component Communication
- `ProjectCatalog.vue` acts as state container
- `ProjectFilter.vue` emits `@update:filters` events upward
- `ProjectList.vue` receives projects + filters as props, uses computed for reactive filtering
- No global state management - props/events pattern only

## Development Workflow

### Commands
```bash
npm run dev      # Dev server at localhost:4321
npm run build    # Production build to ./dist/
npm run preview  # Preview production build
```

### Adding/Modifying Projects
Edit `src/data/projects.js` - Structure:
```js
{
  nombre: string,        // Project name
  area: string,          // Software|IA|IoT|Web|Redes|Seguridad
  descripcion: string,   // Brief description
  estado: string,        // Propuesto|En Desarrollo|Finalizado
  impacto: string        // Alto|Medio|Bajo
}
```

### Vue Component Patterns
- Use Composition API with `<script setup>`
- Props validation required for all components
- CSS is scoped to prevent leakage
- Emit events for parent communication (no prop mutation)

## Project Conventions

### Styling Approach
- CSS custom properties in `:root` for theming
- Inline `<style>` in `.astro` files for page-specific styles
- Scoped `<style>` in `.vue` components
- Mobile-first responsive design
- Color system: `--primary-color: #2563eb`, `--secondary-color: #1e40af`

### Language & Content
- All UI text, comments, and documentation in **Spanish**
- Variable names in Spanish (e.g., `estado`, `impacto`, `area`)
- This is intentional - maintain consistency

### TypeScript Configuration
- Extends `astro/tsconfigs/strict`
- `.astro/types.d.ts` auto-generated
- Vue SFC type checking enabled via `@astrojs/vue` integration

## Firebase Deployment

### Build Configuration
- Output directory: `./dist/`
- Static site (no SSR)
- Configure Firebase: `Public directory: dist`, `Single-page app: No`

### Deployment Steps
```bash
npm run build
firebase init hosting  # First time only
firebase deploy
```

## AI Development Notes

This project was built using:
- **GitHub Copilot**: Code completion and component scaffolding
- **Claude AI**: Architecture decisions and component logic

AI contributions documented in README.md - see "Uso de Inteligencia Artificial" section.

## Key Points for AI Agents
- This is NOT a minimal starter anymore - full interactive system
- Maintain Spanish language in all code and UI
- Respect islands architecture: don't add Vue to `index.astro` unnecessarily
- Filter logic lives in `ProjectList.vue` computed properties, not in parent
- Add new filter types by updating both `ProjectFilter.vue` selects and `ProjectList.vue` filtering logic
- CSS classes follow BEM-like naming in some places, utility classes elsewhere - maintain existing patterns

