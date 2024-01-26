<script setup>
import Layout from './Layout.vue';
import FormVueVue from './FormVue.vue'
import Heading from '../components/Heading.vue'
</script>
<template>
    <Layout>
        <template #header>
            <Heading className="text-xl font-semibold p-4" title="Form Element" />
        </template>
        <template #default>
            <FormVueVue />
        </template>
        <template #footer></template>
    </Layout>
</template>