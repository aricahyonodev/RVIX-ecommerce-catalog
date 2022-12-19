<template>
   <div class="product">
        <!-- Side Left -->
        <img :src="data.image" alt="">

        <!-- Side Right -->
        <div>
            <header>
                <h1>{{data.title}}</h1>
                <div>
                    <p>{{ data.category }}</p>
                    <p>{{ data.rating.rate}}</p>
                </div>
            </header>
            <main>
                <p>{{ data.description }}</p>
                <p>{{data.price}}</p>
                <div>
                    <button>Buy Now</button>
                    <button>Next Product</button>
                </div>
            </main>
        </div>
   </div>
</template>

<script>
export default {
    name: 'ProductDetail',
    props: {
        data: Object
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
    margin: 40px 0 0;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    display: inline-block;
    margin: 0 10px;
}

a {
    color: #42b983;
}
</style>
