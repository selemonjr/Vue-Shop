<template>
    <div>
         <div class="ProductsPage">
            <div class="ProductTitle">
                <h1>The Best Selling Books of the Season</h1>
            </div>
            <div class="ProductsBooks">
                <div class="Products" v-for="product in Products" :key="product.id">
                    <img :src="product.img" class="ProductImage">
                    <div class="ProductsDescription">
                        <h2 class="ProductName">{{product.title}}</h2>
                        <h3 class="ProductsPrice">${{product.price}}</h3>
                        <div class="ProductsButton">
                        <button class="btn" @click="addToCart(product)">Add To Cart</button>
                    </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name:"Product",
    props:["Products"],
    methods: {
        addToCart(product) {
            return this.$emit("addToCart",product)
        },
    },
}
</script>
<style scoped>
.ProductTitle {
    text-align: center;
}
.ProductsBooks {
    display: flex;
    flex-wrap: wrap;
}
.Products {
    padding: 20px;
}
.ProductImage {
    width: 250px;
    height: 400px;
    margin: 20px;
}
.ProductsDescription {
     margin: -20px 20px 0 20px;
}
.ProductsPrice {
    margin: 10px 20px 0px 0;
}
.ProductsButton {
    margin-top: 10px;
}
.btn {
    padding: 5px 20px;
    font-size: 15px;
    transition: all 0.5s;
    border:1px solid #000;
    outline: none;
}
.btn:hover {
    background: #000;
    color: #fff;
}
@media (max-width:700px) {
  .ProductTitle {
    font-size: 10px;
    margin-top: 2%;
  }
    .ProductImage {
    width: 250px;
    height: 300px;
  }
}
</style>