<script setup>
import { ref, onBeforeMount  } from 'vue'
import Navbar from './components/Navbar.vue'
import TableReport from './components/TableReport.vue'
import Button from './components/Button.vue'
import Modal from './components/Modal.vue'

const showModal = ref(false)
const dataTable = ref([])

onBeforeMount(() => {
    fetch(import.meta.env.VITE_API_URL + '/api/list-reports')
    .then(response => response.json())
    .then(data => dataTable.value = data)
    .catch(err => console.log('err', err))
})

</script>

<template>
    <Navbar />
    <h1 class="main-title">Generador de reportes TK</h1>
    <TableReport :table="dataTable" />
    <div class="flex-center">
        <Button type="button" @click="showModal = true"/>
    </div>
    <Modal v-if="showModal" @closeModal="showModal = false"/>
</template>

<style lang="scss">
.main-title {
    color: $black;
    text-align: center;
    margin-top: 50px;
    margin-bottom: 96px;
    font-weight: 500;
    font-size: 28px;
}
.flex-center {
    display: flex;
    justify-content: center;
}
</style>
