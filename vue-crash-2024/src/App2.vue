<script>
  export default {
    
  }
</script>

<template>
  <h3>Pengkondisian:</h3>
  <p v-if="status === 'Active'">User is Active</p>
  <p v-else-if="status === 'Pending'">User is Pending</p>
  <p v-else>User is Inactive</p>

  <button @click="toggleStatus">Change Status</button>

  <h3>Task (Perulangan):</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>

  <a :href="link">Click for Google</a>
</template>