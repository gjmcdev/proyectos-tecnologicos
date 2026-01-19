<template>
  <div class="project-list">
    <div v-if="filteredProjects.length === 0" class="no-results">
      <p>📭 No se encontraron proyectos con los filtros seleccionados.</p>
    </div>
    
    <div v-else class="projects-grid">
      <div 
        v-for="project in filteredProjects" 
        :key="project.nombre" 
        class="project-card"
      >
        <div class="card-header">
          <h3 class="project-name">{{ project.nombre }}</h3>
          <span class="badge badge-area">{{ project.area }}</span>
        </div>
        
        <p class="project-description">{{ project.descripcion }}</p>
        
        <div class="card-footer">
          <span 
            class="badge badge-estado" 
            :class="getEstadoClass(project.estado)"
          >
            {{ project.estado }}
          </span>
          <span 
            class="badge badge-impacto" 
            :class="getImpactoClass(project.impacto)"
          >
            Impacto: {{ project.impacto }}
          </span>
        </div>
      </div>
    </div>
    
    <div class="results-count">
      Mostrando {{ filteredProjects.length }} de {{ projects.length }} proyectos
    </div>
  </div>
</template>

<script setup>
import { computed } from 'vue';

// Props recibidas desde el componente padre
const props = defineProps({
  projects: {
    type: Array,
    required: true
  },
  filters: {
    type: Object,
    default: () => ({
      area: 'Todas',
      estado: 'Todos',
      impacto: 'Todos'
    })
  }
});

// Computed para filtrar proyectos reactivamente
const filteredProjects = computed(() => {
  return props.projects.filter(project => {
    const matchArea = props.filters.area === 'Todas' || project.area === props.filters.area;
    const matchEstado = props.filters.estado === 'Todos' || project.estado === props.filters.estado;
    const matchImpacto = props.filters.impacto === 'Todos' || project.impacto === props.filters.impacto;
    
    return matchArea && matchEstado && matchImpacto;
  });
});

// Funciones para asignar clases CSS dinámicas
const getEstadoClass = (estado) => {
  const classes = {
    'Finalizado': 'estado-finalizado',
    'En Desarrollo': 'estado-desarrollo',
    'Propuesto': 'estado-propuesto'
  };
  return classes[estado] || '';
};

const getImpactoClass = (impacto) => {
  const classes = {
    'Alto': 'impacto-alto',
    'Medio': 'impacto-medio',
    'Bajo': 'impacto-bajo'
  };
  return classes[impacto] || '';
};
</script>

<style scoped>
.project-list {
  width: 100%;
}

.no-results {
  text-align: center;
  padding: 3rem;
  background: #f8fafc;
  border-radius: 0.75rem;
  color: #64748b;
  font-size: 1.1rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 1.5rem;
  margin-bottom: 2rem;
}

.project-card {
  background: white;
  border: 1px solid #e2e8f0;
  border-radius: 0.75rem;
  padding: 1.5rem;
  transition: all 0.3s ease;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
}

.project-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
  border-color: #2563eb;
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: start;
  margin-bottom: 1rem;
  gap: 1rem;
}

.project-name {
  font-size: 1.25rem;
  color: #1e293b;
  font-weight: 700;
  margin: 0;
  line-height: 1.3;
  flex: 1;
}

.project-description {
  color: #475569;
  line-height: 1.6;
  margin-bottom: 1.25rem;
  font-size: 0.95rem;
}

.card-footer {
  display: flex;
  gap: 0.75rem;
  flex-wrap: wrap;
}

.badge {
  padding: 0.4rem 0.75rem;
  border-radius: 0.375rem;
  font-size: 0.8rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.025em;
}

.badge-area {
  background: #dbeafe;
  color: #1e40af;
}

.badge-estado {
  flex: 1;
  text-align: center;
}

.estado-finalizado {
  background: #d1fae5;
  color: #065f46;
}

.estado-desarrollo {
  background: #fef3c7;
  color: #92400e;
}

.estado-propuesto {
  background: #e0e7ff;
  color: #3730a3;
}

.badge-impacto {
  flex: 1;
  text-align: center;
}

.impacto-alto {
  background: #fee2e2;
  color: #991b1b;
}

.impacto-medio {
  background: #fed7aa;
  color: #9a3412;
}

.impacto-bajo {
  background: #e5e7eb;
  color: #374151;
}

.results-count {
  text-align: center;
  color: #64748b;
  font-size: 0.95rem;
  padding: 1rem;
  background: #f8fafc;
  border-radius: 0.5rem;
}

@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
  
  .card-header {
    flex-direction: column;
  }
}
</style>
