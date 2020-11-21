<template>
  <div id="app">
    <Header />
    <div class="container">
    <TransactionsList />
    </div>
  </div>
</template>

<script>
import TransactionsList from './components/TransactionsList'
import Header from './components/Header'

export default {
  name: 'App',
  components: {
    TransactionsList,
    Header
  }
}
</script>

<style>
html {
  background: #ebebeb;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #232323;
  margin-top: 10px;
}
.container{
  display: grid;
  place-items: center;
}
</style>
