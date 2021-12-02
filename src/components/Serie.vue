<template>
  <div class="container">
    <h1>Tv series</h1>
    <div class="wrapper">
      <div v-for="(serie,index) in series" :key="index" class="item">
        <img :src="serie.poster_path" alt="">
        <h2>{{serie.name}}</h2>
        <div class="original-title">{{serie.original_name}}</div>
        <div class="lenguage">
           <span>Lingua:</span>
           <span>{{serie.original_language}}</span> 
        </div>
        <div class="vote">{{serie.vote_average}}</div>
      </div>
    </div>
  </div>
     
</template>

<script>
export default {
  name:'Serie',
  props:{
    series:Array
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