<template>
  <div class="filter-panel">
    <h2 class="filter-title">🔍 Filtrar Proyectos</h2>
    
    <div class="filters-grid">
      <!-- Filtro por Área -->
      <div class="filter-group">
        <label for="filter-area" class="filter-label">
          <span class="label-icon">📂</span>
          Área Tecnológica
        </label>
        <select 
          id="filter-area"
          v-model="localFilters.area" 
          @change="emitFilters"
          class="filter-select"
        >
          <option value="Todas">Todas las áreas</option>
          <option value="Software">Software</option>
          <option value="IA">Inteligencia Artificial</option>
          <option value="IoT">Internet de las Cosas</option>
          <option value="Web">Desarrollo Web</option>
          <option value="Redes">Redes</option>
          <option value="Seguridad">Seguridad</option>
        </select>
      </div>

      <!-- Filtro por Estado -->
      <div class="filter-group">
        <label for="filter-estado" class="filter-label">
          <span class="label-icon">⚡</span>
          Estado del Proyecto
        </label>
        <select 
          id="filter-estado"
          v-model="localFilters.estado" 
          @change="emitFilters"
          class="filter-select"
        >
          <option value="Todos">Todos los estados</option>
          <option value="Finalizado">Finalizado</option>
          <option value="En Desarrollo">En Desarrollo</option>
          <option value="Propuesto">Propuesto</option>
        </select>
      </div>

      <!-- Filtro por Impacto -->
      <div class="filter-group">
        <label for="filter-impacto" class="filter-label">
          <span class="label-icon">🎯</span>
          Nivel de Impacto
        </label>
        <select 
          id="filter-impacto"
          v-model="localFilters.impacto" 
          @change="emitFilters"
          class="filter-select"
        >
          <option value="Todos">Todos los niveles</option>
          <option value="Alto">Alto</option>
          <option value="Medio">Medio</option>
          <option value="Bajo">Bajo</option>
        </select>
      </div>
    </div>

    <!-- Botón de reseteo -->
    <button 
      @click="resetFilters" 
      class="reset-button"
      :disabled="isDefaultFilters"
    >
      🔄 Restablecer Filtros
    </button>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';

// Emits para comunicar cambios al padre
const emit = defineEmits(['update:filters']);

// Estado local de filtros
const localFilters = ref({
  area: 'Todas',
  estado: 'Todos',
  impacto: 'Todos'
});

// Computed para verificar si están en valores por defecto
const isDefaultFilters = computed(() => {
  return localFilters.value.area === 'Todas' &&
         localFilters.value.estado === 'Todos' &&
         localFilters.value.impacto === 'Todos';
});

// Emitir filtros actualizados al componente padre
const emitFilters = () => {
  emit('update:filters', { ...localFilters.value });
};

// Resetear todos los filtros
const resetFilters = () => {
  localFilters.value = {
    area: 'Todas',
    estado: 'Todos',
    impacto: 'Todos'
  };
  emitFilters();
};
</script>

<style scoped>
.filter-panel {
  background: white;
  border: 1px solid #e2e8f0;
  border-radius: 0.75rem;
  padding: 1.5rem;
  margin-bottom: 2rem;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.05);
}

.filter-title {
  font-size: 1.5rem;
  color: #1e293b;
  margin-bottom: 1.5rem;
  font-weight: 700;
}

.filters-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.25rem;
  margin-bottom: 1.5rem;
}

.filter-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.filter-label {
  font-weight: 600;
  color: #475569;
  font-size: 0.95rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
}

.label-icon {
  font-size: 1.1rem;
}

.filter-select {
  padding: 0.75rem;
  border: 2px solid #e2e8f0;
  border-radius: 0.5rem;
  font-size: 1rem;
  color: #1e293b;
  background: white;
  cursor: pointer;
  transition: all 0.2s ease;
  font-family: inherit;
}

.filter-select:hover {
  border-color: #cbd5e1;
}

.filter-select:focus {
  outline: none;
  border-color: #2563eb;
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
}

.reset-button {
  width: 100%;
  padding: 0.875rem;
  background: #f1f5f9;
  border: 2px solid #e2e8f0;
  border-radius: 0.5rem;
  color: #475569;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: all 0.2s ease;
  font-family: inherit;
}

.reset-button:hover:not(:disabled) {
  background: #e2e8f0;
  border-color: #cbd5e1;
  color: #1e293b;
}

.reset-button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}

.reset-button:active:not(:disabled) {
  transform: scale(0.98);
}

@media (max-width: 768px) {
  .filters-grid {
    grid-template-columns: 1fr;
  }
  
  .filter-panel {
    padding: 1rem;
  }
}
</style>
