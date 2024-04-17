<script setup>
import { ShoppingCart } from 'lucide-vue-next';
import Button from '../basics/Button.vue';

</script>

<template>
   
    <header class="p-4 bg-primary text-primary-foreground w-full flex justify-between items-center">
        <div class="flex gap-2 items-center">
            <img src="../../assets/logo.png" alt="logo" width="45" height="45" />
            <h1 class="text-3xl bold uppercase">My beautiful shop</h1>
        </div>
        <nav>
            <ul class="flex gap-4 items-center">
                <li><a href="#" class="hover:text-accent">Home</a></li>
                <li><a href="#" class="hover:text-accent">Products</a></li>
                <li><a href="#" class="hover:text-accent">About</a></li>
                <li><a href="#" class="hover:text-accent">Contact</a></li>
                <Button class="rounded-lg">
                    <ShoppingCart class="h-15 w-15" />
                </Button>
            </ul>
        </nav>
    </header>

</template>
