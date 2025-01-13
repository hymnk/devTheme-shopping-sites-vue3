<template>
    <header class="header">
      <div class="header-top">
        <p>Header Area.</p>
      </div>
    </header>
  </template>
  
  <script>
  export default {
    name: 'SiteHeader'
  }
  </script>
  
  <style scoped>
  .header {
    background-color: #eee;
  }
  
  .header-top {
    text-align: center;
    padding: 1em 0;
    border-bottom: 3px solid #333;
  }
  
  .header-top p {
    color: #666;
    font-size: 120%;
  }
  </style>
  