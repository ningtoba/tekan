<template>
    <div class="w-2/3 h-screen mx-auto flex-col">
      <Header class="h-1/4 max-h-52 pt-10"></Header>
      <Word class="h-96 mt-32"></Word>
    </div>
</template>

<script>
import Header from './components/Header'
import Word from './components/Word'

export default {
  name: 'App',
  components: {
    Header,
    Word
  }
}
</script>

<style>
#app {
  font-family: 'Be Vietnam', Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
}
</style>
