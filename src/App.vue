<script setup>
import navbar from './components/navbar.vue';
import spider from './components/spider.vue';
import list from './components/list.vue';
import add_del from './components/add_del.vue';
import shopping_cart from './components/shopping_cart.vue';
</script>

<template>
  <navbar />
  <p>{{ msg }}</p>
  <p v-html="my_site"></p>
  <list />
  <spider />
  <add_del />
  <shopping_cart />
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
