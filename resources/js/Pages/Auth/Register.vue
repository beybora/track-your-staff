<template>
    <Head title="Register"></Head>

    <div class="min-h-screen flex flex-col justify-center items-center">
        <h1 class="text-3xl font-bold mb-8 text-gray-800">Register</h1>

        <div class="w-full max-w-lg bg-white p-8 rounded shadow-md">
            <form @submit.prevent="submit">
                <TextInput
                    name="name"
                    type="text"
                    v-model="form.name"
                    :message="form.errors.name"
                    placeholder="Enter your name"
                ></TextInput>

                <TextInput
                    name="email"
                    type="text"
                    v-model="form.email"
                    :message="form.errors.email"
                    placeholder="Enter your email"
                ></TextInput>

                <TextInput
                    name="password"
                    type="password"
                    v-model="form.password"
                    :message="form.errors.password"
                    placeholder="Enter your password"
                ></TextInput>

                <TextInput
                    name="confirm password"
                    type="password"
                    v-model="form.password_confirmation"
                    :message="form.errors.password_confirmation"
                    placeholder="Confirm your password"
                ></TextInput>

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
import TextInput from "@/Components/TextInput.vue";

const form = useForm({
    name: null,
    email: null,
    password: null,
    password_confirmation: null,
});

const submit = () => {
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
