<template>
  <div class="subHeader">
    <h2 class="subHeader__title">All Books</h2>
    <div class="subHeader__button">
      <span class="subHeader__buttonText">Add New Books</span>
    </div>
    <SearchField />
  </div>
</template>

<script>
import SearchField from './SearchField'

export default {
  name: 'SubHeader',
  components: {
    SearchField
  }
}
</script>

<style lang="scss">

.subHeader {
  width: auto;
  margin: 3rem auto;
  display: grid;
  grid-template-columns: repeat(2, 1fr);

  @include device-lg {
    width: 100rem;
  }

  &__title {
    color: $fontColor;
    font-size: 2.1rem;
    align-self: center;
    justify-self: center;

    @include device-lg {
      justify-self: left;
    }
  }

  &__button {
    background-color: $btnBgColor;
    padding: 0.85rem;
    border-radius: 2px;
    box-shadow: 0 2px 3px rgba(0, 0, 0, 0.2);
    justify-self: center;
    text-align: center;    

    &:hover,
    &:focus {
      background-color: rgba($btnBgColor, 0.75);
      cursor: pointer;
    }

    @include device-lg {
      justify-self: end;
      margin: 0;
    }
  }

  &__buttonText {
    color: #fff;    
    font-size: 1.5rem;
    text-transform: uppercase;
  }
}

</style>