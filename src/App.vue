<script setup lang="ts">
import category_data from './data/categories.json';
import task_data from './data/tasks.json';
import {ref} from 'vue';
import type {Category,Task} from './types/';

const categories = ref(category_data);
const tasks = ref(task_data);

</script>

<template>
 <div class="h-12 p-2">
    <h1 class="text-sm font-bold">Trello風タスク管理</h1>
 </div>
</template>
