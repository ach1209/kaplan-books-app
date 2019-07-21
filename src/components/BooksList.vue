<template>
  <div class="books__container md-layout md-alignment-center">
    <div class="md-layout-item md-medium-size-50 md-small-size-50 md-xsmall-size-100 md-size-50" v-for="book in books" v-bind:key="book.id">
      <md-card>
        <md-card-header>
          <span>{{ book.volumeInfo.title }}</span>
        </md-card-header>
        <md-card-content>
          <p>Published by: {{ book.volumeInfo.publisher}}</p>
          <p v-html="book.searchInfo.textSnippet"></p>
        </md-card-content>
      </md-card>
    </div>  
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

<style lang="scss" scoped>

.books__container {
  max-width: 1000px;
  margin: 0 auto;
}

.md-card {
  background-color: #ffffff;
  border-left: 4px solid #ffa839;
  margin-bottom: 30px;
  height: auto;

  @include device-xs {
    height: 200px;
  }

  @include device-s {
    height: 200px;
    margin-right: 20px;
  }
}

.md-card-header span {
  font-weight: 700;
}

</style>