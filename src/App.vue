<script setup>
  import Title from "./components/Title.vue";
  import List from "./components/List.vue";
</script>

<template>
  <div class="min-h-screen bg-purple-200">
    <div class="container flex flex-col pt-8 mx-auto space-y-10">
      <Title/>
      <div class="flex justify-between">
      <List />
      <List isCompleted/>
        <!-- <div class="w-1/3">
          <h3 class="text-2xl font-bold text-center text-green-600">Completed</h3>
            <ul>
              <li v-for="todo in completed"
              :key="todo.id"
              @click="changeStatus(todo.id)"
              class="w-full py-2 my-2 text-center font-bold text-black bg-gray-300 border border-black rounded-lg hover:bg-red-500 hover:text-white duration-500">
              {{todo.content}}</li>
            </ul>
        </div> -->
      </div >
    </div>
  </div>
</template>