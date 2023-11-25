<template>
    <AuthenticatedLayout>
        <Head title="My Files"></Head>
        {{ $page.component }}
    </AuthenticatedLayout>
</template>

<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import { Head } from "@inertiajs/vue3";
</script>

<style lang="scss" scoped></style>
