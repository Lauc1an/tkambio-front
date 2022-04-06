<script setup>
import { ref } from 'vue'
import DownloadIcon from '../icons/DownloadIcon.vue'

const props = defineProps({
    table: Array
})

function download(id, filename) {
    fetch('http://tkambioapi.localhost/api/download-report/'+id)
    .then(res => res.blob())
    .then((data) => {
        let a = document.createElement("a")
        a.href = window.URL.createObjectURL(data)
        a.download = filename
        a.click()
    })
    .catch(err => console.log('err', err))
}
</script>

<template>
    <section class="container">
        <div class="table-container">
            <div class="table-row table-header">
                <div class="table-col">
                    Título
                </div>
                <div class="table-col">
                    Fecha de creación
                </div>
                <div class="table-col">
                    Acción
                </div>
            </div>
            <div v-for="row in table" class="table-row table-content">
                <div class="table-col title">
                    {{ row.title }}
                </div>
                <div class="table-col date">
                    {{ row.created_at }}
                </div>
                <div class="table-col action">
                    <button type="button" class="download-btn" @click="download(row.id, row.report_link)">
                        <p>Descargar</p>
                        <DownloadIcon class="icon"/>
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
.container {
    width: 100%;
    height: auto;
    display: flex;
    justify-content: center;
    .table-container {
        background-color: $blue;
        color: $white;
        width: 100%;
        height: auto;
        padding: 12px 30px 25px;
        border-radius: 10px;
        margin-bottom: 30px;
        .table-row {
            display: grid;
            grid-template-columns: 1fr 1fr 1fr;
            .table-col {
                text-align: center;
                &:first-child {
                  text-align: left;
                }
                &:last-child {
                  text-align: right;
                }
                &.title {
                    font-size: 12px;
                }
                &.action {
                    display: flex;
                    justify-content: flex-end;
                    align-items: center;
                    .download-btn {
                        background-color: transparent;
                        border: none;
                        display: flex;
                        cursor: pointer;
                        p {
                            font-weight: 600;
                            margin: 0;
                            color: $white;
                        }
                        .icon {
                            height: 16px;
                            width: auto;
                            margin-left: 5px;
                            margin-top: 4px;
                        }
                    }
                }
            }
            &.table-header {
                border-bottom: 4px solid $gray;
                padding-bottom: 15px;
            }
            &.table-content {
                padding: 12px 0;
                &:not(:last-child) {
                    border-bottom: 1px solid $gray;
                }
                .table-col {
                    &:not(:last-child) {
                        border-right: 4px solid $gray;
                    }
                }
            }
        }
    }
    @media (min-width: 768px) {
        .table-container {
            max-width: 630px;
        }
    }
}
</style>
