<template>
  <div id="app">
    <AppHeader />
    <SubHeader />
    <BooksList />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import SubHeader from './components/SubHeader.vue'
import BooksList from './components/BooksList.vue'

export default {
  name: 'app',
  components: {
    AppHeader,
    SubHeader,
    BooksList
  }
}
</script>

<style>
#app {
  background-color: #f3f5fb;
}
</style>
