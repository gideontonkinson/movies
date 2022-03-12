<template>
    <div class = "wrapper">
    <h1 class = "empty">Watchlist</h1>
    <div v-if = "watchlist.length == 0">
        <h1 class = "empty">Your Watchlist is Empty</h1>
    </div>
    <div v-else class="watchlist">
    <div class="movie" v-for="movie in watchlist" :key="movie.id">
      <div class="info">
        <h1>{{movie.title}}</h1>
        <p>{{movie.genere}}</p>
      </div>
      <div>
        <button v-on:click = "remove(movie)" class="auto">Remove from Watchlist</button>
      </div>
    </div>
    </div>
    </div>
</template>

<script>
export default {
    computed: {
        watchlist() {
            return this.$root.$data.watchlist;
        }
    },
    methods: {
        remove(movie){
            var tempWatchlist = this.$root.$data.watchlist.filter(item => item.id != movie.id);
            this.$root.$data.watchlist = tempWatchlist;
        }
    },
}
</script>

<style scoped>
    .watchlist {
        margin-top: 20px;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
    }

    .empty {
        text-align: center;
    }

    .movie {
        text-align:center;
    }

    .movie .image {
        display: flex;
        justify-content: center;
        margin-bottom: 5px;
    }

    .movie {
        margin: 10px;
        margin-top: 50px;
        border-style: solid;
        border-color: #F2921D;
        border-radius: 5px;
        width: 300px;
    }

    .movie img {
        height: 250px;
        width: 298px;
        object-fit: cover;
    }

    button {
        height: 50px;
        background: #666;
        color: white;
        border: none;
        padding: 7px;
        margin: 10px;
    }

    button:hover {
        background: #333
    }

    button:active {
        background: #000
    }
</style>