<script setup>
import Input from './basics/Input.vue';

// on change value input, update url with ?search=value

const onInput = (value) => {
    const url = new URL(window.location.href);
    url.searchParams.set('search', value);
    window.history.pushState({}, '', url);
}

</script>

<template>
    <section class="flex justify-center items-center max-w-xl m-auto">
        <div class="flex flex-col items-center my-5">
            <Input placeholder="Search Products..." @onInput="onInput" />
        </div>
    </section>    

</template>