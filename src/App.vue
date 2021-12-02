<template>
  <div >
    <Header
    @sendTitle="rideTitle"
    />
    <Main
    :titleType="searchTitleType"
    />
    
  </div>
</template>

<script>
import Header from './components/Header'
import Main from './components/Main'
// import axios from "axios";
export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data(){
    return{
    searchTitleType:{},
    // films:[],
    // urlSearchMovie:'https://api.themoviedb.org/3/search/movie?',
    // apiKey:'f06b44ac869efe8c64e78f6eb1684059',
   }
  },
  methods:{
    rideTitle(searchTitle,type){
      
      this.searchTitleType ={searchTitle,type} ; 
      //  if(this.searchTitle!==''){
      //   this.getApi()
        
       }
     
  },
    // getApi(){
    //   axios.get(`${this.urlSearchMovie}api_key=${this.apiKey}&query=${this.searchTitle}`)
    //   .then((respond)=>{
    //     this.films = respond.data.results
    //   })
    //   .catch((error)=>{
    //     console.log('errore',error)
    //   })
   
    // },
}
        
      
     
 

</script>

<style lang="scss">
@import './assets/style/general.scss';
</style>
