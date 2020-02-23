<template>
<div>
    <span 
        :class="{activeTab: selectedTab === tab}" 
        v-for="(tab,index) in tabs" 
        :key="index"
        @click="selectedTab = tab">
        {{tab}}
    </span>
       <div v-show="selectedTab === 'Reviews'"> 
                <p v-if="reviews.length <= 0">There is no reviews yet.</p>
                <ul>
                    <li v-for="(review,index) in reviews" :key="index">
                    <p>Name: {{review.name}}</p>
                    <p>Rating: {{review.rating}} </p>
                    <p>Review: {{review.review}}</p>
                    </li>
                </ul>
        </div>
        <ProductReview 
            v-show = "selectedTab === 'Make a Review'" 
            @review-sumitted="addReview">
        </ProductReview>
            
</div>    
</template>
<script>
import ProductReview from './ProductReview'
export default {
    name:'ProductTabs',
    components : {ProductReview},    
    props: {
        reviews: {
            type: Array,required: true
        }
    },
    data() {
        return {
            tabs: [ 'Reviews', 'Make a Review'],
            selectedTab: 'Reviews',

        }
    },
    methods: {
         addReview(productReview) {
        this.reviews.push(productReview)
    } 
    }
}
</script>
