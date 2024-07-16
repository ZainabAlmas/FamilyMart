<template>
  <div>
    <div class="navbar">
      <h1>MegaMart</h1>
      <input
        type="text"
        id="Search here"
        placeholder="Search here..."
        required
      />
      <div id="cart-logo">
        <i class="fa fa-shopping-cart" style="color: #2bbdebf5">Cart</i>
        <span id="cart-count">0</span>
      </div>
    </div>

    <div class="container">
      <div class="row">
        <!-- Sample product template, repeat for each product -->
        <div
          class="col col-12 col-sm-6 col-md-4"
          id="product-1"
          v-for="product in products"
          :key="product.id"
        >
          <div class="card">
            <img :src="product.image" class="ml-4" height="200" />
            <div class="card-title">{{ product.title }}</div>
            <div class="card-text">{{ product.description }}</div>
            <div class="card-text price">{{ product.price }} $</div>
            <button class="btn" @click="addToCart">Add to Cart</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>

export default {
  data() {
    return {
      products: [],
    };
  },
  methods: {
    async fetchProducts() {
      try {
        const response = await fetch("https://fakestoreapi.com/products");
        this.products = await response.json();
      } catch (error) {
        console.error("Error fetching products:", error);
      }
    },

    
  },
  mounted() {
    this.fetchProducts();
  },
};
</script>

<style scoped>

.container{
  background-color: rgb(239 245 245) ;
}
.navbar {
  display: flex;
  height: 93px;
  justify-content: space-evenly;
  align-items: center;
  /* margin-top: 20px; */
  background-color: rgb(255, 255, 255);
}
h1 {
  color: #2bbdebf5;
  font-size: 2rem;
  font-family: sans-serif;
  padding-top: 12px;
}

input {
  width: 400px;
  padding: 14px;
  border: 1px solid #0000ff24;
  border-radius: 10px;
  margin-right: 105px;
  background-color: #b8cad617;
  margin-top: 5px;
}

.fa {
  font-size: 28px;
  cursor: pointer;
  padding-top: 12px;
  font-style: normal;
  font-family: sans-serif;
  font-weight: bold;
}
#cart-count {
  color: #2bbdebf5;
  position: absolute;
  right: 149px;
  font-weight: bold;
  top: 32px;
}



.btn {
      background-color: #66e2e4cc;
    color: black;
    padding: 6px 26px;
    border-radius: 5px;
    cursor: pointer;
    border: 2px solid #47b3cfb5;
}
.container {
  width: 100%;
  margin: 0 auto;
  padding: 16px;
}
.row {
  display: flex;
  flex-wrap: wrap;
}
.col {
  padding: 16px;
  box-sizing: border-box;
}
.col-12 {
  flex: 0 0 100%;
  max-width: 100%;
}
.col-sm-6 {
  flex: 0 0 50%;
  max-width: 50%;
}
.col-md-4 {
  flex: 0 0 33.3333%;
  max-width: 33.3333%;
}
.card {
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 16px;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  background-color: rgb(255, 255, 254);
  height: 94%;
}
.card img {
  height: 170px;

  object-fit: cover;
  border-radius: 8px;
}
.card-title {
  color: #4fc3f7;
  font-size: 1.25rem;
  font-weight: bold;
  margin: 16px 0;
}
.card-text {
  color: #000;
  font-size: 1rem;
  margin-bottom: 8px;
}
.card-text.price {
  font-size: 1.25rem;
  font-weight: bold;
}
.add-to-cart-btn {
  margin-left: 16px;
  margin-bottom: 12px;
  border-radius: 8px;
  background-color: #cddc39;
  padding: 8px 16px;
  cursor: pointer;
}
</style>
