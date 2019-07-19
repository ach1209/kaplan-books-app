<template>
  <div id="app">
    <AppHeader />
    <md-content>
      <BooksList />
    </md-content>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import BooksList from './components/BooksList.vue'

export default {
  name: 'app',
  components: {
    AppHeader,
    BooksList
  }
}
</script>

<style>
#app {
  background-color: #f3f5fb;
}

.md-content {
  width: 1000px;
  margin: 60px auto 0;
}
</style>
