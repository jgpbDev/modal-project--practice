<template>
<!--  
  The event modifier makes the click to be specifically on 
  the visible part of this element 
-->
  <div class="backdrop" @click.self="closeModal">
    <!--
      This class with v-bind is a dynamic class, the prop
      name is the class and its value is if it is going to be
      applied or not 

      This could be useful if we want to apply themes or custom
      options in our app
    -->
    <div class="modal" :class="{ sale: theme === 'sale'}">
      <!-- The 'Default content' will show if we remove the slot in the component call -->
      <slot>Default content</slot>
      <div class="actions">
        <!-- We are calling the named slot -->
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['header', 'text', 'theme'],
  methods: {
    //Here we're going to use what is called: CUSTOM EVENTS
    closeModal() {
      this.$emit('close');
    }
  }
}
</script>

<style scoped>
  .modal {
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
  }
  .backdrop {
    top: 0;
    position: fixed;
    background: rgba(0, 0, 0, 0.5);
    width: 100%;
    height: 100%;
  }
  h1 {
    color: aqua;
    border: none;
    padding: 0;
  }
  .modal p {
    font-style: normal;
  }
  .modal .actions {
    text-align: center;
    margin: 30px 0 10px 0;
  }
  .modal .actions a {
    color: #333;
    padding: 8px;
    border: 1px solid #eee;
    border-radius: 4px;
    text-decoration: none;
    margin: 10px;
  }
  .modal.sale {
    background: crimson;
    color: white;
  }
  .modal.sale h1 {
    color: white;
  }
  .modal.sale .actions {
    color: white;
  }
  .modal.sale .actions a {
    color: white;
  }
</style>