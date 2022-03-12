<template>
<div class="wrapper">
  <div class="movies">
    <div v-for="movie in movies" :key="movie.id">
      <div class = "movie">
        <router-link  :to="'/movie/' + movie.id">
        <div class="info">
          <h1>{{movie.title}}</h1>
          <p>Genere: {{movie.genere}}</p>
          <p>Director: {{movie.director}}</p>
          <p>Studio: {{movie.studio}}</p>
          <p>Average Community Rating: {{movie.ratings.avg}}</p>
        </div>
        </router-link>
        <button class="auto" v-on:click="add(movie)">Add to Watchlist</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'MovieList',
  props: {
    movies: Array,
  },
    methods: {
        add(movie){
          var tempMovie = this.$root.$data.watchlist.filter((mov => mov.id === movie.id));
          if(tempMovie.length > 0){
            return;
          } else {
            this.$root.$data.watchlist.push({
            id: movie.id,
            title: movie.title,
            genere: movie.genere,
            director: movie.director,
            studio: movie.studio,
            summary: movie.summary,
            ratings: movie.ratings,
            comments: movie.comments
          });
        }
        }
    },
}


</script>

<style scoped>
.movies {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.movie {
  margin: 10px;
  margin-top: 50px;
  width: 200px;
}

.info {
  background: #42a146;
  color: #000;
  padding: 10px 15px;
  height: 230px;
  align-content: center;
}

.info h1 {
  font-size: 18px;
  margin: 7px 0px;
}

.info h2 {
  font-size: 16px;
}

.info p {
  margin: 5px 0px;
  font-size: 14px;
}


button {
  height: 50px;
  background: #666;
  color: white;
  border: none;
  width: 100%;
}

button:hover {
    background: #333
}

button:active {
    background: #000
}

.auto {
  margin-left: auto;
}

a {
  text-decoration: none;
}
</style>