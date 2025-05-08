<template>
    <Head title="Register"></Head>

    <div class="min-h-screen flex flex-col justify-center items-center">
        <h1 class="text-3xl font-bold mb-8 text-gray-800">Register</h1>

        <div class="w-full max-w-lg bg-white p-8 rounded shadow-md">
            <form @submit.prevent="submit">
                <div class="mb-6">
                    <label class="block text-gray-700 font-semibold mb-2"
                        >Name</label
                    >
                    <input
                        type="text"
                        class="w-full p-3 border border-gray-300 rounded focus:outline-none focus:border-blue-500"
                        placeholder="Enter your name"
                        v-model="form.name"
                    />
                    <small>{{ form.errors.name }}</small>
                </div>

                <div class="mb-6">
                    <label class="block text-gray-700 font-semibold mb-2"
                        >E-Mail</label
                    >
                    <input
                        type="text"
                        class="w-full p-3 border border-gray-300 rounded focus:outline-none focus:border-blue-500"
                        placeholder="Enter your email"
                        v-model="form.email"
                    />
                    <small>{{ form.errors.email }}</small>
                </div>

                <div class="mb-6">
                    <label class="block text-gray-700 font-semibold mb-2"
                        >Password</label
                    >
                    <input
                        type="password"
                        class="w-full p-3 border border-gray-300 rounded focus:outline-none focus:border-blue-500"
                        placeholder="Enter your password"
                        v-model="form.password"
                    />
                    <small>{{ form.errors.password }}</small>
                </div>

                <div class="mb-6">
                    <label class="block text-gray-700 font-semibold mb-2"
                        >Confirm Password</label
                    >
                    <input
                        type="password"
                        class="w-full p-3 border border-gray-300 rounded focus:outline-none focus:border-blue-500"
                        placeholder="Confirm your password"
                        v-model="form.password_confirmation"
                    />
                </div>

                <button
                    type="submit"
                    :disabled="form.processing"
                    class="w-full bg-blue-600 text-white p-3 rounded font-semibold hover:bg-blue-700 transition"
                >
                    Register
                </button>

                <p class="text-center text-slate-600 mt-4">
                    Already a user?
                    <a href="#" class="text-blue-500 hover:underline">Login</a>
                </p>
            </form>
        </div>
    </div>
</template>
<script setup>
import { useForm } from "@inertiajs/vue3";

const form = useForm({
    name: null,
    email: null,
    password: null,
    password_confirmation: null,
});

const submit = (e) => {
    form.post(route("register"), {
        onError: () => {
            form.reset("password", "password_confirmation");
        },
        onFinish: () => {
            form.reset("password", "password_confirmation");
        },
    });
};
</script>
