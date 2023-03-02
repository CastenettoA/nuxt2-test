<template>
    <header>

        <NuxtLink to="/">
            <div class="log flex items-center py-2 px-4">
                <img class="w-10" src="https://cdn1.iconfinder.com/data/icons/google-s-logo/150/Google_Icons-09-64.png"
                    alt="logo">
                <span class="font-bold ml-2">Nuxt2 Test</span>
            </div>
        </NuxtLink>

        <Menu />
    </header>
</template>

<script>
export default {
    name: 'HeaderComponent'
}
</script>