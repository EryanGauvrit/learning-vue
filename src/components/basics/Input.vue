<script setup>
import { ref } from 'vue';
import { defineProps } from 'vue';

const input = ref('');
const props = defineProps({
    placeholder: {
        type: String,
        default: 'Search...',
    },
    type: {
        type: String,
        default: 'text',
    },
    modelValue: {
        type: String,
        default: '',
    },
    onInput: {
        type: Function,
        default: () => {},
    },
});



</script>

<template>
    <input
        v-model="input"
        :type="type"
        :placeholder="placeholder"
        @input="onInput(input)"
        class="w-full h-10 px-3 py-2 border border-primary bg-accent text-accent-foreground  rounded-lg focus:outline-none focus:border-primary"
    />
    

</template>