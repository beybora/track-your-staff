<template>
    <div>
        <header class="bg-cyan-700">
            <nav
                class="flex justify-between items-center p-4 max-w-screen-2xl mx-auto"
            >
                <div class="space-x-6">
                    <Link
                        :href="route('home')"
                        class="nav-link"
                        :class="{ 'bg-slate-700': $page.component === 'Home' }"
                    >
                        Home
                    </Link>
                    <Link
                        :href="route('about')"
                        class="nav-link"
                        :class="{ 'bg-slate-700': $page.component === 'About' }"
                    >
                        About
                    </Link>
                </div>

                <div class="space-x-6">
                    <div
                        v-if="$page.props.auth && $page.props.auth.user"
                        class="space-x-6"
                    >
                        <Link
                            :href="route('dashboard')"
                            class="nav-link"
                            :class="{
                                'bg-slate-700': $page.component === 'Dashboard',
                            }"
                        >
                            Dashboard
                        </Link>
                        <Link
                            :href="route('logout')"
                            method="post"
                            as="button"
                            class="text-white bg-red-400 px-4 py-2 rounded"
                        >
                            Logout
                        </Link>
                        <span class="text-xl font-bold text-white">
                            {{ $page.props.auth.user.name }}
                        </span>
                    </div>
                    <div v-else class="space-x-6">
                        <Link
                            :href="route('register')"
                            class="nav-link"
                            :class="{
                                'bg-slate-700':
                                    $page.component === 'Auth/Register',
                            }"
                        >
                            Register
                        </Link>
                        <Link
                            :href="route('login')"
                            class="nav-link"
                            :class="{
                                'bg-slate-700':
                                    $page.component === 'Auth/Login',
                            }"
                        >
                            Login
                        </Link>
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
import { Link, usePage } from "@inertiajs/vue3";
</script>

<style scoped>
.nav-link {
    color: white;
    padding: 8px 16px;
    border-radius: 4px;
    transition: background-color 0.2s;
}

.nav-link:hover {
    background-color: #5e9ca0;
}

.bg-slate-700 {
    background-color: #334155;
}
</style>
