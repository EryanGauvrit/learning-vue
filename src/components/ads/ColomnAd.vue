<script setup>

import { defineProps } from 'vue';

const props = defineProps({
    class: {
        type: String,
        required: false
    }
});
</script>

<template>
    <div :class="class">
        <img src="../../assets/ads/verticale.jpg" alt="vertical" class="w-auto h-full py-3 my-3 object-contain" />
    </div>
</template>
