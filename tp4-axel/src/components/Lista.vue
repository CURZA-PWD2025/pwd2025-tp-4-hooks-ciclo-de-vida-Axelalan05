<template>
    <div>
        <h2>Profesiones</h2>
        <div v-if="profesiones.length === 0">Cargando...</div>
        <ul v-else>
            <li v-for="profesion in profesiones" :key="profesion.id">
                <strong>{{ profesion.nombre }}: </strong> {{ profesion.descripcion }}
            </li>
        </ul>
    </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from 'vue';
import profesionesData from '../resource/profesiones';

const profesiones = ref<any[]>([])

onMounted(() => {
    setTimeout(() => {
        profesiones.value = profesionesData
    }, 3000)
})

</script>

<style scoped></style>