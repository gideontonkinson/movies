<template>
<div>
  <div class="info">
    <h1>{{movie.title}}</h1>
    <h2>{{movie.genere}}</h2>
    <p>Directed by: {{movie.director}}</p>
    <p>Studio: {{movie.studio}}</p>
    <p>Film Critics Review: '{{movie.summary}}'</p>
  </div>
  <div class = "center">
    <StarRating @rating-selected ="setRating" v-bind:increment="0.5" v-bind:max-rating="5" v-bind:show-rating="false" inactive-color="#666" active-color="#339BFF"></StarRating>
    <p><i>Average Rating: {{movie.ratings.avg}}</i></p>
    <h3>Add a Comment</h3>
    <form v-on:submit.prevent="addComment">
        <input v-model="addedName" placeholder="Name">
        <br>
        <textarea v-model="addedComment"></textarea>
        <br />
        <button type="submit">Comment</button>
    </form>
    <h3>Comments</h3>
    <div v-for="comment in movie.comments" :key="comment.date">
      <hr>
      <p>{{comment.text}}</p>
      <p><i>-- {{comment.author}}</i></p>
      <p><i>{{comment.date}}</i></p>
    </div>
</div>
</div>
</template>

<script src="https://momentjs.com/downloads/moment.js"></script>
<script>
import StarRating from 'vue-star-rating'
export default {
  components: {
    StarRating
  },
  name: 'MovieList',
  data() {
    return {
      movie: {},
    }
  },
  mounted() {
    const plugin = document.createElement("script");
    plugin.setAttribute(
      "src",
      "https://momentjs.com/downloads/moment.js"
    );
    plugin.async = true;
    document.head.appendChild(plugin);
  },
  created() {
    this.movie = this.$root.$data.movies.find(movie => movie.id === this.$route.params.id);
    if(this.movie.ratings.sum == undefined){
      this.movie.ratings.sum = 0;
      this.movie.ratings.total = 0;
      this.movie.ratings.avg = 0
    }
  },
  methods: {
    addComment() {
      this.movie.comments.push({
        author: this.addedName,
        text: this.addedComment,
        date: moment().format('MMMM Do YYYY, h:mm a'),
      });
      this.addedName = '';
      this.addedComment = '';
    },
    setRating(rating) {
      this.movie.ratings.sum += rating;
      this.movie.ratings.total += 1;
      this.movie.ratings.avg = (this.movie.ratings.sum/this.movie.ratings.total).toFixed(2);
      this.$forceUpdate()
    }
  }
}
</script>

<style scoped>
button {
    font-family: 'Montserrat', sans-serif;
    font-size: 1em;
}

textarea {
    width: 100%;
    max-width: 500px;
    height: 100px;
    justify-content: center;
    margin: 1em;
}

input {
  justify-content: center;
  margin: 1em;
}

.center {
    text-align: center;
}

.vue-star-rating{
  justify-content: center;
}
</style>

