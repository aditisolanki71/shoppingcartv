<template>
    <div>
      <div class="product">
        <div class="row">
          <div class="column left">
              <img :title="image" v-bind:src="image" />
              <!-- <img src="./images/img20.jpg"> -->
          </div>
          <div class="column right">
            <div class="product-info">
              <ProductData :premium="premium" @add-to-cart="updateToCart"></ProductData>
              <ProductTabs :reviews=reviews></ProductTabs> 
            </div>
          </div>
        </div>
    </div>
    <br/>
    <br/>
  </div>
</template>
<script>
import ProductData from './ProductData'
import ProductTabs from './ProductTabs'
export default {
    name: 'Product',
    components: {ProductTabs,ProductData},
    props: {
        premium: {
            type: Boolean,
            required:true
        }
    },
    data() {
      return {
        welcomeMessage: 'Welcome to',
        image: '/img/img1.bb990836.jpg',
        reviews: []
      }
    },
    methods: {
      updateToCart() {
        this.$emit("update-to-cart")
      }
    },
    computed: {
      title() {
        return this.welcomeMessage + " " + this.title
      },
    
    }
  }
</script>
