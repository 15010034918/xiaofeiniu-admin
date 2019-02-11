<template>
  <div class="xfn-table-add">
    <el-breadcrumb>
      <el-breadcrumb-item to="/main">首页</el-breadcrumb-item>
      <el-breadcrumb-item>桌台管理</el-breadcrumb-item>
      <el-breadcrumb-item>桌台添加</el-breadcrumb-item>
    </el-breadcrumb>
    <br>

    <el-form ref="form" :model="form" label-width="80px">
  <el-form-item label="桌台编号">
    <el-input v-model="form.id"></el-input>
  </el-form-item>
 <el-form-item label="桌台昵称">
    <el-input v-model="form.name"></el-input>
  </el-form-item>
   <el-form-item label="桌台人数">
    <el-select v-model="form.region" placeholder="请选择人数范围">
      <el-option label="4-6人" value="six"></el-option>
      <el-option label="6-8人" value="eight"></el-option>
      <el-option label="8-10人" value="ten"></el-option>
      <el-option label="10-12人" value="twele"></el-option>
    </el-select>
  </el-form-item>
  <el-form-item label="桌台状态">
    <el-checkbox-group v-model="form.type">
      <el-checkbox label="空闲" name="type"></el-checkbox>
      <el-checkbox label="预定" name="type"></el-checkbox>
      <el-checkbox label="占用" name="type"></el-checkbox>
      <el-checkbox label="其他" name="type"></el-checkbox>
    </el-checkbox-group>
  </el-form-item>
  
  
  <el-form-item>
    <el-button type="primary" @click="onSubmit">立即创建</el-button>
    <el-button>取消</el-button>
  </el-form-item>
</el-form>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        form: {
          name: '',
          id:'',
          type: [],
          region: ''   
        }
      }
    },
    methods: {
      onSubmit() {
        console.log('submit!');
      }
    }
  }
</script>