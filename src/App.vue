<template>
  <div >
    <Header
    @sendTitle="rideTitle"
    :getTitle="searchTitle"
    />
    <Main/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: {
    Header,
    Main,
  },
  data(){
    return{
   searchTitle:''
   }
  },
  methods:{
    rideTitle(searchTitle){
      this.searchTitle = searchTitle;
      return this.searchTitle
    }
  }
}
</script>

<style lang="scss">
@import './assets/style/general.scss';
</style>
