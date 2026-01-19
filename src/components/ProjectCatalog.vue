<template>
  <div class="catalog-container">
    <!-- Componente de filtros -->
    <ProjectFilter @update:filters="handleFilterChange" />
    
    <!-- Componente de lista de proyectos -->
    <ProjectList :projects="projects" :filters="currentFilters" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import ProjectFilter from './ProjectFilter.vue';
import ProjectList from './ProjectList.vue';

// Props recibidas desde Astro
const props = defineProps({
  projects: {
    type: Array,
    required: true
  }
});

// Estado local de filtros
const currentFilters = ref({
  area: 'Todas',
  estado: 'Todos',
  impacto: 'Todos'
});

// Manejar cambios en los filtros
const handleFilterChange = (newFilters) => {
  currentFilters.value = newFilters;
};
</script>

<style scoped>
.catalog-container {
  width: 100%;
}
</style>
