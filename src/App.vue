<template>
  <div id="app" class="corainer">
    <img class="logo" alt="Vue logo" src="./assets/logo.png">
		<todo></todo>
  </div>
</template>

<script>
import Todo from './components/Todo.vue'
export default {
  name: 'App',
  components: {
    Todo
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
	font-size: 24px;
}
.corainer{
	max-width: 600px;
	margin: 0 auto;
}
.logo{
	display: block;
	margin: 20px auto;
	height: 75px;
}
</style>
