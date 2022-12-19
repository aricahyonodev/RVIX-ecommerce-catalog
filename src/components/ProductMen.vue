<template>
   <div v-if="!isLoading" class="flex product_men">
        <!-- Side Left -->
        <div class="product_left">
            <img class="img_product"  :src="data.image" alt="">
        </div>

        <!-- Side Right -->
        <div class="product_detail">
            <header>
                <h1 class="blue_catalina product_title">{{data.title}}</h1>
                <div class="flex product_subtitle ">
                    <p>{{ data.category }}</p>
                    <div>{{ data.rating.rate }}/5
                    <span v-for="n in Math.ceil(data.rating.rate)">
                        <div class="rounded-solid-rate"></div>
                     </span>
                    <span v-for="n in 5 - Math.ceil(data.rating.rate) ">
                        <div class="rounded-rate"></div>
                     </span>
                    </div>
                </div>
            </header>
            <main>
                <p class="product-description">{{ data.description }}</p>
                <p class="price blue_catalina">${{data.price}}</p>
                <div>
                    <button class="button-buy">Buy Now</button>
                    <button class="button-next-product"  v-on:click="helloButton">Next Product</button>
                </div>
            </main>
        </div>
   </div>
    <div class="root-loader" v-else>
        <div class="loader"></div>
    </div>
</template>

<script>
export default {
    name: 'ProductMen',
    props: {
        data: Object,
        nextProduct: Function,
        isLoading: Boolean
    },
    data: function () {
        return {
            rateTopRounding: 0,
        }
    },
    methods: {
        helloButton(){
            this.$emit('nextProduct')
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.flex{
    display: flex;
    justify-content: space-between;
}
.product_men{
    padding: 32px 48px;
    margin: 0 10%;
    border-radius: 8px;
    box-shadow: rgba(14, 30, 37, 0.12) 0px 2px 4px 0px, rgba(14, 30, 37, 0.32) 0px 2px 16px 0px;
    background-color: white;
    height: 100%;
    color: #3F3F3F;
    text-align: left;
}
.product-description{
    height: 170px;
}
.price{
    font-size: 20px;
    font-weight: 600;
    padding: 12px 0;
    border-top: 1px solid #DCDCDC;
}

.blue_catalina{
    color: #002772;
}
.button-buy{
    background-color: #002772;
    color: white;
    margin-right: 20px;
    border: 1px solid #002772;
}
.button-next-product{
    background-color: #DCDCDC;
    color: #002772;
    margin-right: 20px;
    border: 3px solid #002772;
}
.img_product{
    width: 80%;
    max-height: 100%;
}

button{
    font-size: 16px;
    font-weight: 600;
    padding: 12px 16px;
    width: 30%;
    border-radius: 4px;
    box-sizing: border-box;
    cursor: pointer;
}
.product_left{
    width: 34%;
}
.product_title {
    font-size: 28px;
    margin-bottom: 16px;
}
.product_subtitle {
    padding-bottom: 8px;
    border-bottom: 1px solid #DCDCDC;
    margin-bottom: 24px;
}
.product_detail{
    width: 60%;
}

.rounded-solid-rate{
    display: inline-block;
    margin: 0 2px;
    width: 16px;
    height: 16px;
    border-radius: 100%;
    background-color: #002772;
}
.rounded-rate {
    display: inline-block;
    margin: 0 2px;
    width: 16px;
    height: 16px;
    border: 2px solid #002772;
    box-sizing: border-box;
    border-radius: 100%;
}

.loader {
    display: flex;
    border: 8px solid #f3f3f3;
    /* Light grey */
    border-top: 8px solid #3498db;
    /* Blue */
    border-radius: 50%;
    width: 50px;
    height: 50px;
    animation: spin 2s linear infinite;
}

@keyframes spin {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
}
.root-loader{
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    width: 100%;
}
</style>
