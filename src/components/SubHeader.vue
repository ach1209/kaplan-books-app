<template>
  <div class="subHeader__container md-layout md-alignment-space-between">
    <div class="subHeader__title md-layout-item md-medium-size-50 md-xsmall-size-50 md-size-50">
      <h2>Kaplan Books</h2>
    </div>
    <div class="subHeader__button md-layout-item md-medium-size-50 md-xsmall-size-50 md-size-50">
      <md-button class="md-raised md-primary">Add New Books</md-button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SubHeader'
}
</script>

<style scoped>

.subHeader__container {
  max-width: 1000px;  
  margin: 20px auto;
}

.md-button.md-raised.md-primary.md-theme-default {
  color: #fff;
  background-color: #004bb7;
}

</style>
