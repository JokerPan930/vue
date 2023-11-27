<template>
  <div>
    
    <el-container>
      <!-- 侧边栏 -->
      <el-aside style="width: 200px; min-height: 100vh; background-color: #001529;">
        <div style="height: 60px; color: skyblue; display: flex; align-items: center; justify-content: center;"> 
          logo
        </div>
        <el-menu router background-color="#001529" text-color="rgba(255,255,255,0.65)" active-text-color="#fff" style="border: none;" :default-active="$route.path">
          <!-- index路径对应router中的path -->
          <!-- default-active使el-menu-item标签中对应index 的高亮  -->
          <el-menu-item index="/">
            <template slot="title">
              <i class="el-icon-house"></i>
              <span>系统首页</span>
            </template>
          </el-menu-item>
          <el-menu-item index="/1">
            <template slot="title">
              <i class="el-icon-house"></i>
              <span>系统首页</span>
            </template>
          </el-menu-item>
          <el-menu-item index="/2">
            <template slot="title">
              <i class="el-icon-house"></i>
              <span>系统首页</span>
            </template>
          </el-menu-item>
          <el-menu-item index="/element">Element</el-menu-item>
          <el-submenu>
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span>信息管理</span>
            </template>
            <el-menu-item>用户信息</el-menu-item>
            <el-menu-item>管理员信息</el-menu-item>
          </el-submenu>
        </el-menu>
      </el-aside>
      <!-- 右边主体 -->
      <el-container>
          <!-- 右边主体头部区域 -->
          <el-header>
            右边主体头部区域
          </el-header>

          <!-- 主体区域 -->
          <el-main>
            主体区域
          </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>

export default {
  name: 'HomeView',
  
}
</script>
<style>
.el-menu--inline,.el-menu--inline .el-menu-item{
  background-color: #000c17 !important;
}
.el-menu--inline .el-menu-item{
  padding-left: 49px !important; 
}
.el-menu-item:hover,.el-submenu__title:hover{
  color: #fff !important;
}
.el-submenu__title:hover i{
  color: #fff !important;
}
.el-menu-item.is-active{
  background-color: #1890ff !important;
  border-radius: 10px;
  margin: 4px;
}
.el-menu-item{
  margin: 4px;
  height: 40px;
  line-height: 40px;
}
.el-submenu__title{
  margin: 4px;
  height: 40px;
  line-height: 40px;
}


</style>
