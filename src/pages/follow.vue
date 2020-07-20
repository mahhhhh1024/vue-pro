<template>
  <div class="pages__padding">
    <uc-cell
      v-for="(item,index) of follow"
      :data="item"
      :index="index"
      :key="item._id"
      collectionName="follow"
     />
  </div>
</template>

<script>
  import UcCell from '../components/uc-cell/uc-cell.vue'
  export default {
    name:'follow',
    props:{},
    data(){
      return {
        follow:[],
      }
    },
    components:{
      UcCell
    },
    mounted(){
      axios({
        url:'/api/goods/follow',
        params:{
          _limit:15
        }
      }).then(
        res=>res.data.err === 0 && (this.follow = res.data.data)
      )
    },
    updated(){},
    methods:{}
  }
</script>

<style>
  .follow{
    padding-top: .6rem;
  }
</style>
