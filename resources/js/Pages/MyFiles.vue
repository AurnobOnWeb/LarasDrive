<template>
    <AuthenticatedLayout>
        {{ $page.component }}
    </AuthenticatedLayout>
</template>

<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
</script>

<style lang="scss" scoped></style>
