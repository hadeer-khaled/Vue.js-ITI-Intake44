<template>
  <div>
    <nav class="navbar navbar-expand-lg bg-body-tertiary mb-4">
      <div class="container-fluid">
        <a class="navbar-brand" href="#" @click="targetcomponent = 'Books'"
          >Books</a
        >
        <div>
          <button
            class="btn btn-outline-primary"
            type="submit"
            @click="targetcomponent = 'Wishlist'">
            WishList
          </button>
        </div>
      </div>
    </nav>
    <div class="row w-50 m-auto text-center g-0">
      <keep-alive>
        <component
          :is="targetcomponent"
          :books="books"
          :wishlist="wishlist"
          :addToWishlist="addToWishlist"
          :removeFromWishlist="removeFromWishlist"
          :formatPrice="formatPrice" />
      </keep-alive>
    </div>
  </div>
</template>

<script>
import Books from "./Books.vue";
import Wishlist from "./Wishlist.vue";
import booksList from "./../books";
export default {
  data: () => ({
    books: booksList,
    wishlist: {
      items: [],
    },
    counter: 0,
    targetcomponent: "Books",
  }),
  methods: {
    addToWishlist(book) {
      console.log(book.title);
      const existsInWishlist = this.wishlist.items.some(
        (item) => item.title === book.title
      );
      if (!existsInWishlist) {
        this.wishlist.items.push(book);
      } else {
        alert("Book already exists in the wishlist!");
        console.log("Book already exists in the wishlist!");
      }
    },
    removeFromWishlist(item) {
      const index = this.wishlist.items.findIndex(
        (wishlistItem) => wishlistItem.title === item.title
      );
      this.wishlist.items.splice(index, 1);
    },
    formatPrice(price) {
      const formatter = new Intl.NumberFormat("ar-SA", {
        style: "currency",
        currency: "SAR",
      });
      return formatter.format(price);
    },
  },
  components: { Books, Wishlist },
};
</script>

<style scoped></style>
