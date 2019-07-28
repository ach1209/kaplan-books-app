<template>
  <div class="books__container">
    <div class="card" v-for="book in books" v-bind:key="book.id">
      <h3 class="card__header">{{ book.volumeInfo.title }}</h3>
      <div class="card__content">
        <p class="u-top-margin"><strong>Publisher:</strong> {{ book.volumeInfo.publisher}}</p>
        <p class="u-top-margin" v-html="book.searchInfo.textSnippet"></p>
        <span class="card-btn card-btn--enabled u-top-margin" v-if="book.saleInfo.saleability === 'FOR_SALE'">
          <a v-bind:href="book.saleInfo.buyLink">Buy - ${{book.saleInfo.retailPrice.amount}}</a>
        </span>
        <span class="card-btn card-btn--disabled u-top-margin" v-else>Not Available</span>
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
    display: grid;
    font-size: 1.4rem;
    line-height: 2rem;
    letter-spacing: 0.03rem;
    color: $fontColor;

    @include device-med {
      grid-template-rows: 4rem 10rem 1fr;
    }
  }

  .u-top-margin {
    margin-top: 1.5rem;
  }

  &-btn {
    font-size: 1.2rem;     
    width: 11rem;
    padding: 0.75rem;
    border-radius: 2px;
    justify-self: flex-end;
    align-self: center;
    text-align: center;
    text-transform: uppercase;
    transition: all 0.2s ease-in-out;

    &--enabled {
      background-color: $btnBgColor;
      box-shadow: 0 2px 3px rgba(0, 0, 0, 0.2);

      a {
        color: $fontColor2;      
        text-decoration: none;
      }

      &:hover,
      &:focus {
        background-color: rgba($btnBgColor, 0.75);
        cursor: pointer;
      }
    }

    &--disabled {
      background-color: $bgColor2;
    }
  }
}

</style>