<script setup>
import { ref } from 'vue'

const task = ref([]);
const newTask = ref('');

const addTask = () => {
  if (newTask.value) {
    task.value.push({
      text: newTask.value,
      completed: false,
    });
    newTask.value = '';
  }
}

const removeTask = (index) => {
  task.value.splice(index, 1);
}
</script>

<template>
  <div>
    <form @submit.prevent="addTask">
      <input v-model="newTask" placeholder="Add a new task">
      <button type="submit">Add</button>
    </form>

    <ul>
      <li v-for="(item, index) in task" :key="index">
        {{ item.text }}
        <button @click="removeTask(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<style>

input {
  padding: 5px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 10px;
}
button {
  padding: 5px 30px;
  font-size: 16px;
  background-color: #0066cc;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin: 0px 0px 0px 30px;
}

ul {
list-style: none;
margin: 0px;
padding: 0px;
}

button:hover {
  background-color: #0052a3;
}

ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

li {
  padding: 10px;
  border-bottom: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li:last-child {
  border-bottom: none;
}

li button {
  background-color: #d83f15;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

li button:hover {
  background-color: #a30000;
}
</style>
