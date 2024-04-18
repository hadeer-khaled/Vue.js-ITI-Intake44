<template lang="">
  <div class="container products-container">
    <div class="row">
      <div
        v-for="book in books"
        class="mb-3 mx-auto col-3 col-sm-12 col-md-6 col-lg-3">
        <div class="card">
          <img
            :src="require(`../${book.imageLink}`)"
            class="card-img-top"
            alt="book cover"
            style="width: 100%" />
          <div class="card-body">
            <h5 class="card-title">{{ book.title }}</h5>
            <p class="card-text mb-1" style="color: gray; font-size: 12px">
              {{ book.author }}
            </p>
            <p class="card-text" style="color: gray; font-size: 12px">
              {{ book.category }}
            </p>
            <!-- <div class="d-flex justify-content-between"> -->
            <p class="card-text">Price: {{ formatPrice(book.price) }}</p>
            <p class="card-text">ISBN: {{ book.ISBN }}</p>
            <!-- </div> -->
            <div class="d-flex justify-content-between align-items-baseline">
              <p v-bind:class="getPagesColor(book)" style="font-size: 10px">
                Pages: {{ book.pages }}
              </p>
              <button
                type="button"
                class="btn btn-sm btn-primary rounded-3"
                style="font-size: 12px"
                @click="addToWishlist(book)">
                Add To Wishlist
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  methods: {},
  computed: {
    getPagesColor(book) {
      return function (book) {
        if (book.pages < 200) {
          return "badge text-bg-danger";
        } else if (book.pages < 600) {
          return "badge text-bg-warning";
        } else {
          return "badge text-bg-success";
        }
      };
    },
  },
  props: ["books", "addToWishlist", "formatPrice"],
};
</script>
<style scoped></style>
