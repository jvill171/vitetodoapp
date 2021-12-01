<script setup>
import useTodos from "../composables/useTodos";

const { pending, completed, changeStatus } = useTodos();

defineProps({
  isCompleted: {
    default: false,
    type: Boolean,
  },
});
</script>

<template>
  <div class="w-1/3">
    <h3
      class="text-2xl font-bold text-center text-red-500"
      :class="isCompleted ? 'text-green-600' : 'text-red-500'"
    >
      {{ isCompleted ? "Completed" : "Pending" }}
    </h3>
    <ul>
      <li
        v-for="todo in isCompleted ? completed : pending"
        :key="todo.id"
        @click="changeStatus(todo.id)"
        class="
          w-full
          py-2
          my-2
          text-center
          font-bold
          text-black
          bg-gray-300
          border border-black
          rounded-lg
          hover:text-white
          duration-500
        "
        :class="isCompleted ? 'hover:bg-red-500' : 'hover:bg-green-500'"
      >
        {{ todo.text }}
      </li>
    </ul>
  </div>
</template>
