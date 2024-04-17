<script setup>

import { ref, onMounted  } from 'vue';
import Button from './basics/Button.vue';

const categories = ref([]);
const API_URL = import.meta.env.VITE_API_URL;

const fetchCategories = async () => {
    try {
        const fetchCategories = await fetch(API_URL + '/products/categories');
        categories.value = await fetchCategories.json();
    } catch (error) {
        errorMessages.value = error.message;
    }
}

onMounted(() => {
    setTimeout(async () => {
        await fetchCategories();
    }, 3000);
});

</script>

<template> 
    <aside>
        <h2 class="text-xl font-bold">Categories</h2>
        <ul>
            <li v-for="(category, index) in categories" :key="index">
                <Button>
                    {{ category }}
                </Button>
            </li>
        </ul>
    </aside>

</template>