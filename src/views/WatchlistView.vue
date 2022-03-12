<template>
<div class = "wrapper">
    <h1 class = "empty">Watchlist</h1>
    <div v-if = "watchlist.length == 0">
        <h1 class = "empty">Your Watchlist is Empty</h1>
    </div>
    <div v-else class="watchlist">
        <div class="movies">
            <div v-for="movie in watchlist" :key="movie.id">
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
                    <button class="auto" v-on:click="remove(movie)">Remove from Watchlist</button>
                </div>
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
    background: #a250ee;
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