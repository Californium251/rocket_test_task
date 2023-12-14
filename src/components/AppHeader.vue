<template>
    <div class="app-header">
        <a-typography-title :level="5">Тестовое задание. Автор Максим Курепов</a-typography-title>
        <a-input-search v-model:value="searchVal" placeholder="input search text" style="width: 200px" @search="onSearch" />
    </div>
    <a-divider />
</template>

<style>
.app-header {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
}
</style>

<script setup lang="ts">
import { ref } from 'vue';
import { TypographyTitle, InputSearch, Divider } from 'ant-design-vue';

const ATypographyTitle = TypographyTitle;
const AInputSearch = InputSearch;
const ADivider = Divider;

const searchVal = ref('');
const onSearch = (val: string) => {
    console.log(val);
}
</script>