
<script setup>
import {defineEmits, defineProps} from 'vue'
defineProps({
    show: Boolean,
    default: true
})
const emit = defineEmits(["onClick"])
const onClick = () => {
   emit('onClick');
}
</script>

<template>
    <div v-show="show" class=" bottom-4 right-4 z-50">
        <div class="bg-white shadow-md rounded-md  border border-gray-100">
            <!-- Toast content -->
            <div class="flex">
                <div class="w-full ">
                    <div class="flex justify-between border-b py-2 px-3 items-center">
                        <h4 class="text-md font-medium text-blue-500">Upload File</h4>
                        <button type="button" @click="onClick"
                            class="text-gray-400 hover:text-gray-500 focus:outline-none focus:text-gray-500 transition ease-in-out duration-150"
                            aria-label="Close">
                            <!-- Heroicon name: x -->
                            <svg class="h-5 w-5" fill="currentColor" viewBox="0 0 20 20">
                                <path fill-rule="evenodd"
                                    d="M5.293 5.293a1 1 0 011.414 0L10 8.586l3.293-3.293a1 1 0 111.414 1.414L11.414 10l3.293 3.293a1 1 0 01-1.414 1.414L10 11.414l-3.293 3.293a1 1 0 01-1.414-1.414L8.586 10 5.293 6.707a1 1 0 010-1.414z"
                                    clip-rule="evenodd" />
                            </svg>
                        </button>
                    </div>
                    <div class="p-4">
                        <p class="mt-1 text-sm text-gray-500 font-medium">You successfully upoad file!</p>
                    </div>
                </div>
            </div>
            <!-- Close button -->
        </div>
    </div>
</template>

