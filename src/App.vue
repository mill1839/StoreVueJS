<template>
    <div id="app">
        <div class="featured-section flex-col flex-col--align-center" id="nav">
            <h1 class="flex-col--2">My Store</h1>
            <div class="flex-col--2 flex-justify-right flex">
                <router-link to="/" class="nav-items__item">Home</router-link>
                <router-link 
                    :to="{ name: 'gender-overview', params: { gender: 'women'}}" 
                    class="nav-items__item">
                    Women
                </router-link>
                <router-link 
                    :to="{ name: 'gender-overview', params: { gender: 'men'}}" 
                    class="nav-items__item">
                    Men
                </router-link>
                <router-link to="/cart" class="nav-items__item">
                    Cart
                    <counter-badge :count="cartCount"></counter-badge>
                </router-link>
            </div>
        </div>
        <router-view/>
    </div>
</template>

<script>
import CounterBadge from '@/components/CounterBadge';

export default {
    name: 'app',
    components: { CounterBadge },
    computed: {
        cartCount(){
            return this.$store.state.cart.length
        }
    }
}
</script>

<style lang="less">
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
}

#nav {
    padding: 30px;

    a {
        font-weight: bold;
        color: #2c3e50;

        &.router-link-exact-active {
            color: #42b983;
        }
    }
}

.nav-items {
    justify-content: flex-end;
    display: flex;
}

.nav-items__item {
    margin-left: 1rem;
    position: relative;
}

ul {
    padding-left: 0;
    list-style: none;
}
</style>
