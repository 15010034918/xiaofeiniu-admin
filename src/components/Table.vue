<template>
  <div class="xfn-table-info">
    <el-card shadow="hover">
      <div class="xfn-table" :style="{background:getTableColor(data.status)}">{{data.tid}}号桌: {{data.status | tableStatus}}</div>
      <el-button type="success" plain size="mini" @click="showTableDetail">详情</el-button>
      <el-button type="danger" plain size="mini">修改</el-button>
    </el-card>

    <!-- 桌台详情的对话框 -->
    <el-dialog :title="data.tid+'桌台详情'" :visible='dialogTableDetailVisible' :before-close='closeDialogTableDetail'>
      <!-- 对话框主体 -->
      <el-tabs type='border-card' @tab-click='makeQRCode'>
        <el-tab-pane label='桌台状态'>状态加载中</el-tab-pane>
        <el-tab-pane label='桌台二维码'>
          <img :src="qrcodeData" alt="">
        </el-tab-pane>
      </el-tabs>
      <!-- 对话框尾部 -->
      <div slot='footer'>
        <el-button type='primary' @click="dialogTableDetailVisible=false" >确定</el-button>
      </div>
    </el-dialog>
  </div>
</template>

<style lang="scss">
  
</style>

<script>
export default {
    data(){
      return{
        dialogTableDetailVisible:false,
        qrcodeData:''  //二维码base64二进制数据
      }
    },
    props:['data'],
    methods:{
      getTableColor(status){
        if(status==1) return '#67C23A';
        else if(status==2) return '#E6A23C';
        else if(status==3) return '#F56C6C';
        else return '#909399'
      },
      showTableDetail(){
        // console.log(this.data) 当前桌子的数据
        this.dialogTableDetailVisible=true;
      },
      closeDialogTableDetail(){
        this.dialogTableDetailVisible=false;
      },
      makeQRCode(){
        //创建二维码--注意此方法不能再当前的mouted中调用,因为绘图必须的canvas在el-dialog中,对话框在组件家再试并不在DOM树上
        var qrcode=require('qrcode');
        // 每个桌子的URL应该形如:
        // http://127.0.0.1:8092/#/3
        var tableUrl=this.$store.state.appUrl+'/#/'+this.data.tid;
        // 把绘制等到的图片二进制数据转换为字符串编码
        qrcode.toDataURL(tableUrl, {
          width:300,
          errorCorrectionLevel:'H'
        }, (err,url)=>{
          this.qrcodeData=url
        })
      }
    }
}
</script>

