<template>
  <div class="pages__padding">
    <uc-cell
      v-for="(item,index) of column"
      :data="item"
      :key="item._id"
      collectionName="column"
     />
  </div>
</template>

<script>
  import UcCell from '../components/uc-cell/uc-cell.vue'
  export default {
    name:'column',
    props:{},
    data(){
      return {
        column:[],
      }
    },
    components:{UcCell},
    mounted(){
      axios({
        url:'/api/goods/column',
        params:{
          _limit:12
        }
      }).then(
        res=>res.data.err === 0 && (this.column = res.data.data)
      )
    },
    updated(){},
    methods:{}
  }
</script>

<style>
</style>
