<template>
  <div class="subHeader">
    <div class="subHeader__container md-layout md-alignment-space-between">
      <div class="subHeader__title md-layout-item md-size-50">
        <h2>Kaplan Books</h2>
      </div>
      <div class="subHeader__button md-layout-item md-size-50">
        <md-button class="md-raised md-primary">Add New Books</md-button>
      </div>
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

<style lang="scss" scoped>

.subHeader__container {
  max-width: 1000px;  
  margin: 20px auto;
  display: flex;
  justify-content: center;
}

.subHeader__button {
  display: flex;
  justify-content: flex-end;
}

.md-button.md-raised.md-primary.md-theme-default {
  color: #fff;
  background-color: #004bb7;
  margin-right: 0;

  @include device-s {
    margin-right: 20px;
  }
}

</style>
