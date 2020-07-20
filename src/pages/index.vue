<template>
  <div class="ydc-entered-box">
    <div class="ydc-contect-right">
      <rightHead/>
      <rightBanner/>
      <div class="ydc-loading-box">
        <tabPanel/>
      </div>
    </div>
  </div>
</template>

<script>
import rightHead from '@/components/rightHead.vue'
import rightBanner from '@/components/rightBanner.vue'
import tabPanel from '@/components/tabPanel.vue'
export default {
  components: {
    rightHead, rightBanner, tabPanel
  }
}
</script>

<style>
.ydc-loading-box {
    margin-top: 20px;
    border: 1px solid #ddd;
    /* border-radius: 53px; */
    padding-bottom: 40px;
}
</style>
