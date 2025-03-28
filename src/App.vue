<template>
  <div id="app">
    <h1>Book List</h1>
    <ul>
      <li v-for="book in books" :key="book.id">{{ book.title }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      books: []
    }
  },
  created() {
    // Fetch the books data from your API
    fetch('fetch('https://clean-api-k8hl.onrender.com/books')  // Keep this URL as is
')
      .then(response => response.json())
      .then(data => {
        this.books = data;
      })
      .catch(error => {
        console.error('Error fetching data:', error);
      });
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
