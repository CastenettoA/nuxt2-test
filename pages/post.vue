<template>
    <section class="bg-white dark:bg-gray-900">
        <p class="mb-8">sei nella pagina post.</p>

        <p v-if="$fetchState.pending">Fetching...</p>
        <p v-else-if="$fetchState.error">An error occurred...</p>
        <div v-else>
            <h2 class="text-xl font-bold mb-2">Nuxt Muntains</h2>
            <ul>
                <li v-for="mountain of mountains" class="inline-block py-1 px-2 bg-slate-200 mr-2 mb-2 rounded-xl">
                    {{ mountain.title }}
                </li>
            </ul>
            
            <h2 class="text-xl font-bold mb-2 mt-4">Nuxt Muntains (full version)</h2>
            <ul>
                <li v-for="mountain of mountains" class="inline-block py-1 px-2 bg-slate-200 mr-2 mb-2 rounded-xl">
                    <b>{{ mountain.title }}</b>
                    <small>{{ mountain.description }}</small>
                    <small class="bg-slate-300 rounded-xl p-0.5 px-1 mr-1">height: {{ mountain.height }}</small>
                    <small v-for="country of mountain.countries" class="bg-slate-300 rounded-xl p-0.5 px-1 mr-1">{{ country }}</small>
                </li>
            </ul>
            <button @click="$fetch" class=" border-slate-50">Refresh ($fetch)</button>
        </div>
    </section>
    </template>
    
    <script>
    export default {
      name: 'PostPage',

      head: {
        title: 'Post Page'
      },

      data: () => ({
        mountains: [],
        jsonAPi: []
      }),

      async fetch() {
        this.mountains = await fetch('https://api.nuxtjs.dev/mountains')
            .then(res => res.json());
      },
    }
    </script>
    