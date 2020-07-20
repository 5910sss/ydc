<template>
  <div class="ydc-tabPanel">
    <div>
      <ul>
        <li v-for="(item, idx) of datas" :key="idx" :class="idx==cur?'hit':''" @click="cur=idx">{{item.title}}</li>
      </ul>
    </div>
    <div class="ydc-panes">
      <div class="ydc-pane" v-for="(item, idx) of datas" :style="{display: idx==cur?'block' : 'none'}" :key='idx'>
        <ol class="ydc-pane-list">
          <li v-for="(data, idx) of item.data" :key="idx">
            <a>{{data.title}}<i v-if="data.isNew">new</i></a>
            <span>{{data.time}}</span>
          </li>
        </ol>
      </div>
    </div>
    <pagination/>
  </div>
</template>

<script>
import pagination from '@/components/pagination.vue'

export default {
  components: {
    pagination
  },
  data () {
    return {
      cur: 0,
      datas: [
        {
          title: '公告栏',
          data: [{id: 2, title: '一点车关于封禁通知（4月13日-4月20日）', isNew: true, href: 'http://www.bing.com', time: 1544537222},
            {id: 4, title: '一点车关于封禁通知（4月13日-4月21日）', isNew: false, href: 'http://www.bing.com', time: 1544537002},
            {id: 8, title: '一点车关于封禁通知（4月13日-4月23日）', isNew: true, href: 'http://www.bing.com', time: 1543537222},
            {id: 15, title: '一点车关于封禁通知（4月13日-4月20日）', isNew: false, href: 'http://www.bing.com', time: 1544536222}]
        },
        {
          title: '一点车资讯',
          data: [{id: 2, title: 'asdfadfgfghfgh', isNew: true, href: ' http://www.bing.com', time: 1544537222},
            {id: 4, title: 'ewyrthdfh-4月20日）', isNew: true, href: 'http://www.bing.com', time: 1544537222},
            {id: 8, title: 'rthdfhdf-4月20日）', isNew: false, href: 'http://www.bing.com', time: 1544537222},
            {id: 15, title: 'fghdfghdf-4月20日）', isNew: false, href: 'http://www.bing.com', time: 1544537222}]
        }
      ]
    }
  }
}
</script>

<style scoped>
.ydc-tabPanel ul {
  height: 44px;
  border-bottom: 1px solid #d0d0d0;
  background: #eaeaea;
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

.ydc-tabPanel .hit{
  color: #fff;
  background: #ff5f5f;
}

.ydc-pane-list li{
  height:45px;
  line-height: 45px;
  padding: 0 20px;
}

.ydc-pane {
  padding: 20px 0;
}

.ydc-pane-list i {
  color: #ff0000;
  font-style: oblique;
}

.ydc-pane-list span{
  float: right;
  color:#999;
}
</style>
