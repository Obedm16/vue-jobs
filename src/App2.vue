<script>
export default {
  data() {
    return {
      name: 'John Doe',
      status: false,
      tasks: ["Task 1", "Task 2", "Task 3", "Task 4", "Task 5"],
      link: 'https://google.com',
    }
  },
  methods : {
    toggleStatus() {
      if (this.status === 'active') {
        this.status === 'pending';
      } else if (this.status === 'pending') {
        this.status = 'inactive';
      } else {
        this.status = 'active';
      }
    }
  }
}
</script>
<template>
  <h1>{{ name }}</h1>
  <p v-if="status">User is Active</p>
  <p v-else-if="status">User is Pending</p>
  <p v-else>User is Inactive</p>
  <h3>Tasks:</h3>
  <ul>
    <li v-for="task, index in tasks" :key=index>{{ task }}</li>
  </ul>
  <!-- v-bind -->
   <a v-bind:href="link" target="_blank">Click Me</a>
   <hr>

   <!-- <button v-on:click="toggleStatus">Change Status</button> -->
   <button @click="toggleStatus">Change Status</button> //In development this one is emphasized more due to clean syntax
</template>
