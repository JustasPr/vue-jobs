<script>
export default {
  data() {
    return {
      name: 'Justas',
      status: 'pending'
    };
  },
  methods: {
    toggleStatus() {
      if(this.status === 'active') {
        this.status = 'pending';
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
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'inactive'">User is inactive</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <button @click="toggleStatus">Change status</button>
</template>
<style scoped>
h1 {
  color: red;
}
</style>