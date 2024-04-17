<script setup>

import { ref, onMounted  } from 'vue';
import Card from './Card.vue';
import Loader from './basics/Loader.vue';
import SideBarFilters from './SideBarFilters.vue';

const products = ref([]);
const isLoading = ref(true);
const API_URL = import.meta.env.VITE_API_URL;
const errorMessages = ref(null);
const cart = ref([]);
const favorite = ref({});

const fetchProducts = async () => {
    try {
        const fetchProducts = await fetch(API_URL + '/products');
        products.value = await fetchProducts.json();
    } catch (error) {
        errorMessages.value = error.message;
    } finally {
        isLoading.value = false;
    }
}

onMounted(() => {
    setTimeout(async () => {
        await fetchProducts();
    }, 3000);
});

function pushToCart(product) {
  cart.value.push(product)
}

function pushToFavorite(product) {
  favorite.value = product
}

</script>

<template>
    <div class="flex justify-between">
        <div>CART: {{ cart }}</div>
        <div>Favoris: {{ favorite.title }}</div>
      </div>
      <div class="grid grid-cols-4 px-4">
          <SideBarFilters />
          <Section v-if="products.length > 0" class="flex flex-wrap justify-center my-10 gap-4 col-span-3">
              <Card v-for="product in products" :key="product.id" :product="product" @addToCart="pushToCart" :favoriteId="favorite.id"
                    @addToFavorite="pushToFavorite" />
          </Section>
      </div>

    <div v-if="errorMessages" class="flex justify-center items-center h-screen">
        <p class="text-destructive">{{ errorMessages }}</p>
    </div>

    <Loader v-if="isLoading" />

</template>