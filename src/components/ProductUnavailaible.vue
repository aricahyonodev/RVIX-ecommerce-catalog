<template>
   <div v-if="!isLoading" class="product-unavailaible">
    <div class="product-content">
        <p>This product not available to show</p>
        <button class="button-next-product" v-on:click="helloButton">Next Product</button>
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
        isLoading: Boolean,
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
.product-unavailaible{
    padding: 32px 48px;
    margin: 0 10%;
    border-radius: 8px;
    box-shadow: rgba(14, 30, 37, 0.12) 0px 2px 4px 0px, rgba(14, 30, 37, 0.32) 0px 2px 16px 0px;
    background-color: white;
    height: 100%;
    color: #3F3F3F;
    text-align: center;
    display: flex;
    justify-content: center;
    align-items: center;
}

.product-content{
    width: 50%;
}
.button-next-product {
    background-color: white;
    color: #1E1E1E;
    border: 3px solid #1E1E1E;
}
button {
    margin-top: 12px;
    font-size: 16px;
    font-weight: 600;
    padding: 12px 16px;
    width: 60%;
    border-radius: 4px;
    box-sizing: border-box;
    cursor: pointer;
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

.root-loader {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    width: 100%;
}
</style>
