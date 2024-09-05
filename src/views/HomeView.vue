<template>
  <div class="home">
    <div class="item">
      <LuminaCard></LuminaCard>
      <p>透明流光卡片-模式1</p>
    </div>
    <div class="item">
      <LuminaCard mode="2"></LuminaCard>
      <p>透明流光卡片-模式2</p>
    </div>
    <div class="item" style="padding-top: 30px">
      <div class="mnv-box">
        <MagicNavBtn ref="MagicNavBtnRef" text="导航按钮"></MagicNavBtn>
      </div>
      <div class="btn-box">
        <button @click="playMagicNavBtn" class="btn">播放</button>
        <button @click="hideMagicNavBtn" class="btn">隐藏</button>
      </div>
      <p>导航按钮</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import LuminaCard from '@/components/LuminaCard/LuminaCard.vue'
import MagicNavBtn from '@/components/MagicNavBtn/MagicNavBtn.vue'

const MagicNavBtnRef = ref()
function playMagicNavBtn() {
  MagicNavBtnRef.value.play()
}
onMounted(() => {
  playMagicNavBtn()
})
function hideMagicNavBtn() {
  MagicNavBtnRef.value.hide()
}
</script>
<style lang="scss">
.home {
  display: flex;
  height: 100vh;
  padding: 20px;
  column-gap: 20px;
  row-gap: 20px;
  .item p {
    text-align: center;
    margin-top: 10px;
  }
}
.btn-box {
  margin-top: 60px;
  text-align: center;
}
.mnv-box {
  width: 400px;
  height: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.btn {
  display: inline-block;
  padding: 5px 10px;
  background: #fff;
  border-radius: 4px;
  cursor: pointer;
  margin: 10px;
}
</style>
