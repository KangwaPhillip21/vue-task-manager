<script setup lang="ts">
import { ref } from 'vue'

const task = ref('')
const tasks = ref<string[]>([])

const addTask = () => {
  if (task.value.trim()) {
    tasks.value.push(task.value)
    task.value = ''
  }
}

const deleteTask = (index: number) => {
  tasks.value.splice(index, 1)
}
</script>

<template>
  <div class="container">
    <h1>Task Manager</h1>

    <input
      v-model="task"
      placeholder="Enter a task"
    />

    <button @click="addTask">
      Add Task
    </button>

    <ul>
  <li v-for="(item, index) in tasks" :key="index">
    {{ item }}
    <button @click="deleteTask(index)">Delete</button>
  </li>
</ul>
  </div>
</template>

<style>
.container {
  max-width: 600px;
  margin: 50px auto;
  text-align: center;
}

input {
  padding: 10px;
  width: 250px;
}

button {
  padding: 10px 20px;
  margin-left: 10px;
  cursor: pointer;
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 20px;
}

li {
  padding: 10px;
  border: 1px solid #ddd;
  margin-top: 10px;
}
</style>