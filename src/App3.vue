<script setup>
import { ref, onMounted } from 'vue';

    const name = ref("John Doe");
    const status = ref('active');
    const tasks = ref(["Task One", "Task Two", "Task Three", "Task Four", "Task Five"]);
    const newTask = ref();

    const toggleStatus = () => {
      if (status.value === 'active') {
        status.value = 'pending';
      } else if (status.value === 'pending') {
        status.value = 'inactive';
      } else {
        status.value = 'active';
      }
    };

    const addTask = () => {
      if(newTask.value.trim() !== ''){
        tasks.value.push(newTask.value);
        newTask.value = '';
      }
    };

    const deleteTask = (index) => {
      tasks.value.splice(index, 1);
    };

    onMounted(async () => {
      try {
        const res = await fetch('https://jsonplaceholder.typicode.com/todos');
        const data = await res.json();
        tasks.value = data.map(task => task.title);
      } catch (error) {
        console.log("Error fetching tasks");
        
      }
    })

    // return {
    //   name,
    //   status,
    //   tasks,
    //   toggleStatus,
    // };
</script>
<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is Active</p>
  <p v-else-if="status === 'pending'">User is Pending</p>
  <p v-else>User is Inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" v-model="newTask">
    <button type="submit">Submit</button>
  </form>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="index">
      <span>
        {{ task }}
        <button @click="deleteTask">Delete</button>
      </span>
    </li>
  </ul>
  <!-- v-bind -->
   <!-- <a v-bind:href="link" target="_blank">Click Me</a> -->
   <hr>

   <!-- <button v-on:click="toggleStatus">Change Status</button> -->

   <!-- In development this one is emphasized more due to clean syntax -->
   <button @click="toggleStatus">Change Status</button> 
</template>
