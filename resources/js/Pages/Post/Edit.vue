<script>
import MainLayout from "@/Layouts/MainLayout.vue";
import {Link} from "@inertiajs/vue3";

export default {
    name: "Edit",
    components: {MainLayout, Link},

    props:[
        'post'
    ],

    data() {
        return {
            id: this.post.id,
            title: this.post.title,
            content: this.post.content,
        }
    },

    methods: {
        update() {
            this.$inertia.patch(`/posts/${this.id}`, {
                title: this.title,
                content: this.content,
            })
        }
    }
}
</script>

<template>
    <MainLayout>
        <h1 class="text-lg mb-2">Edit post</h1>
        <div class="mb-8">
            <Link :href="route('post.index')" class="text-sm text-sky-500">Back</Link>
        </div>
        <form @submit.prevent="update">
            <div class="mb-4">
                <input v-model="title" class="w-full rounded-full border-sky-950" type="text" name="title"
                       placeholder="title">
            </div>
            <div class="mb-4">
                <textarea v-model="content" class="w-full rounded-full border-sky-950" name="content"
                          placeholder="content"></textarea>
            </div>
            <div>
                <button class="mx-auto block text-center border border-sky-500 bg-sky-500 rounded-full p-2 text-white w-32 hover:bg-white hover:text-sky-500">
                    Edit post
                </button>
            </div>
        </form>
    </MainLayout>
</template>

<style scoped>

</style>
