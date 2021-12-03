<template>
  <div class="container " >
    <h1>Film</h1>
     
        <div class="wrapper">
          <div v-for="(film,index) in films" :key="index" class="item">
            <div class="flip-card">
              <div class="flip-card-inner">
                <div class="flip-card-front">
                   <img :src="`https://image.tmdb.org/t/p/w500/${film.poster_path}`" alt="Avatar" style=""> 
                   <div else>
                    <h2>{{film.name}}</h2>
                    <p>Non sono presenti immagini</p>
                  </div>
                </div>
                <div class="flip-card-back">
                  <h4>{{film.title}}</h4>
                    <div class="original-title">{{film.original_title}}</div>
                    <div class="lenguage">
                      <span>Lingua:</span> 
                      <span v-if="film.original_language === 'it'"> <img  src="../assets/img/it.png"></span>      
                      <span v-else-if="film.original_language === 'en'"> <img  src="../assets/img/en.png"></span>      
                      <span v-else>{{film.original_language}}</span> 
                    </div>
                    <div class="vote">Voto : {{Math.round(film.vote_average/2)}}</div>
                </div>
              </div>
            </div>
            
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

}
       
</script>

<style lang="scss" scoped>


@import '../assets/style/vars.scss';
@import '../assets/style/mixin.scss';
.container{
  h1{
    color: white;
    text-align: center;
    padding-top:50px;
  }

  .wrapper{
    @include display();
    overflow:hidden ;
    width: 65%;
    margin: auto;
    .item{
      
      margin:15px;
      color:white; 
      text-align: center;
      
      
      .lenguage,
      .original-title{
        padding:10px 0px;
      }
      .lenguage{
      img{
        width: 30px;
        margin-left:20px;
      }  
      }
     }
.flip-card {
  background-color: transparent;
  width: 150px;
  height: 200px;
  perspective: 1000px;
  
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-card-front {
  background-color: #bbb;
  color: black;
  overflow-y: hidden;
  img{
    width:150px;
  }
}

.flip-card-back {
  background-color: darken($primaryColor, 10%);
  color: white;
  transform: rotateY(180deg);
  flex-direction: column;
  @include display(center,center)
}
}
}
</style>