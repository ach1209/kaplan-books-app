<template>
  <div class="header">
    <i class="material-icons header__menu">menu</i>
    <span class="header__title">Kaplan Books</span>
  </div>
</template>

<script>
export default {
  name: 'AppHeader'
}
</script>

<style lang="scss">

.header {
  background-color: $bgColor;
  min-height: 6rem;
  padding-right: 2rem;
  padding-left: 2rem;
  display: flex;
  align-items: center;

  &__menu {
    &:hover,
    &:focus {
      cursor: pointer;
    }
  }

  &__title {
    font-size: 2rem;
    letter-spacing: 0.1rem;
    margin-left: 3rem;
  }
}

</style>