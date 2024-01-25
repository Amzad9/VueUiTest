
<script setup>
defineProps({
    label: {
        type: String,
        default: "",
    },
});

</script>
<template>
     <label 
        class="mb-1 block font-medium text-sm text-gray-700">
        {{ label }}
       </label>
</template>