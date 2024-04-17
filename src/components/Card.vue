<script setup>
import { defineProps } from 'vue';
import AddToCart from './AddToCart.vue';
import { StarIcon } from 'lucide-vue-next';
import Button from './basics/Button.vue';

const props = defineProps({
    product: {
        type: Object,
        required: true
    },
    favoriteId: {
        type: Number,
        required: false
  }
});

const emit = defineEmits({
    addToCart: (product) => product,
    addToFavorites: (product) => product
});
</script>

<template>

    <div class="max-w-xs bg-card border border-primary text-card-foreground shadow-lg rounded-lg overflow-hidden">
        <img :src="product.image" alt="product" class="w-full p-2 h-36 object-contain object-center">
        <div class="p-4 flex flex-col justify-between gap-4">
            <div class="flex flex-col gap-2">
                <h1 class="text-gray-900 font-bold text-xl">{{ product.title }}</h1>
                <p class=" text-gray-600 text-sm h-28 overflow-auto">{{ product.description }}</p>
            </div>
            <div class="flex items-center justify-between ">
                <p class="text-gray-600">${{ product.price }}</p>
                <div class="flex gap-2 items-center">
                    <AddToCart @click="emit('addToCart', product)" />
                    <button @click="emit('addToFavorite',product)" :class="favoriteId === product.id ? 'text-warning' : 'text-foreground'">
                        <StarIcon />
                    </button>
                </div>
            </div>
        </div>
    </div>

</template>