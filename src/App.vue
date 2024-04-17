<script setup>
import Header from './components/layout/Header.vue';
import Footer from './components/layout/Footer.vue';
import Products from './components/Products.vue';
import SearchProduct from './components/SearchProduct.vue';
import BannerAd from './components/ads/BannerAd.vue';
import ColomnAd from './components/ads/ColomnAd.vue';

</script>

<template>
    <Header />
    
    <div class="flex justify-around items-center">
        <BannerAd />
        <BannerAd />
    </div>
    <div class="grid grid-cols-12 min-h-screen bg-background text-foreground">
        <div class="col-span-2 px-4 flex flex-col justify-around">
            <ColomnAd />
            <ColomnAd />
            <ColomnAd />
            <ColomnAd />
            <ColomnAd />
        </div>
        <main class=" col-span-8">
            <SearchProduct />
            <Products  />
        </main>
        <div class="col-start-11 col-span-2 px-4 flex flex-col justify-around">
            <ColomnAd  />
            <ColomnAd  />
            <ColomnAd  />
            <ColomnAd  />
            <ColomnAd  />
        </div>
    </div>
    <Footer />
</template>
