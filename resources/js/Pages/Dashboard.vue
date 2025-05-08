<template>
    <div>
        <h1 class="text-3xl font-bold mb-6 text-center">
            Welcome back {{ $page.props.auth.user.name }}
        </h1>
    </div>
</template>

<script setup>
import { Head } from "@inertiajs/vue3";
</script>

<style scoped></style>
