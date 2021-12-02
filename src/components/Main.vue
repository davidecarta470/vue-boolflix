<template>
  <main>
    <Movie
    :films="films"
    v-if="isFilm"
    />
    <Serie
    :series="series"
    v-if="isSerie"
    />
  </main>
</template>

  

<script>
import axios from "axios";
import Movie from './Movie.vue';
import Serie from './Serie.vue';
export default {
  name: 'Main',
  components:{
    Movie:Movie,
    Serie:Serie,
  },
  props:{
    titleType:Object
  },
  data(){
    return{
      isFilm:false,
      isSerie:false,
      films:[],
      series: [],
      apiUrl:'https://api.themoviedb.org/3/search/',
      apiParams:{
        query:'',
        api_key:'f06b44ac869efe8c64e78f6eb1684059'
      },
        
    }
  },
  methods:{
 


    getApi(query,type){
      axios.get(this.apiUrl+type,{
        params:{
          query:query,
          api_key:'f06b44ac869efe8c64e78f6eb1684059'}
      })
      .then((respond)=>{
        if(type==='movie') {
          this.films = respond.data.results 
          console.log(this.films)
        }else {
          this.series = respond.data.results
        }
        
      })
      .catch((error)=>{
        console.log('errore',error,type)
      })
    },
   
    
     
          
          
    // newfunction(){
    //   this.getApi()
    // }
  },
  // la computed non è adeguata per chiamare funzioni 
  // in questo caso si viene a creare un ciclo di getApi continuo.Riesco ad evitarlo
  // chiamando una ulteriore funzione all'interno della computed (newfunction) ma l'utilizzo 
  // della watch è preferibile
  // computed:{
  //   getTitle(){ 
  //     if(this.filmsChosed!==''){
  //       this.newfunction()
  //     }
  //   return this.filmsChosed
  //   }
        
  // }
  watch:{
    titleType(value){
      const  {searchTitle,type} = value
      if (searchTitle!==''&& type){
        
        if(type==='all'){
          this.isFilm=true;
          this.isSerie=true;
          const options = ['movie','tv'] ;
          for (let i=0; i<2; i++){
            this.getApi(searchTitle,options[i]);
          }
        }else{
          this.films=[]
          this.series=[]
          if(type==='movie'){
            this.isSerie=false
            this.isFilm=true
          }else{
            this.isFilm=false
            this.isSerie=true
          }
          this.getApi(searchTitle,type)
        }
      }
    }
  }
}
        
      
</script>
<style  lang="scss" scoped>
@import '../assets/style/vars.scss';
@import '../assets/style/mixin.scss';
 main {
  min-height:calc(100vh - 80px);
  background-color:$primaryColor;

 }    

</style>