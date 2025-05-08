<template>
    <div class="mb-6">
        <label class="block text-gray-700 font-semibold mb-2">{{ name }}</label>
        <input
            :type="type"
            class="w-full p-3 border border-gray-300 rounded focus:outline-none focus:border-blue-500"
            :placeholder="placeholder"
            v-model="model"
        />
        <small v-if="message">{{ message }}</small>
    </div>
</template>

<script setup>
const model = defineModel({
    type: null,
    required: true,
});

defineProps({
    name: {
        type: String,
        required: true,
    },
    type: {
        type: String,
        default: "text",
    },
    message: {
        type: String,
    },
    placeholder: {
        type: String,
        default: "",
    },
});
</script>
