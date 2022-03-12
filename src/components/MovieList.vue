<template>
<div class="wrapper">
  <div class="movies">
    <router-link v-for="movie in movies" :key="movie.id" :to="'/movie/' + movie.id">
      <div class = "movie">
        <div class="info">
          <h1>{{movie.title}}</h1>
          <p>{{movie.genere}}</p>
        </div>
        <div>
          <button class="auto" v-on:click="add(movie)">Add to Watchlist</button>
        </div>
      </div>
    </router-link>
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
  background: #F2921D;
  color: #000;
  padding: 10px 30px;
  height: 80px;
}

.info h1 {
  font-size: 16px;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}


button {
  height: 50px;
  background: #666;
  color: white;
  border: none;
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
</style>