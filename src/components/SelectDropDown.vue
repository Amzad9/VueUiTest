
<script setup>
import { ref } from 'vue'
import Dropdown from 'primevue/dropdown';

const selectedCountry = ref("");
const countries = ref([
    { name: 'Australia', code: 'AU' },
    { name: 'Brazil', code: 'BR' },
    { name: 'China', code: 'CN' },
    { name: 'Egypt', code: 'EG' },
    { name: 'France', code: 'FR' },
    { name: 'Germany', code: 'DE' },
    { name: 'India', code: 'IN' },
    { name: 'Japan', code: 'JP' },
    { name: 'Spain', code: 'ES' },
    { name: 'United States', code: 'US' }
]);

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
    },
    countries: {
        type:Array
    }
});

const emit = defineEmits(["update:modelValue"]);

const inputHandle = (e) => {
    const value = e.target.value;
    emit("update:modelValue", value);
};
</script>
<template>
    <div class="card flex justify-content-center">
        {{ selectedCountry }}
        
    </div>
</template>


