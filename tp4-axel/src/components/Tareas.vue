<template>
    <div>
        <h2>Tareas</h2>
        <input v-model="nuevaTarea" @keyup.enter="agregarTarea" placeholder="Agregar tarea..." />
        <ul>
            <li v-for="(tarea, index) in tareas" :key="index"
                :style="{ color: index < tareasPrevias ? 'lightblue' : 'white' }">{{ tarea }}
                <button @click="eliminarTarea(index)">🗑️</button>
            </li>
        </ul>

        <Alerta v-if="mostrarAlerta" />
    </div>
</template>

<script setup lang="ts">
import { ref, onBeforeUpdate, onUpdated } from 'vue';
import Alerta from './Alertas.vue'

const mostrarAlerta = ref(false)

const tareas = ref<string[]>(['Estudiar Vue', 'Hacer TP'])
const nuevaTarea = ref('')
let tareasPrevias = 0

onBeforeUpdate(() => {
    console.log("Lista aun no modificada")
    tareasPrevias = tareas.value.length
})

onUpdated(() => {
    console.log("Lista modificada")
})

function agregarTarea() {
    if (nuevaTarea.value.trim() === '') {
        mostrarAlerta.value = true
        setTimeout(() => mostrarAlerta.value = false, 2000)
        return
    }

    tareas.value.push(nuevaTarea.value.trim())
    nuevaTarea.value = ''
}
function eliminarTarea(index: number) {
    tareas.value.splice(index, 1)
}


</script>

<style scoped>
button {
    margin-left: 10px;
    background-color: #ff4d4d;
    color: white;
    border: none;
    border-radius: 4px;
    padding: 2px 6px;
    cursor: pointer;
}

button:hover {
    background-color: #cc0000;
}
</style>