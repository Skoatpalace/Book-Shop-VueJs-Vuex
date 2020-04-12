<template>
  <div>
    <h1>Cart</h1>
    <div v-if="cart">
      <table class="table ">
        <thead class="thead-dark">
          <tr class="text-center">
            <th scope="col">Quantity</th>
            <th scope="col">Title</th>
            <th scope="col">image</th>
            <th scope="col">Price</th>
            <th scope="col"></th>
            <th scope="col"></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="product in cart.products" :key="product.id">
            <th scope="row">{{ product.quantity }}</th>
            <td>{{ product.title }}</td>
            <td><img :src="product.image" alt="image" width="100px" /></td>
            <td>{{ product.price }}</td>
            <td>
              <i
                class="far fa-minus-square fa-lg"
                @click="decrementQuantity(product)"
              ></i>
            </td>
            <td>
              <i
                class="far fa-plus-square fa-lg"
                @click="incrementQuantity(product)"
              ></i>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  created() {
    this.$store.dispatch("getCartFromStorage");
  },
  methods: {
    incrementQuantity(product) {
      this.$store.dispatch("updateCart", product);
    },
    decrementQuantity(product) {
      this.$store.dispatch("removeOneFromCart", product);
    }
  },
  computed: {
    cart() {
      return this.$store.getters.getCart;
    }
  }
};
</script>

<style scoped>
.quantity {
  border: 1px solid black;
  padding: 3px;
  margin: 3px;
  font-size: 17px;
  font-weight: bold;
}
.product {
  height: 89px;
  width: 80%;
  margin: 25px;
  border-bottom: 1px solid #ccc;
}
</style>
