<template>
  <div class="">
    <h1>添加菜品</h1>
    <el-form label-width='100px'>
      <el-form-item label='菜品图片: '>
        <el-upload :action="uploadAction" :on-success='doUploadSucc' name="dishImg" :show-file-list='false' class='xfn-uploader'>
          <img v-if="imageUrl" :src="imageUrl" alt="">
        </el-upload>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
export default {
  data(){
    return{
      imageUrl:'',  //要显示的预览图片地址
      uploadAction:this.$store.state.globalSettings.apiUrl +'/admin/dish/image', //可处理未见上传的api
      formData:{
        title:'',
        imgUrl:"",
        price:'',            //菜品图片在服务器的文件名称
        detail:'',
        categoryId:''
      }
    }
  },
    methods: {
  doUploadSucc(res,file){
      // 文件上传成功后客户端等到响应消息后的处理函数
      //res:服务端返回的消息
      // file: 从INPUT[type=file]中读取的第一个上传的文件对象
      console.log(res)
      this.form.imgUrl=res.fileName;
      this.imageUrl=URL.createObjectURL(file.raw)
    }
  }
}
</script>

<style lang="scss" >
   .xfn-uploader {
    .el-upload{
      border:1px dotted #aaa;
      border-radius: 3px;
      cursor: pointer;
      width: 250px;
      height: 177px;
      overflow: hidden;
      &:hover{
       border-color: #409EFF; 
      }
    }
    img{
      max-width:100%;
    }
  }
</style>
