<template>
    <div>
        <header class="bg-cyan-700 text-white">
            <nav class="flex items-center justify-between p-4 max-w-screen-2xl">
                <div class="space-x-6">
                    <h1>{{ title }}</h1>
                    <Link :href="route('home')">Home</Link>
                    <Link :href="route('about')">About</Link>
                    <Link :href="route('register')">Register</Link>
                    <Link :href="route('login')">Login</Link>
                </div>
            </nav>
        </header>
        <main class="p-2 max-w-screen-2xl mx-auto">
            <slot></slot>
        </main>
    </div>
</template>

<script setup>
import { Link } from "@inertiajs/vue3";
</script>
