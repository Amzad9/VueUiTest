<script setup>
import { ref } from 'vue'

import RadioButton from 'primevue/radiobutton';
import Checkbox from 'primevue/checkbox';
import InputSwitch from 'primevue/inputswitch';
import InputGroup from 'primevue/inputgroup';
import InputGroupAddon from 'primevue/inputgroupaddon';
import InputNumber from 'primevue/inputNumber';
import Dropdown from 'primevue/dropdown';
import Toast from './../components/Toast.vue'
import Calendar from 'primevue/calendar';
import InputVue from './../components/InputVue.vue';
import Textarea from "./../components/Textarea.vue"
import LabelVue from '../components/LabelVue.vue';
import Chips from './../components/chips.vue'
const username = ref("")
const checked = ref(false);
const checkedbox = ref(false);
const selectedCountry = ref("");
const toastShow = ref(true);
const ingredient = ref(false)
const date = ref('')
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

const chips = ref([
    { content: 'Item 1' },
    { content: 'Item 2' },
    { content: 'Item 3' },
    { content: 'Item 4' },
    { content: 'Item 5' }
]);

const removeChip = (index) => {
    console.log(index)
    chips.value.splice(index, 1);
};

const hide = () => {
    toastShow.value = !toastShow.value
    console.log(toastShow.value)
}
</script>

<template>
    <div class="grid grid-cols-12">
        <div class="col-span-3 p-4">
            <form @submit.prevent="">
                <InputVue v-model="username" label="Input Field" />
                <InputVue v-model="username" label="Input Field Focus" />
                <InputVue v-model="username" label="Input Field Desabled" disabled />
                <InputVue v-model="username" label="Input Field Focus" :error="true" />
                <div class="flex gap-4 w-64 mt-4">
                    <InputGroup>
                        <InputGroupAddon class="">$</InputGroupAddon>
                        <InputNumber placeholder="230,34,5" />
                    </InputGroup>
                    <InputGroup class="w-44">
                        <InputNumber value="rb1" placeholder="90" />
                        <InputGroupAddon>%</InputGroupAddon>
                    </InputGroup>
                </div>
                <Textarea v-model="username" label="TextArea" />
            </form>
        </div>
        <div class="col-span-3 border-l border-r border-indigo-100 p-4">
            <LabelVue label="Dropdown With Search"/>
            <Dropdown v-model="selectedCountry" :options="countries" filter optionLabel="name"
                placeholder="Select a Country" class="w-full md:w-14rem border border-gray-200">
                <template #value="slotProps">
                    <div v-if="slotProps.value" class="flex align-items-center">
                        <img :alt="slotProps.value.label"
                            src="https://primefaces.org/cdn/primevue/images/flag/flag_placeholder.png"
                            :class="`mr-2 flag flag-${slotProps.value.code.toLowerCase()}`" style="width: 18px" />
                        <div>{{ slotProps.value.name }}</div>
                    </div>
                    <span v-else>
                        {{ slotProps.placeholder }}
                    </span>
                </template>
                <template #option="slotProps">
                    <div class="flex align-items-center">
                        <img :alt="slotProps.option.label"
                            src="https://primefaces.org/cdn/primevue/images/flag/flag_placeholder.png"
                            :class="`mr-2 flag flag-${slotProps.option.code.toLowerCase()}`" style="width: 18px" />
                        <div>{{ slotProps.option.name }}</div>
                    </div>
                </template>
        </Dropdown>
        <div class="mt-1">
            <LabelVue label="Date Select"/>
            <Calendar v-model="date" class="  h-[36px] block"/>
        </div>
    </div>
    <div class="col-span-6 p-4">
        <Toast :show="toastShow" @onClick="hide"/>
        <Chips :chips="chips" @close="removeChip"/>
        <div class="mt-5 flex items-center">
            <InputSwitch v-model="checked" />
            {{ checkedbox }}
            <Checkbox v-model="checkedbox" inputId="ingredient1" name="pizza" value="Cheese" />
            <Checkbox v-model="checkedbox" inputId="ingredient2" name="pizza" value="Mushroom" />

           {{ ingredient }}
            <RadioButton v-model="ingredient" inputId="ingredient1" name="pizza" value="Cheese" />
            <RadioButton v-model="ingredient" inputId="ingredient1" name="pizza" value="Cheese1" />

        </div>
    </div>
</div>
</template>
<style scoped>
.p-calendar .p-inputtext {
    width: 100% !important;
}
</style>