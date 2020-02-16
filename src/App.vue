<template>
<div>
  <div class="navbar">
  </div>

  <div id="app">
    <div class="cart">
      Cart: {{cart}}
      <!-- <button v-on:click="increaseProduct" style="pdding:5px;margin:5px">+</button> -->
      <button v-on:click="decreaseProduct" style="pdding:5px;margin:5px">-</button>
    </div>
    <Product :premium="premium" @add-to-cart="updateCart"></Product>
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
      premium: true,
        cart:0
    }
  },
  methods: {
     increaseProduct() {
      this.cart +=1
    },
    decreaseProduct() {
      if(this.cart > 0) {
      this.cart -=1
      }
    },
    updateCart() {
      this.cart += 1
    }
  }
  

}
</script>

