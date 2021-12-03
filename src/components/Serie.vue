<template>
  <div class="container" v-if="series !== []">
    <h1>Serie Tv</h1>
    <div class="wrapper">
      <div v-for="(serie,index) in series" :key="index" class="item">
        <div class="flip-card">
          <div class="flip-card-inner">
            <div class="flip-card-front">
             <img v-if="serie.poster_path" :src="`https://image.tmdb.org/t/p/w500/${serie.poster_path}`" alt="Avatar" style="">
             <div else>
               <h2>{{serie.name}}</h2>
               <p>Non sono presenti immagini</p>
             </div>
            </div>
            <div class="flip-card-back">
              <h4>{{serie.name}}</h4>
              <div class="original-title">{{serie.original_name}}</div>
              <div class="lenguage">
                <span>Lingua:</span>
                <span v-if="serie.original_language === 'en'"><img  src="../assets/img/it.png"></span> 
                <span v-else-if="serie.original_language ==='it'"><img  src="../assets/img/en.png"></span> 
                <span v-else>{{serie.original_language}}</span> 
                <div class="vote">
                      Voto :
                      <span v-if="Math.round(serie.vote_average/2)">
                        <i
                        v-for="(star,index) in Math.round(serie.vote_average/2)" :key="index" 
                        class="fas fa-star"
                        >
                        </i>
                        <i
                        v-for="(star,index) in 5-Math.round(serie.vote_average/2)" :key="index" 
                        class="far fa-star"
                        >
                        </i>
                      </span>
                      <span v-else>{{Math.round(serie.vote_average/2)}}</span>  
                   
                </div>
              </div>
            </div>
          </div>
        </div>
        
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
  background-color: darken($primaryColor, 10%);;
  color: rgb(255, 255, 255);
  overflow-y: hidden;
  
  img{
    width: 150px;
  }
  div{
    h2{
    text-align: center;
    padding-top: 40px;
    }
    p{
      color:  lighten($primaryColor, 20%);
      max-width: 50%;
      margin: auto;
      padding-top:40px;
    }
  }


}

.flip-card-back {
  background-color: #000000;
  color: white;
  transform: rotateY(180deg);
  flex-direction: column;
  @include display(center,center)
}
  }
}
</style>
      