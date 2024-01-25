<script setup lang="ts">
import { defineProps, defineEmits } from 'vue';
import InputText from 'primevue/inputtext';

defineProps({
    label: {
        type: String,
        default: "",
    },
    placeholder: {
        type: String,
        default: "",
    },
    modelValue: {
        type: String,
        default: "",
        required: true,
    },
    error: {
        type: Boolean,
        default: false,
    },
    disabled:{
        type: Boolean,
        default: false, 
    }
});

const emit = defineEmits(["update:modelValue"]);

const inputHandle = (e: Event) => {
    const value = (e.target as HTMLInputElement).value;
    emit("update:modelValue", value);
};
</script>

<template>
    <div class="mb-2">
        <label 
        :for="label" 
        class="mb-1 block font-medium text-sm text-gray-700">
        {{ label }}
       </label>
        <InputText 
        :id="label" 
        :value="modelValue" 
        @input="inputHandle" 
         type="text" size="large" 
        :placeholder="placeholder"
        :disabled="disabled"
        :aria-label="label"
        :class="[`block w-full rounded-md  py-1.5 pl-7 pr-10  border`, error ? 'border-red-500 bg-red-100' : 'focus:border-blue-500  border-1']" />
    </div>
</template>
