<template>
    <nav class="min-w-[200px]">
        <Link
            :href="route('myFiles')"
            class="h-[80px] px-3 flex items-center gap-3"
        >
            <ApplicationLogo
                class="block h-9 w-auto fill-current text-gray-800 dark:text-gray-200"
            />
            LaraDrive
        </Link>
        <div class="px-4">
            <createNewDropdown />
            <div class="py-3">
                <NavLink
                    :href="route('myFiles')"
                    :active="$page.component === 'MyFiles'"
                    >My Files</NavLink
                >
                <NavLink href="/">Shared with me</NavLink>
                <NavLink href="/">Shared by me</NavLink>
                <NavLink href="/">Trash</NavLink>
            </div>
        </div>
    </nav>
</template>

<script setup>
import ApplicationLogo from "../ApplicationLogo.vue";
import createNewDropdown from "./createNewDropdown.vue";
import { Link } from "@inertiajs/vue3";
import NavLink from "../NavLink.vue";
</script>

<style lang="scss" scoped></style>
