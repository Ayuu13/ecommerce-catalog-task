<template>
    <div class="page-container">
    <div class="unavailable">
        <div class="page-info">
        <h2>Oops! This product is unavailable to show</h2>
        <div>
            <button @click="$emit('back')" class="back-btn">Back to Home</button>
        </div>
        </div>
    </div>
    </div>
</template>

<script>
export default {
    name: 'UnavailablePage'
}
</script>

<style scoped>
.page-container{
    background-color: #dcdcdc;
    margin: 10px;
    margin-top: 20px;
    min-height: 80vh;
    display: flex;
    justify-content: center;
    align-items: center;
}
.unavailable{
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 30px;
}
.page-info{
    max-width: 500px;
    min-height: 250px;
    background-color: white;
    border-radius: 5px;
    padding: 0 20px;
    padding-bottom: 20px;
    box-shadow: 0 2px 6px #3f3f3f;
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
}
.back-btn {
    background-color: #3f3f3f;
    color: white;
    padding: 8px 30px;
    border: none;
    border-radius: 5px;
    font-weight: bold;
    cursor: pointer;
}
</style>