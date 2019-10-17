<template>
  <div id="app">
    <h1>Giphy API Search</h1>
    <search v-on:searchRequested="findGiphy"></search>
    <div v-if="isLoaded" class="loading">Loading....</div>
    <list v-bind:gifs=gifs></list>
  </div>
</template>

<script>
import Search from './components/Search'
import List from './components/List'
export default {
  name: 'app',
  data () {
    return {
      gifs : [],
      isLoaded : true
    }
  },
  components : {
    Search,
    List
  },
  methods : {
    doFetch(url){
      fetch(url)
      .then(res => res.json())
      .then(res => {
        if(res.meta.status == 200){
          this.isLoaded = false;
          this.gifs = res.data;
          console.log(res);
        }else{

        }
      })
    },

    findGiphy(query){
      this.gifs = [];
      this.isLoaded = true;
      const url = `https://api.giphy.com/v1/gifs/search?api_key=UVElFfWz2XmXz230xqUG093OQo95V04g&q=${query}&limit=25&offset=0&rating=G&lang=en`;
      this.doFetch(url);
    }
  },
  created(){
    const url = 'https://api.giphy.com/v1/gifs/trending?api_key=UVElFfWz2XmXz230xqUG093OQo95V04g&limit=25&rating=G';
    this.doFetch(url)
  }
  
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #35495e;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

.loading{
  margin-top: 20px;
  font-weight:600;
  font-size: 22px;
  text-align: center;
}
</style>
