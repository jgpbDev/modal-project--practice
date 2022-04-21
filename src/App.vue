<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  
  <div v-if="showModal">
    <Modal :header="header" :text="text" theme="sale" @close="toggleModal">
      <!-- Also we can pass named slots -->
      <template v-slot:links>
        <a href="#">Sign up now</a>
        <a href="#">More info</a>
      </template>
      <!-- This is the slot to render on the component -->
      <h1>Este es el contenido del slot</h1>
      <p>Este contenido lo pasamos al componente escribiendolo desde donde mandamos llamar el componente</p>
    </Modal>
  </div>
  <div v-if="showModal2">
    <Modal @close="toggleModalTwo">
      <template v-slot:mySlot>
        <a href="#">This is my button</a>
      </template>
      <h1>Este modal fue creado por mí</h1>
    </Modal>
  </div>
  
  <!-- Event modifiers: could be '@click.right' or '@click.alt' for example -->
  <button @click.alt="toggleModal">Open modal (alt)</button>
  <button @click="toggleModalTwo">Open the second modal</button>
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
      text: 'This is the text that I am using for testing Vue 3',
      showModal: false,
      showModal2: false
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active')
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal =  !this.showModal;
    },
    toggleModalTwo() {
      this.showModal2 =  !this.showModal2;
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
