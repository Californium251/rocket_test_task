<template>
    <div class="app-header">
        <a-typography-title :level="5">Тестовое задание. Автор Максим Курепов</a-typography-title>
        <a-input-search v-model:value="searchVal" placeholder="Введите запрос..." style="width: 200px" @search="onSearch" :disabled="props.loading" />
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
import axios from 'axios';

const props = defineProps({
    loading: Boolean,
})

const emit = defineEmits(['update:data', 'update:loading']);

const parseData = (query: string) => query.split(';').reduce((acc: { [key: string]: string }, el: string) => {
    const [key, value] = el.split('=');
    acc[key] = value;
    return acc;
}, {});

const getData = async (query: string) => {
    const url = import.meta.env.VITE_API_URL;
    const res = await axios.get(url, { params: parseData(query) })
    return res.data;
}

const ATypographyTitle = TypographyTitle;
const AInputSearch = InputSearch;
const ADivider = Divider;

const searchVal = ref('');
const onSearch = async (val: string) => {
    emit('update:loading', true);
    try {
        const data = await getData(val);
        emit('update:data', data);
    } catch (e) {
        console.error(e);
        emit('update:data', []);
    } finally {
        emit('update:loading', false);
    }
}
</script>