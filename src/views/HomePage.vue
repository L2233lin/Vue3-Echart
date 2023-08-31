<script setup></script>

<template>
  <div class="common-layout">
    <el-container>
      <el-header>
        <itemHeader></itemHeader>
      </el-header>
      <el-main>
        <el-row>
          <el-col :span="7">
            <itemLeftBar></itemLeftBar>
            <itemLeftLine></itemLeftLine>
            <itemLeftPie></itemLeftPie>
          </el-col>
          <el-col :span="10" class="itemCenter">
            <itemNo></itemNo>
            <itemMap></itemMap>
          </el-col>
          <el-col :span="7">
            <itemRightBar></itemRightBar>
            <itemRightLine></itemRightLine>
            <itemRightPie></itemRightPie>
          </el-col>
        </el-row>
      </el-main>
    </el-container>
  </div>
</template>

<style lang="less" scoped>
// .common-layout {
//   min-width: 1024px;
//   max-width: 1920px;
// }
.el-header {
  padding: 0;
  height: 5vw;
}

.el-main {
  padding: 10px 10px 0;
}

.itemCenter {
  padding: 0 10px 0;
}
</style>
