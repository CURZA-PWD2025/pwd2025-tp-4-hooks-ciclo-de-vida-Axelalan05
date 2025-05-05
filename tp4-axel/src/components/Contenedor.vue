<template>
    <div>
        <select v-model="componenteSeleccionado">
            <option value="Lista">Lista</option>
            <option value="Tareas">Tareas</option>
            <option value="DimensionComponente">Dimension</option>
        </select>

        <keep-alive>
            <component :is="componentes[componenteSeleccionado]" />
        </keep-alive>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import Lista from './Lista.vue'
import Tareas from './Tareas.vue'
import DimensionComponente from './DimensionComponente.vue'

const componenteSeleccionado = ref<'Lista' | 'Tareas' | 'DimensionComponente'>('Lista')

const componentes = {
    Lista,
    Tareas,
    DimensionComponente
}

</script>

<style scoped></style>