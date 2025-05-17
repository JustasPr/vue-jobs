<script setup>
import { ref } from 'vue';
    const name = 'Justas';
    const status = ref('active');
    const tasks  = ref(['Task One', 'Task Two', 'Task Three']);
    const newTask = ref('');

    const toggleStatus = () => {
      if(status.value === 'active') {
        status.value = 'pending';
      } else if (status.value === 'pending') {
        status.value = 'inactive';
      } else {
        status.value = 'active';
      }
    };
    const addTask = () => {
      if(newTask.value.trim() !== '') {
        console.log(newTask.value)
        tasks.value.push(newTask.value);
        newTask.value = '';
      };
    };
    const deleteTask = (index) => {
      tasks.value.splice(index, 1);
    };
</script>

<template> 
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'inactive'">User is inactive</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <button @click="toggleStatus">Change status</button>
  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>
  <ul>
    <li v-for="(task, index) in tasks" :key="task"> 
        {{ task }}
    </li>
    <button @click="deleteTask(index)">x</button>
  </ul>
</template>
<style scoped>
h1 {
  color: red;
}
</style>