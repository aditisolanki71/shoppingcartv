<template>
<div>
  <div class="navbar">
  </div>

  <div id="app">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <div class="product">
      <div class="row">
        <div class="column left">
            <img :title="image" :alt="imagdesc" v-bind:src="image" />
            <!-- <img src="./images/img1.jpg"> -->
        </div>
        <div class="column right">
          {{ product }}
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
      product: 'dress',
      image: '/img/img1.bb990836.jpg'
    }
  }

}
</script>

