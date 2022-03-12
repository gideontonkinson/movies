<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/browse">Browse by Genere</router-link> | 
      <router-link to="/watchlist">Watchlist</router-link>
    </nav>
    <router-view/>
    <div class = "center">
      <a href = "https://github.com/BYUCS260/grocery-store-gideontonkinson" >GitHub Repository</a>
    </div>  
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
  font-size: 20px;
}

nav a.router-link-exact-active {
  color: #378ad8;
}
</style>
