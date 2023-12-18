<script setup>
import NavBar from './components/NavBar.vue';
import Spider from './components/Spider.vue';
import List from './components/List.vue';
import AddAndDel from './components/AddAndDel.vue';
import ShoppingCart from './components/ShoppingCart.vue';
</script>

<template>
  <NavBar />
  <p>{{ msg }}</p>
  <p v-html="my_site"></p>
  <List />
  <Spider />
  <AddAndDel />
  <ShoppingCart />
</template>

<style lang="scss">
#app {
  height: 100%;
  width: 100%;

}
// .background-image {
//   background-image: url('./assets/img/orange.png');
//   background-repeat: no-repeat;
//   background-size: cover;
//   background-position: center;
//   position: fixed;
// }
</style>

<script>
export default {
  data() {
    return {
      msg: 'Hello World!',
      my_site: '<a href="https://mc8.me">mc8.me</a>'
    }
  },
  methods: {
  }
}
</script>
