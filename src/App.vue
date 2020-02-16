<template>
<div>
  <div class="navbar">
  </div>

  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <div class="product">
      <div class="row">
        <div class="column left">
            <img :title="image" v-bind:src="image" />
            <!-- <img src="./images/img6.jpg"> -->
        </div>
        <div class="column right">
          <div class="product-info">
            <h1>{{ product }}</h1>
            <p v-if="inventory > 10">In Stock</p>
            <p v-else-if="inventory < 10 && inventory > 0 ">Almost Sold Out</p>
            <p v-else>Out of Stock </p>
            <p v-show="onSale">ON Sale</p>

            <ul>
             <li :key="item" v-for="item in details">{{item}}</li>
            </ul>

              <span>Available Colors: </span>
              <br/>
                <div style="display:block" v-for="variant in variants" :key="variant.variantId">
                  <span @mouseover="updateProduct(variant.variantImage)">{{variant.variantColor}}</span>
                </div>
        
            <ul>
              <span>Available Sizes: </span>
                <li style="display:inline;" v-for="size in sizes" :key="size">
                  <span style="padding:5px">{{size}}</span>
                </li>
            </ul>

            <div>
              <button v-on:click="addToCart">Add to cart</button>
              <div class="cart">
                Cart: {{cart}}
                <button v-on:click="increaseProduct" style="pdding:5px;margin:5px">+</button>
                <button v-on:click="decreaseProduct" style="pdding:5px;margin:5px">-</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import './styles.css'
export default {
  name: 'App',
  // components: {
  //   HelloWorld
  // },
  data() {
    return {
      product: 'Dress',
      image: '/img/img1.bb990836.jpg',
      inventory: 0,
      onSale: true,
      details: ["80% cotton","20% polyester","gender-neutral"],
      variants: [
              {variantId:4,
                variantColor:"pink",
                variantImage:"/img/img4.a4032e38.jpg"
              },
              {variantId:6,
                variantColor:"white",
                variantImage:"/img/img6.f519008f.jpg"
              }
            ],
    sizes: ['xs','x','s','m','l','xl'],
    cart:0
    }
  },
  methods: {
    addToCart() {
      alert("Added into cart")
    },
    updateProduct(variantImage) {
      this.image = variantImage
    },
    increaseProduct() {
      this.cart +=1
    },
    decreaseProduct() {
      if(this.cart > 0) {
      this.cart -=1
      }
    }
  }

}
</script>

