<script setup>
import { ref } from 'vue'
import Button from './Button.vue'
import CalendarIcon from '../icons/CalendarIcon.vue'

const emit = defineEmits(['close'])

const formDescription = ref()
const formStart = ref()
const formEnd = ref()

function submitForm() {
    let data = {
        "title": formDescription.value,
        "start": formStart.value,
        "end": formEnd.value
    }

    fetch(import.meta.env.VITE_API_URL + '/api/generate-report', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify(data),
    })
    .then(response => response.json())
    .then(data => {
        console.log('Success:', data);
        formDescription.value = ''
        formStart.value = ''
        formEnd.value = ''
        emit('close')
    })
    .catch((error) => {
        console.error('Error:', error);
    });
}
</script>

<template>
    <form @submit.prevent="submitForm">
        <div class="input-group">
            <label for="description">Descripcion del reporte</label>
            <input type="text" id="description" v-model="formDescription">
        </div>
        <p>Fecha de nacimiento</p>
        <div class="grid">
            <div class="input-group">
                <label for="start">Inicio</label>
                <input type="date" id="start" v-model="formStart">
                <CalendarIcon class="icon" />
            </div>
            <div class="input-group">
                <label for="end">Fin</label>
                <input type="date" id="end" v-model="formEnd">
                <CalendarIcon class="icon" />
            </div>
        </div>
        <div class="flex-center">
            <Button type="submit" />
        </div>
    </form>
</template>

<style lang="scss" scoped>
p {
    font-weight: 300;
    color: $gray-dark;
    font-size: 12px;
}
.grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-column-gap: 15px;
}
.flex-center {
    margin-top: 28px;
}
.input-group {
    position: relative;
    margin-top: 15px;
    margin-bottom: 10px;
    display: flex;
    label {
        position: absolute;
        background-color: $white;
        font-weight: 400;
        font-size: 12px;
        color: $gray-dark;
        top: -10px;
        left: 15px;
        padding: 0 5px;
    }
    input {
        display: block;
        width: 100%;
        border: 1px solid $gray;
        border-radius: 5px;
        height: 50px;
        padding: 0 10px;
    }
    .icon {
        height: 24px;
        width: auto;
        position: absolute;
        right: 10px;
        top: 14px;
    }
}
</style>
