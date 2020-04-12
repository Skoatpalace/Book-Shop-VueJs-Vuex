<template>
  <div class="d-flex flex-wrap" v-if="products">
    <div
      class="product-single d-flex flex-column justify-content-between"
      v-for="product in products"
      :key="product.id"
    >
      <div>{{ product.title }}</div>
      <div>
        <img
          alt="book image"
          :src="product.image"
          class="product-image"
          width="100px"
        />
        <div class="product-price">{{ product.price }} €</div>
      </div>
      <button
        class="btn btn-outline-success btn-lg btn-block"
        @click="addToCart(product)"
      >
        Add to cart
      </button>
    </div>
  </div>
</template>

<script>
export default {
  created() {
    this.$store.dispatch("getProducts");
  },
  computed: {
    products() {
      return this.$store.state.products;
    }
  },
  methods: {
    addToCart(product) {
      this.$store.dispatch("updateCart", product).then(() => {
        console.log(this.$store.state.cart);
      });
    }
  }
};
</script>

<style scoped>
.product-single {
  padding: 5px;
  margin: 5px;
  width: 350px;
  height: 300px;
  border: 2px solid #666;
}
.product-image {
  margin: 5px;
  width: 30%;
}
.product-price {
  padding-left: 5px;
}
</style>
