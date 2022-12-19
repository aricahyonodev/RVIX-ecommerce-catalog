<template>
  <div id="app" v-if="data !== null" >
      <div v-if="data.category == 'men\'s clothing'" class="blue_tealish">
        <ProductMen :isLoading="isLoading" :data="data" @nextProduct="addPageIndex" />
      </div>
      <div v-if="data.category === 'women\'s clothing'" class="pink_lace">
        <ProductWomen :isLoading="isLoading" :data="data" @nextProduct="addPageIndex" />
      </div>
      <div v-if="data.category !== 'men\'s clothing' && data.category !== 'women\'s clothing'" class="grey_light">
        <ProductUnavailaible :isLoading="isLoading" @nextProduct="addPageIndex" />
      </div>
  </div>
</template>

<script>
import ProductMen from './components/ProductMen.vue'
import ProductWomen from './components/ProductWomen.vue'
import ProductUnavailaible from './components/ProductUnavailaible.vue'

export default {
  name: 'App',
  data: function () {
    return {
      pageIndex: 1,
      data: null,
      isLoading: true
    }
  },

  methods: {
    async getData(index){
      this.isLoading = true; 
      const res = await fetch(`https://fakestoreapi.com/products/${index}`);
      const finalRes = await res.json();
      this.isLoading = false; 
      this.data      = finalRes;
    },
      addPageIndex(){
        this.pageIndex++
         if (this.pageIndex > 20) {
            this.pageIndex = 1;
            this.getData(this.pageIndex)
          } else {
            this.getData(this.pageIndex)
          }
      }
  },
  mounted() {
    this.getData(this.pageIndex)
  },
  components: {
    ProductMen,
    ProductWomen,
    ProductUnavailaible
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
}

.pink_lace{
  padding-top: 60px;
  background-color: #FDE2FF;
  height: 60%;
}
.blue_tealish{
  padding-top: 60px;
  background-color: #D6E6FF;
  height: 60%;
}
.grey_light {
  padding-top: 60px;
  background-color: #DCDCDC;
  height: 60%;
}


</style>
