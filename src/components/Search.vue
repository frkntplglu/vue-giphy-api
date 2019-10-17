<template>
  <div class="search">
    <input type="text" class="search-input" v-model='query' v-on:keyup.enter="findGiphy">
    <button @click="findGiphy" class="search-btn">SEARCH</button>
  </div>
</template>
<script>
export default {
  data(){
    return {
      query : ''
    }
  },

  methods : {
    findGiphy(){
      this.$emit('searchRequested',this.query);
    }
  }
}
</script>
<style lang="">
  .search{
    display: flex;
  }
  .search input{
    padding: 15px 20px;
    border-radius: 5px;
    border: 1px solid #ddd;
    width: calc(100% - 170px);
    font-size:14px;
    transition: 300ms;
  }
  .search input:focus{
    box-shadow: 0 0 5px #42b883;
    outline: #42b883;
  }
  .search button{
    width: 160px;
    margin-left: 10px;
    background:#42b883;
    border:none;
    border-radius: 5px;
    font-size: 14px;
    font-weight: 600;
    color:#fff;
    transition: 300ms;
    cursor: pointer;
  }
  .search button:hover{
    background: #35495e;
  }
</style>