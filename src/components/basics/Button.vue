<script setup>

import { defineProps } from 'vue';

const props = defineProps({
    variant: {
        type: String,
        default: 'default',
        validator: (value) => {
            return ['default', 'outline', 'secondary', 'link', 'ghost', 'success', 'destructive', 'warning'].includes(value);
        }
    },
    size: {
        type: String,
        default: 'default',
        validator: (value) => {
            return ['default', 'sm', 'lg', 'icon'].includes(value);
        }
    },
    class: {
        type: String,
        default: ''
    }
});

const initialStyle = 'disabled:opacity-60 py-2 px-4 flex justify-center items-center font-bold text-white';

const variants = {
    default:
          "bg-card text-card-foreground shadow hover:bg-secondary hover:text-secondary-foreground",
    destructive:
        "bg-destructive text-destructive-foreground shadow-sm hover:bg-destructive/90",
    outline:
        "border border-input bg-background shadow-sm hover:bg-accent hover:text-accent-foreground",
    secondary:
        "bg-secondary text-secondary-foreground shadow-sm hover:bg-accent hover:text-accent-foreground",
    ghost: "hover:bg-accent hover:text-accent-foreground",
    link: "text-primary underline-offset-4 hover:underline",
    warning: "bg-warning text-warning-foreground shadow-sm hover:bg-accent",
    success: "bg-success text-success-foreground shadow-sm hover:bg-success/90",
}

const sizes = {
    default: "h-9 px-4 py-2",
    sm: "h-8 rounded-md px-3 text-xs",
    lg: "h-10 rounded-md px-8",
    icon: "h-15 w-15 rounded-full p-3",
};

</script>

<template>
    <button :class="initialStyle + ' ' + variants[variant] + ' ' + sizes[size]">
        <slot></slot>
    </button>
</template>