<script setup>
  import {ref, computed} from 'vue';

  const newTodo = ref("");

  const todos = ref([]);

  const pending = computed(() => {
    return todos.value.filter((todo) => !todo.done);
  });
  const completed = computed(() => {
    return todos.value.filter((todo) => todo.done);
  });

  const addTodo = () => {
    if(newTodo.value.trim()){
      todos.value.push({
        id: todos.value.length,
        content: newTodo.value,
        done: false,
      });
    newTodo.value = "";
    }
  };

  const changeStatus = (id) =>{
    const todo = todos.value.find((todo) => todo.id === id);
    todo.done = !todo.done;
  }
  
  
</script>

<template>
<div class="min-h-screen bg-purple-200">
  <div class="container flex flex-col pt-8 mx-auto space-y-10">
    <h1 class="text-6xl font-thin tracking-tight text-center text-blue-800">My Todo App</h1>
    <input 
      @change="addTodo"
      v-model="newTodo" 
      type="text"
      class="px-4 py-2 text-center border border-black rounded-lg" placeholder="New Todo"/>
    <div class="flex justify-between">
      <div class="w-1/3">
        <h3 class="text-2xl font-bold text-center text-red-500">Pending</h3>
          <ul>
            <li v-for="todo in pending"
            :key="todo.id"
            @click="changeStatus(todo.id)"
             class="w-full py-2 my-2 text-center font-bold text-black bg-gray-300 border border-black rounded-lg hover:bg-green-500 hover:text-white duration-500">
              {{todo.content}}
            </li>
          </ul>
      </div>
      <div class="w-1/3">
        <h3 class="text-2xl font-bold text-center text-green-600">Completed</h3>
          <ul>
            <li v-for="todo in completed"
            :key="todo.id"
            @click="changeStatus(todo.id)"
             class="w-full py-2 my-2 text-center font-bold text-black bg-gray-300 border border-black rounded-lg hover:bg-red-500 hover:text-white duration-500">
             {{todo.content}}</li>
          </ul>
      </div>
    </div >
  </div>
</div>
</template>

