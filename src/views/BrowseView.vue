<template>
<div>
  <div class="pure-menu pure-menu-horizontal">
    <ul class="pure-menu-list">
      <li class="pure-menu-item"><a @click="select('Documentary')" href="#" class="pure-menu-link">Documentary</a></li>
      <li class="pure-menu-item"><a @click="select('Action')" href="#" class="pure-menu-link">Action</a></li>
      <li class="pure-menu-item"><a @click="select('Crime')" href="#" class="pure-menu-link">Crime</a></li>
      <li class="pure-menu-item"><a @click="select('Thriller')" href="#" class="pure-menu-link">Thriller</a></li>
      <li class="pure-menu-item"><a @click="select('Comedy')" href="#" class="pure-menu-link">Comedy</a></li>
      <li class="pure-menu-item"><a @click="select('Horror')" href="#" class="pure-menu-link">Horror</a></li>
      <li class="pure-menu-item"><a @click="select('Mystery')" href="#" class="pure-menu-link">Mystery</a></li>
      <li class="pure-menu-item"><a @click="select('Adventure')" href="#" class="pure-menu-link">Adventure</a></li>
      <li class="pure-menu-item"><a @click="select('Animation')" href="#" class="pure-menu-link">Animation</a></li>
      <li class="pure-menu-item"><a @click="select('Children')" href="#" class="pure-menu-link">Children</a></li>
      <li class="pure-menu-item"><a @click="select('IMAX')" href="#" class="pure-menu-link">IMAX</a></li>
      <li class="pure-menu-item"><a @click="select('War')" href="#" class="pure-menu-link">War</a></li>
      <li class="pure-menu-item"><a @click="select('Sci-Fi')" href="#" class="pure-menu-link">Sci-Fi</a></li>
      <li class="pure-menu-item"><a @click="select('Romance')" href="#" class="pure-menu-link">Romance</a></li>
      <li class="pure-menu-item"><a @click="select('Fantasy')" href="#" class="pure-menu-link">Fantasy</a></li>
      <li class="pure-menu-item"><a @click="select('Western')" href="#" class="pure-menu-link">Western</a></li>
      <li class="pure-menu-item"><a @click="select('Film-Noir')" href="#" class="pure-menu-link">Film-Noir</a></li>
      <li class="pure-menu-item"><a @click="select('Musical')" href="#" class="pure-menu-link">Musical</a></li>
    </ul>
  </div>
  <MovieList :movies="movies" />
</div>
</template>

<script>
import MovieList from '../components/MovieList.vue';
export default {
  name: 'BrowseView',
  components: {
    MovieList
  },
  data() {
    return {
      genere: '',
    }
  },
  computed: {
    movies() {
      return this.$root.$data.movies.filter(movie => movie.genere.includes(this.genere));
    }
  },
  methods: {
    select(genere) {
      this.genere = genere;
    }
  }
}
</script>