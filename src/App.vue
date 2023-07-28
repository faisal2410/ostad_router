<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <header>
    <div >    
     
<h1 class="text-3xl text-center text-green-700 bg-red-100 font-bold underline">Hello world</h1>
      <nav class="flex justify-center items-center text-2xl mt-4">
        <RouterLink class="mr-[30px] hover:text-blue-300 transition-all " to="/">Home</RouterLink>
        <RouterLink class="hover:text-blue-300 mr-[30px]" to="/about">About</RouterLink>
        <RouterLink  class="hover:text-blue-300" to ="/movies">Movies</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>

</style>
