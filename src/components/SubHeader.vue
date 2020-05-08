<template>
  <div class="subHeader">
    <h2 class="subHeader__title">All Books</h2>
    <div class="subHeader__button">
      <span class="subHeader__buttonText">Add New Books</span>
    </div>
  </div>
</template>

<script>

export default {
  name: 'SubHeader'
}
</script>

<style lang="scss" scoped>

.subHeader {
  display: grid;
  grid-template-columns: repeat(2, 1fr);  
  width: auto;
  margin: 3rem auto;
  padding: 0 3rem;

  @include device-lg {
    width: 100rem;
  }

  &__title {
    align-self: center;
    justify-self: start;    
    color: $fontColor;
    font-size: 2.1rem;
  }

  &__button {
    @include flex-center;
    justify-self: end;    
    background-color: $btnBgColor;
    padding: 0.85rem;
    border-radius: 2px;
    box-shadow: 0 2px 3px rgba(0, 0, 0, 0.2);
    text-align: center;
    cursor: pointer;    
    transition: all 0.2s ease-in-out;

    &:hover,
    &:focus {
      background-color: rgba($btnBgColor, 0.75);
    }

    @include device-med {
      margin: 0;
    }
  }

  &__buttonText {
    color: $fontColor2;    
    font-size: 1.4rem;
  }
}

</style>