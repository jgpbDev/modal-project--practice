<template>
  <div class="backdrop">
    <!--
      This class with v-bind is a dynamic class, the prop
      name is the class and its value is if it is going to be
      applied or not 

      This could be useful if we want to apply themes or custom
      options in our app
    -->
    <div class="modal" :class="{ sale: theme === 'sale'}">
      <h1>{{ header }}</h1>
      <p>{{ text }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ['header', 'text', 'theme'],
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

  .modal.sale {
    background: crimson;
    color: white;
  }
  .modal.sale h1 {
    color: white;
  }
</style>