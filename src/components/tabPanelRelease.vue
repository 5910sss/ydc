<template>
  <div class="ydc-tabPanel ydc-tabPanel-release">
    <div class="ydc-release-tab-head">
      <ul>
        <li v-for="(item, idx) of tabs" :key="idx" :class="cur==idx?'hit':''" @click="cur=idx">{{item.title}}</li>
      </ul>
      <slot name="amount"/>
    </div>
    <div class="ydc-panes">
      <div v-for="(item, idx) of tabs" class="ydc-pane" :style="{display:cur==idx?'block':'none'}" :key="idx">
        <slot :name="item.slotName"/>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      cur: 0
    }
  },
  props: ['tabs']
}
</script>

<style scoped>
.ydc-release-tab-head {
  position: relative;
}

.ydc-tabPanel ul {
    height: 44px;
    border-bottom: 1px solid #d0d0d0;
    line-height: 44px;
}

.ydc-tabPanel ul li {
    float: left;
    margin: 0 2px 0 0;
    font-size: 14px;
    height: 44px;
    line-height: 45px;
    width: 111px;
    text-align: center;
    cursor: pointer;
}

.ydc-tabPanel-release ul {
    background: none;
    border-bottom: 2px solid #d0d0d0;
}

.ydc-tabPanel-release ul li {
    font-size: 16px;
}

.ydc-tabPanel-release .hit {
    border-bottom: 2px solid #ff5f5f;
    cursor: pointer;
    color: #ff5f5f;
    background: none;
    background: -moz-linear-gradient(top, #e1e1e1, #fff);
    font-size: 16px;
}

.ydc-pane {
    background-color: #fff;
    display: none;
    padding: 20px 0;
}
</style>
