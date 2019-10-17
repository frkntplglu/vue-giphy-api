<template>
  <div>
    <ul>
      <li v-for="gif in gifs">
        <img :src="gif.images.fixed_width.url" alt="">
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  props : ['gifs'],
  data(){
    return {
      
    }
  }
}
</script>
<style lang="">
  ul{
    display:flex;
    flex-wrap: wrap;
    margin: 0;
    padding: 20px;
  }
  ul li{
    width: 20%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0;
    padding: 10px;
    box-sizing: border-box;
  }
  ul li img{
    width:100%;
  }
</style>