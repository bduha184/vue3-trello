<script setup lang="ts">
import { ref, reactive } from "vue";
import type { Category, Task } from "@/types";

const addCategory = reactive({
  show_category_input: false,
});
</script>

<template>
  <div style="min-width: 400px">
    <div class="bg-gray-200 m-2 p-2 text-sm">
      <div
        v-if="!addCategory.show_category_input"
        @click="addCategory.show_category_input = true"
      >
        カテゴリーを追加
      </div>
      <div v-else>
        <input
          type="text"
          class="w-full p-2"
          placeholder="新しいカテゴリー名を追加してください"
        />
        <div class="flex m-2">
          <button
            class="px-4 py-2 bg-green-500 hover:bg-green-700 text-white rounded-lg mr-2 font-bold"
          >
            追加
          </button>
          <button
            class="px-4 py-2 bg-red-500 hover:bg-red-700 text-white rounded-lg font-bold"
          >
            キャンセル
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
