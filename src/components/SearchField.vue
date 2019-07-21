<template>
  <div class="searchField__container md-layout">
    <md-field class="md-layout-item md-size-50">
      <label>Placeholder</label>
      <md-input></md-input>
    </md-field>
  </div>

</template>

<script>
export default {
  name: 'SearchField'
}
</script>

<style lang="scss" scoped>

.searchField__container {
  width: 1000px;
  margin: 0 auto;

  .md-field {

    .md-input {
      border-bottom: 1px solid;
    }
  }
}

</style>