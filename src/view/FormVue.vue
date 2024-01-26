<script setup>
import { ref, watchEffect } from 'vue'

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
import { chip, countries } from './../data/data'
const username = ref("")
const isUsernameValid = ref(true);
const checked = ref(false);
const checkedbox = ref(false);
const selectedCountry = ref("");
const toastShow = ref(true);
const ingredient = ref(false)
const date = ref('')

const chips = ref(chip);

const removeChip = (index) => {
    console.log(index)
    chips.value.splice(index, 1);
};

const hide = () => {
    toastShow.value = !toastShow.value
    console.log(toastShow.value)
}
watchEffect(() => {
    if (username.value.length > 5) {
        isUsernameValid.value = false;
    } else {
        isUsernameValid.value = true;
    }
})
</script>

<template>
    <div class="grid grid-cols-12">
        <div class="col-span-3 p-4">
            <form @submit.prevent="">
                <InputVue v-model="username" label="Input Field" />
                <InputVue v-model="username" label="Input Field Focus" />
                <InputVue v-model="username" label="Input Field Desabled" disabled />
                <InputVue v-model="username" label="Input Field Focus" :error="!isUsernameValid" placeholder="With Error" />
                <LabelVue label="Custom Input" />
                <div class="flex gap-4 w-64 mt-1 mb-1">
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
            <LabelVue label="Dropdown With Search" />
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
            <div class="mt-2">
                <LabelVue label="Date Select" />
                <Calendar v-model="date" class="  h-[36px] block" />
            </div>
        </div>
        <div class="col-span-6 p-4">
            <Toast :show="toastShow" @onClick="hide" />
            <Chips :chips="chips" @close="removeChip" />
            <div class="mt-5 flex items-center">
                <InputSwitch v-model="checked" />
                {{ checkedbox }}

                <Checkbox v-for="item in ['Cheese', 'Mushroom', 'Onion']" v-model="checkedbox" name="pizza" :value="item" />

                {{ ingredient }}
                <RadioButton v-for="item in ['Cheese', 'Mushroom', 'Onion']" v-model="ingredient" name="pizza"
                    :value="item" />

            </div>
        </div>
    </div>
</template>
<style scoped>
.p-calendar .p-inputtext {
    width: 100% !important;
}
</style>