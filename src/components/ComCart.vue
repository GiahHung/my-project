<template>
  <div v-if="cart.length == 0">
    Cart empty
  </div>
  <div v-else class="modal-content">
    <table style="width: 100%;" class="text-center table">
      <tr>
        <th>HÌNH</th>
        <th>SẢN PHẨM</th>
        <th>Đơn giá</th>
        <th>Số lượng</th>
        <th>Tiền</th>
        <th></th>
      </tr>
      <!-- Display each cart item using v-for -->
      <tr v-for="item in cart" :key="item.id">
        <td><img :src="item.image" style="height: 100px; width: 100px;"></td>
        <td class="align-middle">{{ item.name }}</td>
        <td class="align-middle">{{ item.price }}</td>
        <td class="align-middle">
          <button class="btn btn-secondary" @click="decreaseQuantity(item.id)">-</button>
          {{ item.quantity }}
          <button class="btn btn-secondary" @click="increaseQuantity(item.id)">+</button>
        </td>
        <td class="align-middle">{{ item.price * item.quantity }}</td>
        <td class="align-middle">
          <button class="btn btn-danger" @click="removeItem(item.id)">Remove</button>
        </td>
      </tr>
      <tr>
        <th></th>
        <th></th>
        <th>Tổng tiền</th>
        <th></th>
        <th>{{ totalPrice }}</th>
        <th>
          <button class="btn btn-danger" @click="clearCart">Xóa hết</button>
        </th>
      </tr>
    </table>
  </div>
</template>

<script>
import items from '@/data/items.js';
import ShoppingCart from '../data/ShoppingCart.js';

export default {
  data() {
    return {
      cart: ShoppingCart,
    };
  },
  computed: {
    totalPrice() {
      return this.cart.reduce((sum, item) => sum + item.price * item.quantity, 0);
    },
  },
  methods: {
    increaseQuantity(id) {
      const item = this.cart.find((product) => product.id === id);
      const oldProduct = items.find((product) => product.id == id)
      if (item && oldProduct && oldProduct.quality > 0) {
        item.quantity++;
        oldProduct.quality--;
      }
    },
    decreaseQuantity(id) {
      const item = this.cart.find((product) => product.id === id);
      if (item && item.quantity > 1) {
        const oldProduct = items.find((product) => product.id == id)
        item.quantity--;
        oldProduct.quality++;
      } else {
        this.removeItem(id);
      }
    },
    removeItem(id) {
      this.cart = this.cart.filter((product) => product.id !== id);
    },
    clearCart() {
      this.cart.splice(0, this.cart.length);
    },
  },
};
</script>

<style>
/* Your CSS remains unchanged */
</style>
