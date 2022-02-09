<template>
  <div class="errPage-container">
    <el-row>
      <el-col :span="12">
        <h1 class="text-jumbo">Oops!</h1>
        <h2>你没有权限去该页面</h2>
        <el-button class="pan-back-btn" @click="back">返回</el-button>
      </el-col>
      <el-col :span="12">
        <img
          :src="errGif"
          width="313"
          height="428"
          alt="Girl has dropped her ice cream."
        />
      </el-col>
    </el-row>
  </div>
</template>

<script setup>
import errGif from '@/assets/401_images/401.gif'
import { getCurrentInstance } from 'vue'

const { proxy } = getCurrentInstance()

const back = () => {
  if (proxy.$route.query.noGoBack) {
    proxy.$router.push({ path: '/dashboard' })
  } else {
    proxy.$router.go(-1)
  }
}
</script>

<style lang="scss" scoped>
.errPage-container {
  width: 800px;
  max-width: 100%;
  margin: 100px auto;
  .pan-back-btn {
    background: #008489;
    color: #fff;
    border: none !important;
  }
  .text-jumbo {
    font-size: 60px;
    font-weight: 700;
    color: #484848;
  }
}
</style>
