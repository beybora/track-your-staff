<template>
    <Head :title="`${$page.component} - `" />
    <div>
        <table class="w-full border-collapse bg-white rounded shadow-md">
            <thead>
                <tr class="bg-slate-300">
                    <th class="p-4 text-left">Name</th>
                    <th class="p-4 text-left">Email</th>
                    <th class="p-4 text-left">Registration Date</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user in users.data" :key="user.id">
                    <td class="p-4 text-left">{{ user.name }}</td>
                    <td class="p-4 text-left">{{ user.email }}</td>
                    <td class="p-4 text-left">
                        {{ getDate(user.created_at) }}
                    </td>
                </tr>
            </tbody>
        </table>

        <div>
            <!-- Pagination Links -->
            <div>
                <Link
                    v-for="link in users.links"
                    :key="link.label"
                    :href="link.url || '#'"
                    v-html="link.label"
                    class="p-1 mx-1"
                    :class="{
                        'text-slate-300': !link.url,
                        'text-blue-500 font-medium': link.active,
                        'cursor-pointer': link.url,
                    }"
                ></Link>
            </div>

            <!-- Pagination Info -->
            <p class="text-slate-600 text-sm">
                Showing {{ users.from }} to {{ users.to }} of
                {{ users.total }} results
            </p>
        </div>
    </div>
</template>

<script setup>
import { Link } from "@inertiajs/vue3";

defineProps({
    users: Object,
});

const getDate = (date) =>
    new Date(date).toLocaleDateString("en-us", {
        year: "numeric",
        month: "long",
        day: "numeric",
    });
</script>
