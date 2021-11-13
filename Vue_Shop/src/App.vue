<template>
<div class="container">
  <div class="nav">
    <div class="logo">
      <h1><span class="ired">i</span>Books</h1>
    </div>
    <div class="links">
      <ul>
        <li class="ProductsLink"><h2 @click="navigateTo('ProductPage')">Products</h2></li>
        <li @click="navigateTo('CartPage')"><div class="icon"><i class="fas fa-cart-plus"></i></div></li>
        <div class="itemsCount" v-if="Carts.length >= 1">
          <span class="cartItems">{{Carts.length}}</span>
        </div>
      </ul>
    </div>
  </div>
  <div class="products" v-if="page === 'ProductPage'">
    <Product :Products="Products" @addToCart="addToCart"/>
  </div>

   <div class="cart" v-if="page === 'CartPage'">
    <Cart :Carts="Carts" @RemoveFromCart="RemoveFromCart"/>
  </div>
</div>
</template>
<script>
import Cart from "./components/Cart.vue";
import Product from "./components/Product.vue";
export default {
  name:"App",
  data() {
    return {
       Products:[
        {
          id:1,
          img:"https://dispatch.barnesandnoble.com/content/dam/ccr/bnstores/books/topnav-promopod-images/2021/Fiction/PROD-21823_RUSH_Fiction_Flyout1_Book_Club_Pick.jpg",
          title:"Our Country Friends",
          price:"14.59",
        },
        {
          id:2,
          img:"https://prodimage.images-bn.com/pimages/9780316485647_p0_v3_s192x300.jpg",
          title:"The Dark Hours",
          price:"20.30"
        },
        {
          id:3,
          img:"https://prodimage.images-bn.com/pimages/9780385546027_p0_v2_s192x300.jpg",
          title:"The Judges List",
          price:"25.00"
        },
        {
          id:4,
          img:"https://prodimage.images-bn.com/pimages/9781982154875_p0_v5_s192x300.jpg",
          title:"Game On",
          price:"20.29",
        },
        {
          id:5,
          img:"https://prodimage.images-bn.com/pimages/9780735222359_p0_v5_s192x300.jpg",
          title:"The Lincoln Highway",
          price:"23.99",
        },
        {
          id:6,
          img:"https://prodimage.images-bn.com/pimages/9780062671127_p0_v3_s192x300.jpg",
          title:"The Sentence",
          price:"22.99",
        },
        {
          id:7,
          img:"https://prodimage.images-bn.com/pimages/9781538719725_p0_v3_s192x300.jpg",
          title:"Mercy",
          price:"21.49",
        },
        {
          id:8,
          img:"https://prodimage.images-bn.com/lf?set=key%5Bresolve.pixelRatio%5D,value%5B1%5D&set=key%5Bresolve.width%5D,value%5B300%5D&set=key%5Bresolve.height%5D,value%5B10000%5D&set=key%5Bresolve.imageFit%5D,value%5Bcontainerwidth%5D&set=key%5Bresolve.allowImageUpscaling%5D,value%5B0%5D&product=path%5B/pimages/9781538728628_p0_v1%5D&call=url%5Bfile:common/decodeProduct.chain%5D",
          title:"The Wish",
          price:"19.60",
        },
        {
          id:9,
          img:"https://prodimage.images-bn.com/lf?set=key%5Bresolve.pixelRatio%5D,value%5B1%5D&set=key%5Bresolve.width%5D,value%5B300%5D&set=key%5Bresolve.height%5D,value%5B10000%5D&set=key%5Bresolve.imageFit%5D,value%5Bcontainerwidth%5D&set=key%5Bresolve.allowImageUpscaling%5D,value%5B0%5D&product=path%5B/pimages/9781250272706_p0_v2%5D&call=url%5Bfile:common/decodeProduct.chain%5D",
          title:"Becoming",
          price:"28.99"
        },
        {
          id:10,
          img:"https://prodimage.images-bn.com/lf?set=key%5Bresolve.pixelRatio%5D,value%5B1%5D&set=key%5Bresolve.width%5D,value%5B300%5D&set=key%5Bresolve.height%5D,value%5B10000%5D&set=key%5Bresolve.imageFit%5D,value%5Bcontainerwidth%5D&set=key%5Bresolve.allowImageUpscaling%5D,value%5B0%5D&product=path%5B/pimages/9780316499149_p0_v2%5D&call=url%5Bfile:common/decodeProduct.chain%5D",
          title:"Fear No Evil",
          price:"20.99"
        },
        {
          id:11,
          img:"https://prodimage.images-bn.com/lf?set=key%5Bresolve.pixelRatio%5D,value%5B1%5D&set=key%5Bresolve.width%5D,value%5B300%5D&set=key%5Bresolve.height%5D,value%5B10000%5D&set=key%5Bresolve.imageFit%5D,value%5Bcontainerwidth%5D&set=key%5Bresolve.allowImageUpscaling%5D,value%5B0%5D&product=path%5B/pimages/9781982173678_p0_v4%5D&call=url%5Bfile:common/decodeProduct.chain%5D",
          title:"State of Terror",
          price:"30.99",
        },
        {
          id:12,
          img:"https://prodimage.images-bn.com/pimages/9781982164881_p0_v4_s192x300.jpg",
          title:"Enemy Of The Gates",
          price:"20.99",
        }
      ],
      Carts:[],
      page:"ProductPage",
    }
  },
  components: {
    Cart,
    Product,
  },
  methods: {
    addToCart(product) {
      return this.Carts.push(product)
    },
    navigateTo(page) {
      return this.page = page;
    },
    RemoveFromCart(product) {
      return this.Carts.splice(this.Carts.indexOf(product),1);
    }
  },
}
</script>
<style>
*{
  margin:0;
  padding:0;
  box-sizing: border-box;
}
body {
  height: 100vh;
  width: 100%;
  font-family: sans-serif;
  position: relative;
}
.container {
  overflow:hidden;
}
.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 1%;
  height: 10vh;
  background: #eee;
}
.ired {
  color: #ff0000;
}
.links {
  display: flex;
  justify-content: center;
  align-items: center;
}
.links ul {
  list-style: none;
  margin: 10px;
}
.links ul li {
  display: inline-flex;
  margin: 10px;
  padding: 10px;
}
.icon {
  font-size: 20px;
}
.ProductsLink {
  cursor: pointer;
  transition: all 0.5s;
}
.ProductsLink:hover {
  color:#ff0000;
}
.itemsCount {
  background: #ff0000;
  width: 20px;
  height: 20px;
  text-align: center;
  position: absolute;
  top: 2px;
  right: 42px;
  border-radius: 10px;
}
.cartItems {
  color: #fff;
  margin-top: 10%;
  font-size: 15px;
}

@media (min-width:1279px) and (max-width:1280px) {
    .itemsCount {
  background: #ff0000;
  width: 20px;
  height: 20px;
  text-align: center;
  position: absolute;
  top: 15px;
  right: 42px;
  border-radius: 10px;
}
.cartItems {
  font-size: 20px;
  margin-top: 20px;
}
.icon {
  font-size: 25px;
}
}


@media (min-width:833px) and (max-width:834px) {
    .itemsCount {
  background: #ff0000;
  width: 20px;
  height: 20px;
  text-align: center;
  position: absolute;
  top: 23px;
  right: 37px;
  border-radius: 10px;
}
.cartItems {
  font-size: 20px;
  margin-top: 20px;
}
.icon {
  font-size: 25px;
}
}

@media (min-width:765px) and (max-width:768px) {
    .itemsCount {
  background: #ff0000;
  width: 20px;
  height: 20px;
  text-align: center;
  position: absolute;
  top: 20px;
  right: 36px;
  border-radius: 10px;
}
.cartItems {
  font-size: 15px;
  margin-top: 2px;
}
.icon {
  font-size: 22px;
}
}
@media(max-width:700px) {
  .nav {
    width: 100%;
  }
  .logo h1 {
    font-size: 20px;
  }
  .ProductsLink {
    font-size: 10px;
  }
  .icon {
    font-size: 20px;
  }
  .itemsCount {
  background: #ff0000;
  width: 20px;
  height: 20px;
  text-align: center;
  position: absolute;
  top: 12px;
  right: 33px;
  border-radius: 10px;
}
.cartItems {
  font-size: 14px;
  margin-top: 1px;
}
}
@media(orientation:landscape) and (max-width:667px) {
  .nav {
    height: 15vh;
  }
  .itemsCount {
  background: #ff0000;
  width: 20px;
  height: 20px;
  text-align: center;
  position: absolute;
  top: 0px;
  right: 35px;
  border-radius: 10px;
}
.cartItems {
  font-size: 13px;
}
}

</style>
