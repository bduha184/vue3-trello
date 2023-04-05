<script setup lang="ts">
import category_data from './data/categories.json';
import task_data from './data/tasks.json';
import {ref,computed} from 'vue';
import type {Category,Task,CategoryTask} from './types/';
import CategoryItems from '@/components/CategoryItem.vue';

const categories = ref<Category[]>(category_data);
const tasks = ref<Task[]>(task_data);

const renderCategoryTask = computed<CategoryTask[]>(()=> {
  return categories.value.map(category => {
    const filterTasks = tasks.value.filter(
      task => task_data.category_id === category.id
    );
    return {
      id:category.id,
      name:category.name,
      tasks:filterTasks
    };
  });
})

</script>

<template>
 <div class="h-12 p-2">
    <h1 class="text-sm font-bold">Trello風タスク管理</h1>
    <div class="flex">
      <CategoryItems
        class="min-w-[400px]"
        v-for="categoryTask in renderCategoryTask"
        :key="categoryTask.id"
        :categoryTask="categoryTask"
      />
    </div>
 </div>
</template>
