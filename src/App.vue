<template>
  <h1>{{ title }}</h1>
  <Modal :header="header" :text="text" theme="sale"/>
</template>

<script>
import Modal from "./components/Modal.vue"

export default {
  //It is optional to name our components
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'This is my title in the data',
      header: 'Sign up to this new app',
      text: 'This is the text that I am using for testing Vue 3'
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus();
    }
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
}
h1 {
  border-bottom: 1px solid #dddddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
