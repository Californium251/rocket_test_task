<script setup lang="ts">
import AppHeader from './AppHeader.vue'
import ResultsTable from './ResultsTable.vue'
import { ref } from 'vue';
import type { DataPiece } from './ResultsTable.vue';

const data = ref<Array<DataPiece>>([]);
const loading = ref<boolean>(false);

const updateData = (newData: Array<DataPiece>) => {
    data.value = newData;
}

const updateLoading = (newVal: boolean) => {
    loading.value = newVal;
}

</script>

<template>
    <div class="app-background">
        <div class="app-container">
            <AppHeader @update:data="updateData" @update:loading="updateLoading" :loading="loading" />
            <hr>
            <ResultsTable :data="data" :loading="loading" />
        </div>    
    </div>
</template>

<style scoped>
.app-background {
    width: 100%;
    height: 100vh;
    padding-top: 1rem;
    background-color: #e5e5e5;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    box-sizing: border-box;
}

.app-container {
    min-width: 90%;
    background-color: #fff;
    padding: 2rem;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}
</style>
