<template>
    <div>
        <h1>{{ product }}</h1>
        <p v-if="inventory > 10">In Stock</p>
        <p v-else-if="inventory < 10 && inventory > 0 ">Almost Sold Out</p>
        <p v-else :class="[inventory == 0 ? textdecoration : '']">Out of Stock </p>
        <p v-show="inventory > 0">ON Sale</p>
        <!-- <p v-if="premium">User is Premium: {{premium}}</p> -->
        <p>Shipping : {{shipping}}</p>
        <ul>
            <li :key="index" v-for="(item,index) in details">{{item}}</li>
        </ul>
            <span>Available Colors: </span>
              <br/>
                <div 
                  class="colorbox" 
                  :style="{backgroundColor: variant.variantColor}" 
                  v-for="variant in variants" 
                  :key="variant.variantId"
                  @mouseover="updateProduct(variant.variantImage)">
                </div>
        <ul>
        <span>Available Sizes: </span>
            <li style="display:inline;" v-for="size in sizes" :key="size">
                <span style="padding:5px">{{size}}</span>
            </li>
        </ul>
        <div>
            <button :disabled="inventory <= 0" v-on:click="addToCart">Add to cart</button>             
        </div>
    </div>
</template>
<script>
export default {
    name: 'ProductData',
    props: {
        premium: {
            type: Boolean,
            required:true
        }
    },
    data() {
        return {
                product: 'Dress',
                inventory: 20,
                //onSale: true,
                textdecoration: 'line',
                details: ["80% cotton","20% polyester","gender-neutral"],
                variants: [
                    {
                        variantId:4,
                        variantColor:"pink",
                        variantImage:"/img/img4.a4032e38.jpg"
                    },
                    {
                        variantId:6,
                        variantColor:"white",
                        variantImage:"/img/img6.f519008f.jpg"
                    },
                    { 
                        variantId:13,
                        variantColor:"blue",
                        variantImage:"/img/img13.bbd56ccc.jpg"
                    },
                    {
                        variantId:20,
                        variantColor:"gray",
                        variantImage:"/img/img20.1d566e03.jpg"
                    }
                ],
                sizes: ['xs','x','s','m','l','xl'],
        }
    },
    methods: {
           addToCart() {
                this.$emit('add-to-cart');
            },
            updateProduct(variantImage) {
                this.image = variantImage
            },
            shipping() {
                if(this.premium) {
                    return 'Free!!'
                }
                return '$2.99'
            }
        }
}
</script>