<template>
  <div class="OrderList">
    <el-breadcrumb>
      <el-breadcrumb-item to="/main">首页</el-breadcrumb-item>
      <el-breadcrumb-item>订单管理</el-breadcrumb-item>
      <el-breadcrumb-item>订单列表</el-breadcrumb-item>
    </el-breadcrumb>
    <br>
  <el-table :data="tableData" border style="width: 100%">
    <el-table-column prop="date" label="订单编号"  width="180"> </el-table-column>
    <el-table-column  prop="name" label="开始时间"  width="180"> </el-table-column>
    <el-table-column prop="address"  label="结束时间"> </el-table-column>
    <el-table-column prop="address"  label="用餐人数"> </el-table-column>
    <el-table-column prop="address"  label="桌台编号"> </el-table-column>
    <el-table-column prop="address"  label="菜单详情"> </el-table-column>
  </el-table>
  </div>
</template>
