<template>
    <form class="w-[600px] h-[80px] flex items-center">
        <TextInput
            type="text"
            class="block w-full mr-2"
            v-model="form.search"
            autocompelete
            placeholder="Search For file and folder"
        />
    </form>
</template>

<script setup>
import { useForm } from "@inertiajs/vue3";
import TextInput from "../TextInput.vue";

const form = useForm({
    search: "",
});
</script>

<style lang="scss" scoped></style>
