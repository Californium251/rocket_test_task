<template>
    <div style="display: block; width: 100%">
        <a-spin class="spinner" :spinning="props.loading">
            <a-table class="table" :columns="columns" :dataSource="props.data" :pagination="{ pageSize }"></a-table>
        </a-spin>
    </div>
</template>

<script setup lang="ts">
import { onMounted, onUnmounted, reactive, ref } from 'vue';
import { Table as ATable, Spin as ASpin } from 'ant-design-vue';
import { defineProps } from 'vue';

export type DataPiece = {
    name: string,
    budget: number,
    status: string,
    pta: string,
    date: Date,
}

const props = defineProps({
    data: Array<DataPiece>,
    loading: Boolean,
})

const columns = reactive<Array<{ title: string, key: string, dataIndex?: string }>>([
    {
        title: 'Название',
        dataIndex: 'name',
        key: 'name',
    },
    {
        title: 'Бюджет',
        dataIndex: 'budget',
        key: 'budget',
    },
    {
        title: 'Статус',
        dataIndex: 'status',
        key: 'status',
    },
    {
        title: 'Ответственный',
        dataIndex: 'pta',
        key: 'pta',
    },
    {
        title: 'Дата',
        dataIndex: 'date',
        key: 'date',
    }
]);

const getPageSize = () => {
    if (window.innerHeight <= 450) {
        console.log('here')
        return 1;
    }
    return Math.floor((window.innerHeight - 400) / 50) + 1;
}
const pageSize = ref(getPageSize());

const handleResize = () => {
    pageSize.value = getPageSize();
}

onMounted(() => {
    window.addEventListener('resize', handleResize);
})

onUnmounted(() => {
    window.removeEventListener('resize', handleResize);
})
</script>

<style>
.table {
    width: 100%;
    display: block;
}

.spinner {
    width: 100%;
    margin-top: 1rem;
    display: block;
}
</style>