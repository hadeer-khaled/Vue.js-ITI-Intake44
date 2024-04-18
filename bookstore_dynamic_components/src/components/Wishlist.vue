<template>
  <div class="whistlist-container container">
    <h2 class="text-center" v-if="wishlist.items.length == 0">
      The Wishlist is Empty
    </h2>
    <table class="table table-hover" v-if="wishlist.items.length != 0">
      <thead>
        <tr>
          <th scope="col">Image</th>
          <th scope="col">Title</th>
          <th scope="col">Price</th>
          <th scope="col">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in wishlist.items" :key="item.title">
          <td>
            <img :src="require(`../${item.imageLink}`)" style="width: 50px" />
          </td>
          <td>{{ item.title }}</td>
          <!-- <td>{{item.price}}</td> -->
          <td>{{ formatPrice(item.price) }}</td>
          <td>
            <button @click="removeFromWishlist(item)" class="btn btn-danger">
              <!-- style="border: none; background-color: transparent" -->
              <!-- <i class="fa-solid fa-trash" style="color: brown"></i> -->
              <FontAwesomeIcon icon="{faTrash}" />
              <!-- <font-awesome-icon icon="faTrash" /> -->
              Delete
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { faTrash } from "@fortawesome/free-solid-svg-icons";
export default {
  props: ["wishlist", "removeFromWishlist", "formatPrice"],
  component: { faTrash },
};
</script>

<style scoped></style>
