<template>
  <div class="container">
    <h1>Gestión de Tareas</h1>

    <div class="input-group">
      <input v-model="nuevaTarea" 
        type="text" 
        placeholder="Escribe una tarea..."
        @keyup.enter="agregarTarea" />

      <input v-model="fechaEntrega" type="date" />

      <button @click="agregarTarea">Agregar</button>
    </div>

    <p v-if="error" class="error">{{ error }}</p>

    <ul>
      <li 
        v-for="(tarea, index) in tareasOrdenadas" 
        :key="index"
        class="tarea"
        :class="obtenerClaseUrgencia(tarea)"
      >
        <div>
          <span :class="{ completada: tarea.completada }">
            {{ tarea.texto }}
          </span>
          <p class="fecha">
            📅 {{ tarea.fecha }}
          </p>
        </div>

        <div class="acciones">
          <button @click="completarTarea(index)">✔</button>
          <button @click="eliminarTarea(index)">❌</button>
        </div>
      </li>
    </ul>

    <p class="total">Total: {{ tareas.length }}</p>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const nuevaTarea = ref('')
const fechaEntrega = ref('')
const tareas = ref([])
const error = ref('')
const mensaje = ref('')

const agregarTarea = () => {
  if (nuevaTarea.value.trim() === '' || fechaEntrega.value === '') {
    error.value = "⚠️ Completa todos los campos"
    return
  }

  tareas.value.push({
    texto: nuevaTarea.value,
    fecha: fechaEntrega.value,
    completada: false
  })

  nuevaTarea.value = ''
  fechaEntrega.value = ''
  error.value = ''
}

const completarTarea = (index) => {
  tareas.value[index].completada = !tareas.value[index].completada
}

const eliminarTarea = (index) => {
  tareas.value.splice(index, 1)
}

const tareasOrdenadas = computed(() => {
  return [...tareas.value].sort((a, b) => new Date(a.fecha) - new Date(b.fecha))
})

const obtenerClaseUrgencia = (tarea) => {
  const hoy = new Date()
  const fecha = new Date(tarea.fecha)
  hoy.setHours(0, 0, 0, 0)
  fecha.setHours(0, 0, 0, 0)
  
  const diferencia = (fecha - hoy) / (1000 * 60 * 60 * 24)

  if (diferencia <= 1) return 'urgente'
  if (diferencia <= 3) return 'proxima'
  return 'normal'
}
</script>

<style scoped>
.container {
  max-width: 500px;
  margin: 40px auto;
  text-align: center;
  font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
  background: linear-gradient(135deg, #f9fafc 0%, #ffffff 100%);
  padding: 28px;
  border-radius: 24px;
  box-shadow: 0 20px 35px -12px rgba(0, 0, 0, 0.1);
}

h1 {
  font-size: 1.8rem;
  font-weight: 700;
  background: linear-gradient(135deg, #030038, #2a2a6e);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  margin-bottom: 24px;
  letter-spacing: -0.3px;
}

.input-group {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
  margin-bottom: 8px;
}

input {
  flex: 1;
  padding: 12px 16px;
  border-radius: 12px;
  border: 1.5px solid #e2e8f0;
  font-size: 14px;
  transition: all 0.2s ease;
  background: white;
}

input:focus {
  outline: none;
  border-color: #030038;
  box-shadow: 0 0 0 3px rgba(3, 0, 56, 0.1);
}

input[type="date"] {
  flex: 0.6;
  font-family: monospace;
}

button {
  padding: 12px 24px;
  border: none;
  border-radius: 12px;
  background: linear-gradient(135deg, #030038, #1a1a4e);
  color: white;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
  font-size: 14px;
}

button:hover {
  transform: translateY(-1px);
  box-shadow: 0 6px 14px rgba(3, 0, 56, 0.25);
}

button:active {
  transform: translateY(0);
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 24px;
}

.tarea {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: white;
  margin-bottom: 12px;
  padding: 14px 16px;
  border-radius: 14px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.04);
  transition: all 0.2s ease;
  animation: fadeIn 0.3s ease;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(8px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.tarea:hover {
  transform: translateX(2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.08);
}

.urgente {
  border-left: 5px solid #ef4444;
  background: linear-gradient(90deg, #fff5f5 0%, white 5%);
}

.proxima {
  border-left: 5px solid #f97316;
  background: linear-gradient(90deg, #fff7ed 0%, white 5%);
}

.normal {
  border-left: 5px solid #10b981;
}

.completada {
  text-decoration: line-through;
  color: #94a3b8;
}

.fecha {
  font-size: 11px;
  color: #64748b;
  margin-top: 4px;
  font-weight: 500;
  letter-spacing: -0.2px;
}

.acciones {
  display: flex;
  gap: 8px;
}

.acciones button {
  padding: 8px 12px;
  background: #f1f5f9;
  color: #334155;
  font-size: 14px;
  border-radius: 10px;
}

.acciones button:hover {
  background: #e2e8f0;
  transform: none;
  box-shadow: none;
}

.error {
  color: #ef4444;
  margin-top: 12px;
  font-size: 13px;
  font-weight: 500;
  background: #fef2f2;
  padding: 8px 12px;
  border-radius: 10px;
  display: inline-block;
}

.total {
  margin-top: 20px;
  font-weight: 600;
  color: #1e293b;
  background: #f1f5f9;
  padding: 10px;
  border-radius: 12px;
  font-size: 14px;
}
</style>