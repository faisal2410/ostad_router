 <script setup>
 import { ref,reactive, onMounted } from 'vue';
 import MovieCard from "../components/MovieCard.vue"
 let movieList = reactive([])
 const isLoading = ref(true);

 onMounted(() => {
      fetch("http://localhost:8000/movies/")
          .then(response => response.json())
           .then(apiMovies => {
                movieList = apiMovies
                console.log(movieList)
            isLoading.value = false;
        
            })
     .catch(error => {
      console.error('Error fetching movies:', error);
      isLoading.value = false; // Set loading to false even on error
    });
 })
        
</script>
<template>
    <div>
       
        <h1>This is Movies Page</h1>
        <!-- <pre>{{ movieList }}</pre> -->
    </div>
    <div v-if="isLoading">Loading...</div>
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