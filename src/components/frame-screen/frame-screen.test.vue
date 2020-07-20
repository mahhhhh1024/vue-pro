<template>
  <div id="app">
    
    <h3>测试 骨架屏</h3>
    
    <frame-screen type="detail" v-if="detail.length==0" />
    <div v-else >数据</div>
    
  </div>
</template>
<script>
  import FrameScreen from './components/frame-screen/frame-screen.vue'
  export default {
    name: 'App',
    data:()=>({
      detail:[]
    }),
    methods:{
      
    },
    mounted(){
     setTimeout(()=>this.detail=['ss'],2000)
    },
    components: {
      FrameScreen
    }
  }
</script>

<style>
</style>
