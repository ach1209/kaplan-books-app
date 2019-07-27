<template>
  <div class="searchField">
    <i class="material-icons searchField__icon">search</i>
    <div class="searchField__formGroup">
      <input class="searchField__input" type="text">  
      <label for="name" class="searchField__label">Search for books</label>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SearchField'
}
</script>

<style lang="scss">

.searchField {
  margin-top: 3rem;
  border-bottom: 1px solid #c3c3c3;
  display: flex;
  align-items: center;
  grid-column: 1 / span 2;

  @include device-lg {
    grid-column: 1 / 2;
  }

  &__icon {
    color: $fontColor;
    align-self: flex-end;
  }

  &__formGroup {
    width: 100%;
    position: relative;
  }

  &__input {
    margin-left: 1rem;
    border: none;
    background: none;
    width: 100%;
    height: 3rem;

    &:focus {
      outline: none;
    }
  }
  
  &__label {
    margin-left: 1rem;
    font-size: 1.5rem;
    transition: all 0.3s ease-in-out;
    position: absolute;
    opacity: 0;
    visibility: hidden;
  }

  &__input:focus ~ &__label {
    transform: translateY(-4.5rem);
    opacity: 1;
    visibility: visible;
    color: $fontColor;
  }
}

</style>