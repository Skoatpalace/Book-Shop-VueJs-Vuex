<template>
  <div class="container">
    <form @submit.prevent="create">
      <div class="row">
        <div class="form-group col-lg-4">
          <label for="id">ISBN</label>
          <input
            v-model="book.id"
            type="text"
            class="form-control"
            id="id"
            placeholder="Enter ISBN"
          />
        </div>
        <div class="col-lg-8"></div>
      </div>
      <div class="form-group">
        <label for="title">Title</label>
        <input
          v-model="book.title"
          type="text"
          class="form-control"
          id="title"
          placeholder="Enter title"
        />
      </div>
      <div class="row">
        <div class="form-group col-lg-6">
          <label for="firstName">First name</label>
          <input
            v-model="book.author.firstName"
            type="text"
            class="form-control"
            id="firstName"
            placeholder="Author first name"
          />
        </div>
        <div class="form-group col-lg-6">
          <label for="lastName">Last name</label>
          <input
            v-model="book.author.lastName"
            type="text"
            class="form-control"
            id="lastName"
            placeholder="Author last name"
          />
        </div>
      </div>
      <div class="row">
        <div class="form-group col-lg-6">
          <label for="publisher">Publisher</label>
          <input
            v-model="book.publisher"
            type="text"
            class="form-control"
            id="publisher"
            placeholder="Publisher"
          />
        </div>
        <div class="form-group col-lg-3">
          <label for="year">Year</label>
          <input
            v-model="book.year"
            type="number"
            class="form-control"
            id="year"
            placeholder="Publication year"
          />
        </div>
        <div class="form-group col-lg-3">
          <label for="price">Price</label>
          <input
            v-model="book.price"
            type="text"
            class="form-control"
            id="price"
            placeholder="Price"
          />
        </div>
      </div>
      <div class="form-group">
        <label for="image">Image</label>
        <input
          v-model="book.image"
          type="text"
          class="form-control"
          id="image"
          placeholder="Image"
        />
      </div>
      <button type="submit" class="btn btn-primary">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      book: {
        id: "",
        title: "",
        author: {
          firstName: "",
          lastName: ""
        },
        publisher: "",
        year: "",
        price: 0,
        image: ""
      }
    };
  },
  methods: {
    create() {
      console.log(this.book);
      this.$store.dispatch("createProduct", this.book);
    }
  }
};
</script>

<style lang="scss" scoped></style>