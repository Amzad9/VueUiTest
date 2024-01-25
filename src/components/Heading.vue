<script setup>
const props = defineProps({
    title: String,
    className: String
})
</script>

<template>
    <h4 :class="[`text-gray-500`, className]">{{ props.title }}</h4>
</template>