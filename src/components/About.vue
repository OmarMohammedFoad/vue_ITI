<template>
    <div class="p-10 max-w-3xl mx-auto text-center">
      <h1 class="text-4xl font-bold mb-4">About This App</h1>
      <p class="text-lg text-gray-700">
        This is a simple Vue.js CRUD application that allows you to manage student records.
      </p>
      <p class="mt-4 text-gray-600">
        It's built using Vue 3 and fetch API for HTTP requests. This project demonstrates basic create, read, update, and delete functionality using a fake REST API powered by <code>json-server</code>.
      </p>
      <div class="mt-6">
        <router-link to="/" class="text-blue-600 underline">Back to Home</router-link>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'AboutPage'
  }
  </script>
  
  <style scoped>
  /* Optional: you can leave this empty or add custom styles */
  </style>
  