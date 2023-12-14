<template>
    <a-table class="table" :columns="columns" :dataSource="dataSource" :pagination="{ pageSize }">
        
    </a-table>
</template>

<script setup lang="ts">
import { onMounted, onUnmounted, reactive, ref } from 'vue';
import { Table as ATable } from 'ant-design-vue';

type DataPiece = {
    name: string,
    budget: number,
    status: string,
    pta: string,
    date: Date,
}

const dataSource = reactive<DataPiece[]>([
    {
        name: 'some name',
        budget: 1000,
        status: 'some status',
        pta: 'some pta',
        date: new Date(),
    },
    {
        name: 'some name',
        budget: 1000,
        status: 'some status',
        pta: 'some pta',
        date: new Date(),
    },
    {
        name: 'some name',
        budget: 1000,
        status: 'some status',
        pta: 'some pta',
        date: new Date(),
    },
    {
        name: 'some name',
        budget: 1000,
        status: 'some status',
        pta: 'some pta',
        date: new Date(),
    },
    {
        name: 'some name',
        budget: 1000,
        status: 'some status',
        pta: 'some pta',
        date: new Date(),
    },
    {
        name: 'some name',
        budget: 1000,
        status: 'some status',
        pta: 'some pta',
        date: new Date(),
    },
    {
        name: 'some name',
        budget: 1000,
        status: 'some status',
        pta: 'some pta',
        date: new Date(),
    },
    {
        name: 'some name',
        budget: 1000,
        status: 'some status',
        pta: 'some pta',
        date: new Date(),
    },
    {
        name: 'some name',
        budget: 1000,
        status: 'some status',
        pta: 'some pta',
        date: new Date(),
    },
    {
        name: 'some name',
        budget: 1000,
        status: 'some status',
        pta: 'some pta',
        date: new Date(),
    },
    {
        name: 'some name',
        budget: 1000,
        status: 'some status',
        pta: 'some pta',
        date: new Date(),
    },
    {
        name: 'some name',
        budget: 1000,
        status: 'some status',
        pta: 'some pta',
        date: new Date(),
    },
])

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
        title: 'PTA',
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
    margin-top: 1rem;
}
</style>