<template>
  <div class="home">
    <h1>Book Shop</h1>
    <products />
  </div>
</template>

<script>
import Products from "@/views/Products";
export default {
  name: "Home",
  components: {
    Products
  }
};
</script>
