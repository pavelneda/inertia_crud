<script>
import MainLayout from "@/Layouts/MainLayout.vue";
import {Link} from "@inertiajs/vue3";

export default {
    name: "Show",
    components: {MainLayout, Link},

    props: [
        'post'
    ],
}
</script>

<template>
    <MainLayout>
        <h1 class="text-lg mb-2">Post</h1>
        <div class="mb-8">
            <Link :href="route('post.index')" class="text-sm text-sky-500">Back</Link>
        </div>
        <div v-if="post">
            <div class="mt-3 pt-3 border-t border-t-black">
                <div>id: {{ post.id }}</div>
                <div>title: {{ post.title }}</div>
                <div>content: {{ post.content }}</div>
                <div class="text-right text-gray-500">{{ post.date }}</div>
            </div>
        </div>
    </MainLayout>
</template>

<style scoped>

</style>
