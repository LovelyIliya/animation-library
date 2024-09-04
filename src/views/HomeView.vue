<template>
  <div class="home">
    <LuminaCard></LuminaCard>
    <LuminaCard mode="2"></LuminaCard>
  </div>
</template>

<script setup lang="ts">
import LuminaCard from '@/components/LuminaCard/LuminaCard.vue'
</script>
<style lang="scss">
.home {
  display: flex;
  column-gap: 20px;
}
</style>
