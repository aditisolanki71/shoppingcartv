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
            <!-- <img src="./images/img1.jpg"> -->
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

            <ul>
              <span>Available Colors: </span>
                <li v-for="variant in variants" :key="variant.variantId">
                  {{variant.variantColor}}
                </li>
            </ul>

            <ul>
              <span>Available Sizes: </span>
                <li style="display:inline;" v-for="size in sizes" :key="size">
                  <span style="padding:5px">{{size}}</span>
                </li>
            </ul>

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
              {variantId:1,variantColor:"green"},
              {variantId:2,variantColor:"red"}],
    sizes: ['xs','x','s','m','l','xl']
    }
  }

}
</script>

