<script setup>
import { ref } from 'vue'
import Form from './Form.vue'

</script>

<template>
    <div class="modal-back" @click="$emit('closeModal')">
        <div class="modal" @click.stop>
            <h2 class="title">Reporte por fecha de nacimiento</h2>
            <p>Ingresa los siguientes datos para generar tu reporte</p>
            <Form @close="$emit('closeModal')"/>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.modal-back {
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    .modal {
        background: $white;
        box-shadow: 1px 3px 13px -3px;
        overflow-x: auto;
        display: flex;
        flex-direction: column;
        border-radius: 10px;
        padding: 20px 28px 35px;
        width: 480px;
        .title {
            font-weight: 700;
            font-size: 24px;
            text-align: center;
            margin-bottom: 9px;
        }
        p {
            font-weight: 300;
            color: $gray-dark;
            text-align: center;
            margin-bottom: 20px;
        }
    }
}
</style>
