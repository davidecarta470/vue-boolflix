<template>
  <div class="container">
    <h1>Film</h1>
    <div class="wrapper">
      <div v-for="(film,index) in films" :key="index" class="item">
        <img :src="film.poster_path" alt="">
        <h2>{{film.title}}</h2>
        <div class="original-title">{{film.original_title}}</div>
        <div class="lenguage">
           <span>Lingua:</span> 
           <span >{{film.original_language}}</span> 
        </div>
        <div class="vote">{{film.vote_average}}</div>
      </div>
    </div>
  </div>   
</template>

<script>
export default {
  name:'Movie',
  props:{
    films:Array
  },
  methods:{

  }
}
</script>

<style lang="scss" scoped>

@import '../assets/style/vars.scss';
@import '../assets/style/mixin.scss';
.container{
  h1{
    color: white;
    text-align: center;
  }

  .wrapper{
    @include display();
    flex-wrap:wrap;
    .item{
      width: 200px;
      margin:40px;
      color:white; 
      .lenguage,
      .original-title{
        padding:10px 0px;
      }  
     }
  }
}
</style>