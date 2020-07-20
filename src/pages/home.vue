<template>
  <div class="pages__padding">
    <Banner :data="banner" collectionName="banner" />
    <uc-cell
      v-for="(item,index) of home"
      :data="item"
      :index="index"
      :key="item._id"
      collectionName="home"
     />
  </div>
</template>

<script>
  
  import Banner from '../components/banner/banner.vue'
  import UcCell from '../components/uc-cell/uc-cell.vue'
  // import axios from '../plugins/axios.js';
  export default {
    name:'home',
    props:{},
    data(){
      return {
        home:[],
        banner:[],
        errorMess:''
      }
    },
    components:{Banner,UcCell},
    mounted(){
      // this.$axios({
      axios({
        url:'/api/goods/banner',
        params:{
          _limit:3
        }
      }).then(
        res=>res.data.err === 0 && (this.banner = res.data.data)
      )
      
      axios({
        url:'/api/goods/home',
        params:{
          _limit:20
        }
      }).then(
        res=>res.data.err === 0 && (this.home = res.data.data)
      )
    },
    updated(){},
    methods:{}
  }
</script>

<style>
  .home{}
</style>
