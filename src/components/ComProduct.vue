<template>
  <main>
    <div class="menu">
      <h2 class="menu-title">Taste Our Foods & Enjoy</h2>
      <div class="menu-carousel">
        <div class="menu-item">
          <router-link
            :to="{ name: 'ProductDetail', params: { id: product.id } }"
          >
            <img :src="product.image" alt="Pumpkin Spice Juice" />
            <div class="menu-item-info">
              <h3>{{ product.name }}</h3>
              <p>{{ product.description }}</p>
              <p>{{ product.price }}</p>
            </div>
          </router-link>
        </div>
        <div>
          <button
            :disabled="product.quality === 0"
            @click="addToCart(product)"
          >
            {{ product.quality === 0 ? "Out of Stock" : "ADD TO CART" }}
          </button>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import ShoppingCart from '../data/ShoppingCart'
export default {
  props: ["product"],
  data() {
    return {
      id: this.product.id,
      cart: ShoppingCart, 
    };
  },
  methods: {
    addToCart(product) {
      const existingProduct = this.cart.find((item) => item.id === product.id);
      if (existingProduct) {
        existingProduct.quantity += 1;
      } else {
        const newProduct = { ...product, quantity: 1 };
        this.cart.push(newProduct);
      }
      console.log(this.cart); // For debugging
    },
  },
};
</script>

<style>
/* Your CSS code remains unchanged */
</style>
