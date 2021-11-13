<template>
    <div>
      <div v-if="Carts.length === 0" class="cartEmpty">
        <h1>Cart Empty</h1>
      </div>
         <div class="ProductsPage">
            <div class="ProductsBooks">
                <div class="Products" v-for="product in Carts" :key="product.id">
                    <img :src="product.img" class="ProductImage">
                    <div class="ProductsDescription">
                        <h2 class="ProductTitle">{{product.title}}</h2>
                        <h3 class="ProductsPrice">${{product.price}}</h3>
                        <div class="ProductsButton">
                           <button class="btn" @click="RemoveFromCart(product)">Remove From Cart</button>
                    </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name:"Cart",
    props:["Carts","total"],
    methods: {
      RemoveFromCart(product) {
          return this.$emit("RemoveFromCart",product)
        },
    },
}
</script>
<style scoped>
.cartEmpty {
  text-align: center;
  margin-top: 3%;
}
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
  .cartEmpty {
    font-size: 10px;
  }
  .ProductImage {
    width: 200px;
    height: 300px;
  }
  .ProductTitle {
    font-size: 20px;
  }
}
</style>