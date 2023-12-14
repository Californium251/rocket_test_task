<script setup lang="ts">
import AppHeader from './AppHeader.vue'
import ResultsTable from './ResultsTable.vue'
</script>

<template>
    <div class="app-background">
        <div class="app-container">
            <AppHeader />
            <hr>
            <ResultsTable />
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
