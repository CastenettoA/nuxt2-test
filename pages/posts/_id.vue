<template>
    <Transition>
        <div v-if="post" class="max-w-lg">
        <h2 class="text-xl font-bold mb-2 capitalize">{{post.title}}</h2>
        <p class="bg-slate-100 rounded-xl">Contenuto: {{ post.body }}</p>
        <p class="bg-blue-300 rounded-xl  px-1 mr-1 inline-block text-sm mt-2">id: {{ post.id }}</p>
    </div>
    </Transition>
</template>

<script>

export default {
    name: 'PostPage',
    head: {
        // title: this.post.title
    },
    data() {
        return {
            id: this.$route.params.id,
            post: []
        }
    },
    async fetch() {
        this.post = await fetch(`https://jsonplaceholder.typicode.com/posts/${this.id}`)
            .then(res => res.json());
      },
}
</script>