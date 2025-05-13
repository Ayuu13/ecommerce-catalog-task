<template>
    <div class="page-container">
    <button @click="$emit('back')" class="back-btn">Back</button>
    
    <div class="main">
        <h2>MEN PRODUCTS (Men's Clothing)</h2>
        <div v-if="menProducts.length" class="product-list">
        <div v-for="(item, index) in menProducts" :key="index" class="product-card">
            <img :src="item.image" alt="product image" class="product-image" />
            <div class="product-info">
                <h3>{{ item.title }}</h3>
                <span class="rating">men's clothing {{ item.rating.rate }} /5</span>
                <p class="product-description">{{ item.description }}</p>
                <h4 class="product-price">${{ item.price }}</h4>
                
                <button class="buy-btn">Buy now</button>
            </div>
        </div>
        </div>
        <p v-else>Loading produk...</p>
    </div>
    </div>
</template>

<script>
export default{
    name: 'PageMen',
    props:{
        products:{
            type: Array,
            required: true
        }
    },
    computed:{
        menProducts(){
            return this.products.filter (
                item => item.category === "men's clothing"
            );
        }
    }
}
</script>

<style scoped>
.page-container {
    background-color: #D6E6FF;
    padding: 20px;
}
.back-btn {
    margin: 0 10px;
    margin-top: 10px;
    padding: 8px 20px;
    background: #002772;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}
.main {
    text-align: center;
}
.product-list{
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
    padding: 0 10px;
}
.product-card{
    display: flex;
    border: 1px solid #ddd;
    border-radius: 12px;
    padding: 20px;
    background-color: white;
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    text-align: left;
    max-width: 800px;
}
.product-image {
    width: 110px;
    height: auto;
    margin-right: 20px;
    margin-top: 20px;
    object-fit: contain;
    align-self: center;
}
.product-info h3 {
  color: #002772;
  margin-bottom: 10px;
}
.product-description {
  font-size: 14px;
}
.product-price {
  color: #002772;
  font-size: 20px;
  margin-bottom: 10px;
}
.buy-btn {
    background-color: #002772;
    color: white;
    padding: 8px 50px;
    border: none;
    border-radius: 5px;
    font-weight: bold;
    cursor: pointer;
}
</style>