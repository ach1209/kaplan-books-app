<template>
  <div class="books__container">
    <div class="card" v-for="book in books" v-bind:key="book.id">
      <h3 class="card__header">{{ book.volumeInfo.title }}</h3>
      <div class="card__content">
        <p class="card__content--topMargin">Published by: {{ book.volumeInfo.publisher}}</p>
        <p class="card__content--topMargin" v-html="book.searchInfo.textSnippet"></p>
      </div>
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

<style lang="scss">

.books__container {
  margin: 0 auto;
  display: grid;
  grid-gap: 2rem;
  grid-template-columns: 1fr;

  @include device-med {
    grid-template-columns: repeat(2, 1fr);
  }

  @include device-lg {
    width: 100rem;
  }
}

.card {
  background-color: $bgColor;
  padding: 1.5rem;
  height: auto;
  border-radius: 2px;
  border-left: 4px solid #ffa839;
  box-shadow: 2px 2px 3px rgba(0, 0, 0, 0.2);

  &__header {
    font-size: 1.5rem;
    font-weight: 700;
    color: $fontColor;
  }

  &__content {
    font-size: 1.4rem;
    line-height: 2rem;
    letter-spacing: 0.03rem;
    color: $fontColor;

    &--topMargin {
      margin-top: 1.5rem;
    }
  }
}

</style>