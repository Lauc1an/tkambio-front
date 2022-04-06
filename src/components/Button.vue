<script setup>
// import { ref } from 'vue'

const props = defineProps({
    type: String
})

</script>

<template>
    <button :type="type" class="btn">Crear reporte</button>
</template>

<style lang="scss" scoped>
.btn {
    background-color: $yellow;
    padding: 11px 42px;
    border-radius: 100%;
    border-radius: 30px;
    font-weight: 500;
    font-size: 16px;
    border: none;
    cursor: pointer;
}
</style>
