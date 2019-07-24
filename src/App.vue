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

<style lang="scss">

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-size: 62.5%;  
}

body {
  font-family: 'Roboto', sans-serif;
  font-size: 1.6rem;
}

#app {
  background-color: $appBgColor;
  padding-bottom: 2rem;
}
</style>
