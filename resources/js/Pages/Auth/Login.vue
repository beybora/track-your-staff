<template>
    <Head title="Login"></Head>

    <div class="min-h-screen flex flex-col justify-center items-center">
        <h1 class="text-3xl font-bold mb-8 text-gray-800">
            Login to your account
        </h1>

        <div class="w-full max-w-lg bg-white p-8 rounded shadow-md">
            <form @submit.prevent="submit">
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

                <div className="flex items-center gap-2">
                    <input
                        type="checkbox"
                        v-model="form.remember"
                        id="remember"
                    />
                    <label for="remember">Remember me</label>
                </div>
                <button
                    type="submit"
                    :disabled="form.processing"
                    class="w-full bg-blue-600 text-white p-3 rounded font-semibold hover:bg-blue-700 transition"
                >
                    Login
                </button>
                <p class="text-center text-slate-600 mt-4">
                    Need an account?
                    <a
                        :href="route('register')"
                        class="text-blue-500 hover:underline"
                        >Register</a
                    >
                </p>
            </form>
        </div>
    </div>
</template>

<script setup>
import { useForm } from "@inertiajs/vue3";
import TextInput from "@/Components/TextInput.vue";

const form = useForm({
    email: null,
    password: null,
    remember: null,
});

const submit = () => {
    form.post(route("login"), {
        onError: () => {
            form.reset("password, remember");
        },
    });
};
</script>
