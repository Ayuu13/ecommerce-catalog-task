<template>
  <div>
    <PageMain 
    v-if="currentPage === 'main'" :products="products"
    @gotoMen="currentPage = 'men'"
    @gotoWoman="currentPage = 'woman'"
    @seeDetail="handleSeeDetail"
    />
  </div>

  <PageMen v-if="currentPage === 'men'" :products="products" @back="currentPage = 'main'" />
  <PageWoman v-if="currentPage === 'woman'" :products="products" @back="currentPage = 'main'" />
  <ProductDetail v-if="currentPage === 'detail'" :product="selectedProduct" @back="currentPage = 'main'" />
  <UnavailablePage v-if="currentPage === 'unavailable'" @back="currentPage = 'main'" />
</template>

<script>
import axios from 'axios'
import PageMain from './components/MainPage.vue'
import PageMen from './components/PageMen.vue'
import PageWoman from './components/PageWoman.vue'
import ProductDetail from './components/ProductDetail.vue'
import UnavailablePage from './components/PageUnavailable.vue'

export default {
  name: 'App',
  components: {
    PageMain, PageMen, PageWoman, ProductDetail, UnavailablePage
  },
  data(){
    return{
      currentPage: 'main', // tampilan awal - default
      products:[] ,
      selectedProduct: null
    }
  },
  methods:{
    handleSeeDetail(product){
      const category = product.category.toLowerCase()
      if (category === "men's clothing" || category === "women's clothing"){
        this.selectedProduct = product
        this.currentPage = 'detail'
      } else {
        this.currentPage = 'unavailable'
      }
    }
  },
  mounted(){
    axios.get('https://fakestoreapi.com/products')
    .then(response =>{
      console.log("DATA: ",response.data)
      this.products = response.data
    })
    .catch(error =>{
      console.error('Gagal fetch data: ',error)
    })
  }
}
</script>