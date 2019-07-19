<template>
  <div class="md-layout">
    <md-card v-for="book in books" v-bind:key="book.id">
      <md-card-header>
        <span>{{ book.volumeInfo.title }}</span>
      </md-card-header>
      <md-card-content>
        <p>Published by: {{ book.volumeInfo.publisher}}</p>
        <p v-html="book.searchInfo.textSnippet"></p>
      </md-card-content>
    </md-card>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'BooksList',
  data() {
    return {
      books: []
    }
  },
  created() {
    const url = 'https://www.googleapis.com/books/v1/volumes?q=kaplan%20test%20prep'
    axios.get(url).then(response => {
      this.books = response.data.items;
    })
  }
}
</script>

<style scoped>

.md-layout {
  justify-content: center;
}

.md-card {
  background-color: #ffffff;
  border-left: 4px solid #ffa839;
  margin-right: 30px;
  margin-bottom: 30px;
  width: 450px;
  height: 200px;
}

.md-card-header span {
  font-weight: 700;
}

</style>