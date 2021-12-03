<template>
<header>
  <div class="logo">
     <h2>logo</h2>
  </div>
  <div>
    <span>Please make your choise</span>
    <select
     v-model="type"
     @click="$emit('sendTitle',searchTitle,type)"
     name="Please select one" id=""
     >
      <option disabilited value=""></option>
      <option value="all">all</option>
      <option value="movie">movies</option>
      <option value="tv">series</option>
    </select>
    <input 
    v-model="searchTitle"
    @keydown.enter="$emit('sendTitle',searchTitle,type)"
    type="text" 
    placeholder="fai la tua ricerca"
    >
  </div>
</header>
  
</template>

<script>
export default {
  name:'Header',
  data(){
    return{
      searchTitle:'',
      type:''
    }
  },
  
}
</script>

<style lang="scss" scoped>
@import '../assets/style/vars.scss';
@import '../assets/style/mixin.scss';
 header{
   height: 80px;
   background-color:$primaryColor;
   @include display(space-between,center);
   padding:0px 40px;
   border-bottom : 10px solid lighten($primaryColor, 30%);
   .logo{
     color:white;
   }
   div{
    span{
      color:white;
      margin-right:20px
    }
     select{
       width:100px;
       margin-right:20px
     }
   }
 }
</style>