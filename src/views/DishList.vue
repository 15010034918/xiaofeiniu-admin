<template>
  <div class="">
    <h1>菜品列表</h1>
    <el-tabs type='border-card'>
      <el-tab-pane v-for="(c,i) in dishList"  :key="(c.index,i.index)">
        <span slot='label'>
          <el-badge :value="c.dishList.length" class="">{{c.cname}}</el-badge>
        </span>
        <el-row>
          <el-col v-for="(d,j) in c.dishList" :key="(d.index,j.index)" :xs="12" :md="6" :lg="4" :xl='3' style="padding:10px">
            <!-- <xfn-dis h :data='d'></xfn-dish> -->
            <img :src="require('../assets/img/dish/'+d.imgUrl)"  alt="" style='max-width:100%'>
            {{d.title}}
            {{d.price}}元
          </el-col>
        </el-row>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
export default {
  data(){
    return {
      dishList:[]
   }
  },
  mounted(){
    // 异步获取菜品
    var url=this.$store.state.globalSettings.apiUrl + '/admin/dish'
    this.$axios.get(url).then(({data})=>{
      this.dishList=data;
    }).catch((err)=>{
      console.log(err)
    })
  }
}
</script>
