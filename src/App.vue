<template>
  <div id="app" class="container">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Header mainTitle="Notas"/>
    <Form/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Form from './components/Form.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld
    Form,
    Header
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 20px;
  max-width: 600px;
}
</style>
