<script>
import MainLayout from "@/Layouts/MainLayout.vue";
import {Link} from "@inertiajs/vue3";

export default {
    name: "Index",
    components: {MainLayout, Link},

    props: [
        'posts'
    ],

    methods:{
        deletePost(id){
            this.$inertia.delete(`/posts/${id}`)
        }
    }
}
</script>

<template>
    <MainLayout>
        <h1 class="text-lg mb-8">Posts</h1>
        <div class="mb-8">
            <Link :href="route('post.create')"
                  class="block text-center border border-sky-500 bg-sky-500 rounded-full p-2 text-white w-32 hover:bg-white hover:text-sky-500">
                Add post
            </Link>
        </div>
        <div v-if="posts">
            <div v-for="post in posts" class="mt-3 pt-3 border-t border-t-black">
                <div>id: {{ post.id }}</div>
                <div>title: {{ post.title }}</div>
                <div>content: {{ post.content }}</div>
                <div class="text-right text-gray-500">{{ post.date }}</div>
                <div class="text-right">
                    <Link :href="route('post.show', post.id)" class="text-sky-500">Show</Link>
                </div>
                <div class="text-right">
                    <Link :href="route('post.edit', post.id)" class="text-sky-500">Edit</Link>
                </div>
                <div class="text-right">
                    <p @click="deletePost(post.id)" class="cursor-pointer text-red-700">Delete</p>
                </div>
            </div>
        </div>
    </MainLayout>
</template>

<style scoped>

</style>
