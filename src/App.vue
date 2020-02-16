<template>
<div>
  <div class="navbar">
  </div>

  <div id="app">
    <Product :premium="premium"></Product>
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</div>
</template>

<script>
import Product from './components/Product.vue'
import './styles.css'
export default {
  name: 'App',
  components: {
    Product
  },
  data() {
    return {
      premium: true
    }
  }
  

}
</script>

