<template>
  <div class="ydc-menu">
    <ul>
      <li class="ydc-menu-item" v-for="(item, idx) in menus" :key="idx">
        <router-link v-if="item.type=='link'" :to="item.to">
          <i :class="['ydc-icon', 'fl', item.icon]"></i>
          {{item.title}}
        </router-link>
        <div v-if="item.type=='sub'">
          <span class="ydc-menu-sub-title">
            <i :class="['ydc-icon', 'fl', item.icon]"></i>
            {{item.title}}
          </span>
          <ul>
            <li v-for="(child,idx) in item.children" :key="idx">
              <router-link :to="child.to">{{child.title}}</router-link>
            </li>
          </ul>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default{
  data () {
    return {
      menus: [
        {type: 'link', to: { name: 'index', params: {} }, icon: 'ydc-icon-home', title: '首页'},
        {type: 'link', to: { name: 'release', params: {} }, icon: 'ydc-icon-find', title: '发布'},
        {type: 'sub',
          icon: 'ydc-icon-fine',
          title: '管理',
          children: [
            {to: {name: 'xxx'}, title: '内容管理'},
            {to: {name: 'xxx'}, title: '内容同步'},
            {to: {name: 'xxx'}, title: '素材中心'}
          ]},
        {type: 'sub',
          icon: 'ydc-icon-fine',
          title: '数据',
          children: [
            {to: {name: 'xxx'}, title: '订阅数据'},
            {to: {name: 'xxx'}, title: '内容数据'},
            {to: {name: 'xxx'}, title: '指数星级'}
          ]},
        {type: 'sub',
          icon: 'ydc-icon-fine',
          title: '设计',
          children: [
            {to: {name: 'xxx'}, title: '账号信息'},
            {to: {name: 'xxx'}, title: '账号状态'}
          ]},
        {type: 'sub',
          icon: 'ydc-icon-fine',
          title: '客服',
          children: [
            {to: {name: 'xxx'}, title: '在线咨询'}
          ]}
      ]
    }
  }
}
</script>

<style scoped>
.ydc-menu {
  min-width: 150px;
  min-height: 1300px;
  height: 100%;
  background: #f4f4f4;
  padding: 33px 0 50px;
  color: #333;
  letter-spacing: 1px;
  border-radius: 2px;
}

.ydc-menu .ydc-menu-item a {
  display: block;
  width: 100%;
  padding: 10px 0 10px 68px;
  line-height: 20px;
  position: relative;
  font-size: 14px;
}

.ydc-menu-sub-title{
  padding:10px 0 10px 70px;
  color: #999;
  border-top: 1px solid #ddd;
  margin-top:15px;
  position: relative;
  display: inline-block;
  width:100%;
  line-height: 22px;
  font-size:14px;
}

.ydc-menu .ydc-menu-item a:hover {
    background: #ff6565;
    color: #fff;
}

.ydc-menu .ydc-menu-item .router-link-active {
    background: #ff6565;
    color: #fff;
}
</style>
