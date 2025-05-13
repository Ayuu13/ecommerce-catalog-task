<template>
    <div class="main"><h1>WELCOME TO E-COMMERCE</h1></div>
    <div class="page-list">
        <div class="page1">
            <button @click="$emit('gotoMen')">MEN</button>
        </div>
        <div class="page2">
            <button @click="$emit('gotoWoman')">WOMAN</button>
        </div>
    </div>
    <div v-if="products.length" class="productAll">
        <div v-for="(item, index) in products" :key="index" class="product-card">
            <img :src="item.image" alt="product image" width="100"
            style="cursor: pointer" @click="$emit('seeDetail', item)"/>
        </div>
    </div>
    <p v-else>Loading produk...</p>
</template>

<script>
export default{
    name: 'MainPage',
    props:{
        products:{
            type: Array,
            required: true
        }
    }
}
</script>

<style scoped>
.main{
    padding: 10px;
    text-align: center;
}
.page-list{
    display: flex;
	justify-content: center;
}
.page1, .page2{
    border-radius: 5px;
    margin: 0 10px;
}
.productAll{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
    margin-top: 20px;
}
.product-card {
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 10px;
    text-align: center;
}
</style>