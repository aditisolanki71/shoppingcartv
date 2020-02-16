<template>
    <div>
        <form class="review-form" @submit.prevent="onSubmit">
            <p>
                <label for="name">Name: </label>
                <input id="name" v-model="name"/>
            </p>

            <p>
                <label for="review">Review: </label>
                <textarea id="review" v-model="review" required></textarea>
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
            rating: null
        }
    },
    methods: {
        onSubmit() {
            let productReview ={
                name: this.name,
                review: this.review,
                rating: this.rating
            }
            this.$emit('review-sumitted',productReview)
            this.name = null
            this.review = null
            this.rating = null
        }
    }
}
</script>
