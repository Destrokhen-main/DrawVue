<template>
  <div class = "screen">
    <h1>Входные данные</h1>
    <Board/>
  </div>
</template>

<script>
import Board from './components/Board'

export default {
  name: 'App',
  components: {
    Board
  }
}
</script>

<style>

#img-logo {
  width:150px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.screen {
  align-items: center;
  width: 50%;
  margin:auto;
  padding:1rem 0;
}
</style>
