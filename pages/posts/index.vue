<template>
    <section class="bg-white dark:bg-gray-900">
        <p class="mb-8">Questa pagina elenca le montagne e fornisce informazioni su ciascuna di esse.</p>

        <p v-if="$fetchState.pending">Fetching...</p>
        <p v-else-if="$fetchState.error">An error occurred...</p>
        <div v-else>
            <h2 class="text-xl font-bold mb-2">Nuxt Post (light)</h2>
            <ul>
                <NuxtLink v-for="post of posts" :to="'/posts/'+post.id"
                    class="inline-block py-1 px-2 bg-slate-200 mr-2 mb-2 rounded-xl">
                    {{ post.title }}
                </NuxtLink>
            </ul>
            
            <h2 class="text-xl font-bold mb-2 mt-4">Nuxt Posts (full version)</h2>
            <ul>
                <li v-for="post of posts" class="inline-block py-1 px-2 bg-slate-200 mr-2 mb-2 rounded-xl">
                    <b>{{ post.title }}</b>
                    <small>{{ post.body }}</small>
                    <small class="bg-slate-300 rounded-xl p-0.5 px-1 mr-1">id: {{ post.id }}</small>
                    <NuxtLink :to="'/posts/'+post.id" class="text-sm bg-slate-300 rounded-xl p-0.5 px-1 font-bold cursor-pointer opacity-50">leggi post</NuxtLink>
                </li>
            </ul>
            <button @click="$fetch" class=" border-slate-50">Refresh ($fetch)</button>
        </div>
    </section>
    </template>
    
    <script>
    export default {
      name: 'PostsPage',
      transition: 'fadein',

      head: {
        title: 'Posts Page'
      },

      data: () => ({
        posts: [],
      }),

      async fetch() {
        this.posts = await fetch('https://jsonplaceholder.typicode.com/posts?_limit=10')
            .then(res => res.json())
            .then(data => {
                return data;
            });
      },
    }
    </script>
    