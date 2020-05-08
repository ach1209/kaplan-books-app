<template>
  <div class="books__container">
    <div class="searchField">
      <i class="material-icons searchField__icon">search</i>
      <div class="searchField__formGroup">
        <input class="searchField__input" type="text" v-model="search">  
        <label for="name" class="searchField__label">Search for books</label>
      </div>
    </div>
    <div class="book-card" v-for="book in searchBooks" :key="book.id">
      <h3 class="book-card__header">{{ book.volumeInfo.title }}</h3>
      <div class="book-card__content book-card--flex-1">
        <p class="book-card--mgT" v-if="book.volumeInfo.publisher"><strong>Publisher:</strong> {{ book.volumeInfo.publisher}}</p>
        <p class="book-card--mgT" v-else><strong>Publisher:</strong> N/A</p>
        <p class="book-card--mgT book-card--flex-1" v-html="book.searchInfo.textSnippet"></p>
        <span class="book-card__btn book-card__btn--enabled book-card--mgT" v-if="book.saleInfo.saleability === 'FOR_SALE'">
          <a :href="book.saleInfo.buyLink">Available</a>
        </span>
        <span class="book-card__btn book-card__btn--disabled book-card--mgT" v-else>Not Available</span>
      </div>
    </div>  
  </div>
</template>

<script>
export default {
  name: 'BooksList',
  data() {
    return {
      search: ''
    }
  },
  props: {
    books: Array
  },
  computed: {
    searchBooks() {
      return this.books.filter(book => book.volumeInfo.title.match(this.search));
    }
  }
}
</script>

<style lang="scss" scoped>

.books__container {
  display: grid;
  grid-gap: 2rem;
  grid-template-columns: 1fr;  
  margin: 0 auto 2rem;
  padding: 0 3rem;

  @include device-med {
    grid-template-columns: repeat(2, 1fr);
  }

  @include device-lg {
    width: 100rem;
  }
}

.book-card {
  display: flex;
  flex-direction: column;
  height: auto;  
  padding: 1.5rem;  
  background-color: $bgColor;
  border-radius: 2px;
  border-left: 4px solid #ffa839;
  box-shadow: 2px 2px 3px rgba(0, 0, 0, 0.2);

  &__header {
    color: $fontColor;    
    font-size: 1.5rem;
    font-weight: 700;
  }

  &__content {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    color: $fontColor;
    font-size: 1.4rem;
    line-height: 2rem;
    letter-spacing: 0.03rem;
  }

  &--mgT {
    margin-top: 1.5rem;
  }

  &--flex-1 {
    flex: 1;
  }

  &__btn {
    align-self: end;
    width: 11rem;
    padding: 0.75rem;
    font-size: 1.2rem;     
    text-align: center;
    text-transform: uppercase;
    border-radius: 2px;
    cursor: pointer;
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
      }
    }

    &--disabled {
      background-color: $bgColor2;
    }
  }
}

.searchField {
  @include flex-center;
  width: 100%;
  margin: 0 auto 2rem;

  @include device-med {
    grid-column: 1 / span 2;
  }

  &__icon {
    align-self: flex-end;
    color: $fontColor;
  }

  &__formGroup {
    display: grid;
    grid-template-rows: 1fr;
    position: relative;
    width: 100%;
    border-bottom: 1px solid #c3c3c3;    
    
    @include device-lg {
      width: 46.5%;
    }
  }

  &__input {
    height: 3rem;
    margin-left: 1rem;
    border: none;
    background: none;

    &:focus {
      outline: none;
    }
  }
  
  &__label {
    position: absolute;
    left: 0;
    opacity: 0;
    margin-left: 1rem;
    font-size: 1.5rem;
    visibility: hidden;
    transition: all 0.3s ease-in-out;
  }

  &__input:focus ~ &__label {
    color: $fontColor;
    transform: translateY(-2rem);
    opacity: 1;
    visibility: visible;
  }
}
</style>