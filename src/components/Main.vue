<template>
  <main>
    <div class="wrapper">
     <div v-for="(film,index) in films" :key="index" class="item">
       <img :src="film.poster_path" alt="">
       <h2>{{film.title}}</h2>
       <div class="original-title">{{film.original_title}}</div>
       <div class="lenguage"> <span>Lingua:</span> {{film.original_language}}</div>
       <div class="vote">{{film.vote_average}}</div>
     </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
export default {
  name: 'Main',
  props:{
    getTitle:String
  },
  data(){
    return{
      films:[],
      url:'https://api.themoviedb.org/3/search/movie?api_key=f06b44ac869efe8c64e78f6eb1684059&query',
      filmTitle:''
    }
  },

  methods:{
    getApi(){
      axios.get(`${this.url}=${this.getTitle}}`)
       .then((respond)=>{
         this.films = respond.data.results
         
       })
       .catch((error)=>{
         console.log('errore',error)
       })

    }
  },

  mounted(){
    this.getApi()
  }
}
</script>

<style  lang="scss" scoped>
@import '../assets/style/vars.scss';
@import '../assets/style/mixin.scss';
main {
  min-height:calc(100vh - 80px);
  background-color:$primaryColor;
  .wrapper{
    @include display(space-around,0);
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