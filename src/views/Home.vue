<template>
    <div class="wrapper">
        <section class="featured-section">
            <h2>Featured Items</h2>
            <ul class="featured-items">
                <li v-for="product in featuredProducts" :key="product.id" class="item">
                    <router-link :to="{ name: 'product', params: { id: product.id}}">
                        <img class="product-image" :src="makeImagePath(product)" alt="">
                        <p class="product-title">{{ product.name }}</p>
                        <p><em>${{ product.price }}</em></p>
                    </router-link>
                </li>
            </ul>
        </section>
    </div>
</template>

<script>
import { imagePath } from '@/mixins/image-path.js'

export default {
    name: 'home',
    mixins: [imagePath],
    computed: {
        featuredProducts: function() {
            return this.$store.getters.featuredProducts.slice(0,3)
        }
    }
};
</script>

<style lang="less">
.featured-section {
    max-width: 800px;
    margin: 0 auto;

    @media only screen and (max-width: 832px) {
        text-align: center;
        max-width: 100%;
        padding: 1rem;
    }
}

.featured-items {
    justify-content: space-between;
    list-style: none;
    padding-left: 0;
    display: flex;

    @media only screen and (max-width: 832px) {
        flex-direction: column;
    }
}

.item {
    width: 33%;
    text-align: center;

    @media only screen and (max-width: 832px) {
        width: 100%;
    }
}

.product-image {
    max-height: 200px;
}

.product-title {
    font-weight: bold;
}
</style>