<template>
    <div>
        <header class="bg-cyan-700 text-white">
            <nav class="flex items-center justify-between p-4 max-w-screen-2xl">
                <div class="space-x-6">
                    <h1>{{ title }}</h1>
                    <Link href="/">Home</Link>
                    <Link href="/about">About</Link>
                </div>
            </nav>
        </header>
        <main class="p-4 max-w-screen-2xl">
            <slot></slot>
        </main>
    </div>
</template>

<script setup>
import { Link } from "@inertiajs/vue3";
</script>
