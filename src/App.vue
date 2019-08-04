<template>
  <div id="app">
    <AppHeader></AppHeader>
    <SubHeader></SubHeader>
    <BooksList v-bind:books="books"></BooksList>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import SubHeader from './components/SubHeader.vue'
import BooksList from './components/BooksList.vue'

import axios from 'axios'

export default {
  name: 'app',
  components: {
    AppHeader,
    SubHeader,
    BooksList
  },
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

<style lang="scss">

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-size: 62.5%;  
}

body {
  font-family: 'Roboto', sans-serif;
  font-size: 1.6rem;
}

#app {
  background-color: $appBgColor;
  padding-bottom: 2rem;
  height: 100vh;
  overflow: auto;
}
</style>
