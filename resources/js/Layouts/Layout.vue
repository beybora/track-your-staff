<template>
    <div>
        <header class="bg-cyan-700">
            <nav
                class="flex justify-between items-center p-4 max-w-screen-2xl mx-auto"
            >
                <div class="space-x-6">
                    <Link :href="route('home')">Home</Link>
                    <Link :href="route('about')">About</Link>
                </div>

                <div class="space-x-6">
                    <div
                        class="space-x-6"
                        v-if="$page.props.auth && $page.props.auth.user"
                    >
                        <Link :href="route('dashboard')">Dashboard</Link>
                        <Link
                            :href="route('logout')"
                            method="post"
                            as="button"
                            class="text-white bg-red-400 px-4 py-2 rounded"
                        >
                            Logout
                        </Link>
                        <span class="text-xl">{{
                            $page.props.auth.user.name
                        }}</span>
                    </div>
                    <div v-else class="space-x-6">
                        <Link :href="route('register')">Register</Link>
                        <Link :href="route('login')">Login</Link>
                    </div>
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
