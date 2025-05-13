<template>
    <button @click="$emit('back')" class="back-btn">Back</button>
    <div class="main">
    <div class="detail">
        <img :src="product.image" alt="Product image" width="200" class="product-image"/>
        <div class="product-info">
            <h2>{{ product.title }}</h2>
            <span>{{ product.category }} {{ product.rating.rate }} /5</span>
            <span class="rating"> {{ product.rating.rate }} /5</span>
            <p class="product-description">{{ product.description }}</p>
            <h3 class="product-price">${{ product.price }}</h3>
            
            <button class="buy-btn">Buy now</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'ProductDetail',
    props: {
        product: {
        type: Object,
        required: true
        }
    }
}
</script>

<style scoped>
.back-btn {
    margin: 20px;
    padding: 8px 14px;
    border: 1px solid #3f3f3f;
    border-radius: 4px;
    cursor: pointer;
}
.main{
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0 20px;
}
.detail{
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    border: 1px solid #dcdcdc;
    border-radius: 10px;
    padding: 20px;
    background-color: #fafafa;
    box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    text-align: left;
}
.product-image {
    width: 110px;
    height: auto;
    margin-right: 20px;
    margin-top: 20px;
    object-fit: contain;
    align-self: center;
}
.buy-btn {
    background-color: #3f3f3f;
    color: white;
    padding: 8px 50px;
    border: none;
    border-radius: 5px;
    font-weight: bold;
    cursor: pointer;
}
</style>