<template>
    <div>
        <form class="review-form" @submit.prevent="onSubmit">
            <p v-if="errors.length">
                <b>Please Correct the Following Error:</b>
                <ul>
                    <li v-for="(error,index) in errors" :key="index">
                        {{error}}
                    </li>
                </ul>
            </p>
            <p>
                <label for="name">Name: </label>
                <input id="name" v-model="name"/>
            </p>

            <p>
                <label for="review">Review: </label>
                <textarea id="review" v-model="review"></textarea>
            </p>

            <p>
                <label for="rating">Rating: </label>
                <select id="rating" v-model.number="rating">
                    <option>5</option>
                    <option>4</option>
                    <option>3</option>
                    <option>2</option>
                    <option>1</option>
                </select>
            </p>

            <p>
                <input type="submit" value="submit">
            </p>
        </form>
    </div>
</template>
<script>
export default {
    name: 'ProductReview',
    data() {
        return {
            name: null,
            review: null,
            rating: null,
            errors: []
        }
    },
    methods: {
        onSubmit() {
            if(this.name && this.review && this.rating) {
                let productReview ={
                name: this.name,
                review: this.review,
                rating: this.rating
            }
            this.$emit('review-sumitted',productReview)
            alert("Reviews Added Successfullty....")
            }
            else {
                if(!this.name) {
                    this.errors.push("Name is Required")
                }
                 if(!this.rating) {
                    this.errors.push("Rating is Required")
                }
                 if(!this.Review) {
                    this.errors.push("Review is Required")
                }
            }
            this.name = null
            this.review = null
            this.rating = null
        }
    }
}
</script>
