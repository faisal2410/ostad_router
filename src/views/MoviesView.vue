 <script setup>
 import { ref,reactive, onMounted } from 'vue';
 import MovieCard from "../components/MovieCard.vue"
 let movieList = reactive([])
 let isLoading = ref(true);

 onMounted(async() => {
     try {
         const result = await fetch("http://localhost:8000/movies/")
      const response = await result.json();
      movieList = response;
      isLoading.value=false  
     } catch (error) {
          console.error("Error Fetching", error);
          isLoading.value = false;
        
     }
    
 })
        
</script>
<template>
    <div>
       
        <h1>This is Movies Page</h1>
        <!-- <pre>{{ movieList }}</pre> -->
    </div>
    <div class="text-2xl font-bold text-indigo-700" v-if="isLoading">Loading...</div>
    <div class="grid grid-cols-3 gap-4 " v-else>
        <MovieCard
        v-for="movie in movieList"
        :key="movie.id"
        :movie="movie"
               />   

    </div>
</template>


<style  scoped>

</style>