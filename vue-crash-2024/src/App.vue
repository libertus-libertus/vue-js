<script setup>
  import { ref } from 'vue';

  const name = ref("Libertus Sabebeget");
  const status = ref("Active");
  const tasks = ref(["Task one", "Task Two", "Task Three"]);
  const newTask = ref();

  const toggleStatus = () => {
    if (status.value === "Active") {
      status.value = "Pending"
    } else if (status.value === "Pending") {
      status.value = "Inactive"
    } else {
      status.value = "Active"
    }
  };

  const addTask = () => {
    if (newTask.value.trim() !== "") {
      tasks.value.push(newTask.value)
      newTask.value = ""
    }
  };

  const deleteTask = (index) => {
    tasks.value.splice(index, 1);
  };
</script>

<template>
  <h1>{{ name }}</h1>
  <h3>Pengkondisian:</h3>
  <p v-if="status === 'Active'">User is Active</p>
  <p v-else-if="status === 'Pending'">User is Pending</p>
  <p v-else>User is Inactive</p>
  <button @click="toggleStatus">Change Status</button> <br><br>

  <form @submit.prevent="addTask" >
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" autofocus/>
    <button type="submit">Submit</button>
  </form>

  <h3>Task:</h3>
  <ol>
    <li v-for="(task, index) in tasks" :key="task">
      <span>
        {{ task }}
      </span>
      <button class="btn" @click="deleteTask(index)"> Remove Task</button>
    </li>
  </ol>
</template>

<style scoped>
  .btn {
    background-color: red;
    color: white;
    border: none;
  }
  .btn:hover {
    cursor: pointer;
  }
</style>