<template>
    <div>
      <h1>Group List</h1>
      <ul>
        <li v-for="group in groups" :key="group.id">{{ group.name }}</li>
      </ul>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        groups: [],
      };
    },
    methods: {
      async fetchGroups() {
        try {
          const response = await axios.get('http://localhost:3000/api/groups');
          this.groups = response.data;
        } catch (error) {
          console.error('Error fetching groups:', error);
        }
      },
    },
    mounted() {
      this.fetchGroups();
    },
  };
  </script>