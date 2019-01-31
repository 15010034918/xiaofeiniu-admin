<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
export default {
  mounted(){
    // 当前组件挂载完成后需要异步请求的全局配置信息
    var url=this.$store.state.globalSettings.apiUrl+'/admin/settings';

    this.$axios.get(url).then((res)=>{
      this.$store.commit('setGlobalSettings',res.data);//将全局配置存储到Vuex存储库
    }).catch((err)=>{
      console.log(err)
    })
  }
}
</script>   


<style lang='scss'>
 #app{
   color: #303133;
   font-family: Arial, Helvetica, "Helvetica Neue",sans-serif,"Hiragino Sans GB","PingFang SC",'微软雅黑',"Microsoft";
 }
</style>
