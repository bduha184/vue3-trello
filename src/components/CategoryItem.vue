<script setup lang="ts">
import type { CategoryTask, Task } from '@/types';
import TaskItem from './TaskItem.vue';

defineProps<{
  categoryTask:CategoryTask;
}>();

const emit = defineEmits<{
  (e:"setDragTask",task:Task):void;
}>();

const setDragTask = (task:Task)=> {
  emit("setDragTask",task);
}

</script>
<template>
   <div class="bg-gray-200 m-2 p-2 text-sm">
    <span class="font-bold"> {{ categoryTask.name }}</span>
    <TaskItem
    v-for="task in categoryTask.tasks"
    :key="task.id"
    :task="task"
    class="m-2 bg-white p-2"
    draggable="true"
    @dragstart="setDragTask"
    />
  </div>
</template>
