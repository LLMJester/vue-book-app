<template>
  <div id="app">
    <h1>Book List</h1>
    <ul>
      <!-- Loop through 'books' array and display each book's title -->
      <li v-for="book in books" :key="book.id">{{ book.title }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      books: []  // Holds the fetched book list
    };
  },
  created() {
    // Fetch data from the API when the component is created
    fetch('https://clean-api-k8hl.onrender.com/books') // Ensure this URL is correct
      .then(response => response.json())  // Parse the response as JSON
      .then(data => {
        this.books = data;  // Update the 'books' array with the fetched data
      })
      .catch(error => {
        console.error('Error fetching books:', error);  // Log any errors
      });
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  font-size: 18px;
  margin: 10px;
}
</style>
