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
          icon: 'ydc-icon-file',
          title: '管理',
          children: [
            {to: {name: 'xxx'}, title: '内容管理'},
            {to: {name: 'xxx'}, title: '内容同步'},
            {to: {name: 'xxx'}, title: '素材中心'}
          ]},
        {type: 'sub',
          icon: 'ydc-icon-find',
          title: '数据',
          children: [
            {to: {name: 'xxx'}, title: '订阅数据'},
            {to: {name: 'xxx'}, title: '内容数据'},
            {to: {name: 'xxx'}, title: '指数星级'}
          ]},
        {type: 'sub',
          icon: 'ydc-icon-record',
          title: '设置',
          children: [
            {to: {name: 'xxx'}, title: '账号信息'},
            {to: {name: 'xxx'}, title: '账号状态'}
          ]},
        {type: 'sub',
          icon: 'ydc-icon-customer',
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

.ydc-icon-find{
  margin-right: 8px;
   background-image:url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA8CAYAAAA6/NlyAAAFRUlEQVRoQ+3ba4gbVRQH8POfbPaDfqj4xvpB66Mo4gPxCeKiVgruNvdmGxCkRRAfoIKg0krru7QKIggVQaFKFaUGc08SdautupVSW0GL4AO3KtaiVFuMiuKyTebIyGaZnc28usnMsO183Ln3nvu7Z+4kkzkLOsIOHGFeOgqe6xmPk2EUCoXziOgay7IWishpAE4mIqtHi/R3s9lcUa/XvwobXyl1ORHdCuBMItpn2/ab1Wp1a6d+UcDQWi8VkXUAzgoL3uXze40xC4jI9htXa/0AET1FRDl3GxFZw8wPe/sFgkul0vGHDh3aBOCGLkMiD9dqtU6t1Wq/duqgtV5JROv8BhORpcz8lvu8L1gpdRwR7QZwRuTZdbmhiPzIzM5VNSPDYdjJqVSMMcNRwFBKbQZwY8DqOas+BsD3cpuNX0T+EpGV1Wr1a+84EbFOty+MMReHgguFwlLLssreQCLyGYCnx8fHR0dGRg7MBnS4fWNgSUReZ+ZbwsBOdr8EcL5nUtsbjcai0dHR8cOd7Gz7aa3vIqIXYoxztTHmk0BwsVi8TEQ+9Qy6t6+v76JyufxnjGBdbzo4ODg/n89/TETOnTvwEJFnmfn+0Lu0UupJAKunrQowWKlU3gkLksT5JUuWnJLL5XaEoF82xtxGRBIFXAcw2G4oIgeZ+aQkMB1iONtrA4CPjDEb2+cdtGVZ2wAs7NDHF+u0nfGxpJTaBcD55vL/ISLvMfPiFMDOF55XiGi5iAiAO40xL7XnMTQ0dGIul9vuQQdi/cB7AJztAs+40yWAn8J6Yt0RgA7FdgRrrb937w8ReZWZlyeAbIfww7avuHuZeb0n03cz8xOd9mzoHk4ZHIh1XXXT0HGSMWMPpwiOhJ0tOivgWNhJ9IPGmGfiZDcrezg2VkQ6XtKTDzwfAriEiPa3Wq2BWq32rXtR0s5w17AOSmv9OBE94gJWjTEqK+CuYh2UUmojgGUu4B5jzLlZAHcdO5nh14ho6ulIRL5j5nPSBvcEm1Vwz7BZBPcUmzVwz7FZAieCzQo4MWwWwIli0wYnjk0TnAo2LXBq2DTAqWKTBqeOTRSstV5DRKuiPoz7Pc9G7e/XTmvd+4eHYrF4uoj8QET5KBPuFTaxDBcKhRWWZTkvpEOPXmITAyultgK4Pkzba2yS4H8AHBMETgKbCHh4eHiBbdvOD/e+R1LYRMBKKQXA+GgPiMhqZn4x7HLv1vme36WVUo8CeKw9YRH5CcAuETHMvCmo+qZbSPc4hwseI6KpH746lQ20g2itB23bPra/v39LuVz+vReIOGNqrd8goptdCRhj5mmvVDu9Lt0J4ApXoC3GGN/iljgT6nVb7yeGiOxi5ivdcTuBs/RCPM4aOS/PDwA4wZXhd5n5pjDwWgAPeSINGWPejhM96bZa60VE9L4n7vPGmHsCwVrr64joA3cj52aUz+cvTLuoJWARLaWUUw1wlbuNbdvFarU67VNkxiVdKpX6m82m8914vifAtkajsTjNsqVO4FKplGs2m04p0+2e8/86BbDM/Edghp2TSqllAKaKSFx7YreIrJ2YmNiWVmFaey4DAwN98+bNGwKwCsCl3sUQkeeY+T7v331rLbXWI0QUVMyyX0ScepCelB5GuAc4pcxO+fKMQ0Qatm1fUKvVfokMnnzX+vlkDXKE+JlpMgHg2kqlsrPTjDJfPhxzGX8WkSIzeysJp4bJeoF4JK+I7COiDa1Wa329Xj8Y1CkKuN0/6X8B8Ju3LSK/AXD25zfNZnNHlH8TmEJEWsI51ChOhucE+yh4TqQxAPEf8xwqeYyYkocAAAAASUVORK5CYII=');
}

.ydc-icon-file{
  margin-right: 8px;
  background-image:url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA8CAYAAAA6/NlyAAAEmklEQVRoQ+1aXWgcVRQ+32T9CYtsa1vBH5pQKYoKgih9ERQxL6VQXwwiFElbiRJSMKznzoaqQdNs7t0QFCoatVF8a14UH8RaRX3wSfrmD0ILXaEipMJGqomus0emzpTtspu5s38Nk53X+53vnG/OnTv33nNAm+zBJtNLPcFJz3gvw70MJ+wNWE3pfD6/K5VKDYnIvSJyD4BU3PcgIsurq6sHpqam1uLathO/ruClpaW+YrF4tFKpTAK4vlXHIvKyUuq1VnlasW8oeGFh4bqVlZVPiejxVhzU2P4pInOt8AH4y3Gck9lsttgMT0PBxphjRDRZQ1oSke8BeLbORGQLgPtt8ZY4IaJTqVTq8MTExAVLm8uwuoLz+fxWx3F+BXBjQPZ3pVIZd1333TjkPtafKaVS6SyAnXFto/Ai8guAPcz8WxQ2HK8rWGs9AmCximSamV+yJa3FFQqF/SLycbP2EXZnBgcH9wwPD1vNukaCDYAXQ0eO4+zIZrMXWwnYGHO6Zj14iplPxuGcnZ3dCWAfEb0KYFtoKyLjSqnjNlx1BRtj/Kl7OCD4g5kzNmTrYYwxdxLRz0TUF+CKmUxm9+joaDkutzHmESL6usruC2YesuGxEVxi5q02ZFEYY8w8Eb1QhVPMbKLs6o1rrb8D8KA/5v/jlVK32PB0VbDW+iYiOgdgh01wMTEPM/O3UTZdFewHY4w5SEQnogJrcvyjSqUy4rruSiP7rgsORH9JRI81KSrK7Ew6nX50bGzsUj3gNRFcKBTSnuc9DeD2qOjXGwfQJyL3EdHe6q2viLytlHp+wwhuRWSDBewuIvoKwK3BuOd53t25XO5sLf6aZLjdgn0+rfUBAB+G3CJyUCn1fmIFz8/P95fL5UsAnOBXpZVSbmIFB4vh70R0cyD4hFIq3Dxd0Z2YKd0TLNLLsD8LEjWltdbF8NwtIseVUuNJX7SeFJE3iShNRE8opfwj6VVPojLsK5ubm9ve39+/tqG2lp3YeNhyJi7DUcITJTjYbT0D4Dwzf5bYw0MoTGu9CGAk2GntV0p9kuhFS2vt36bsCgS/rpSqvk66rD1RU1pr/QaAI0TkXwzuY+bPE53h4Lf0ULlcXs7lcucT/w1HrdCJm9KbUnA+nx8EkHZd94fET2ljTJ6IlPz/7HVd91SiFy2t9QUAtwUiF5j5uUQLNsYsE9H2QOQiMx/qCa73YddUD9tWTLNZRVvBNJ1hrfU7AJ4NnLelXNqKEFtbrfXFsG4sMe+0NBFx6KgdBXHboJvFzczMbEulUtVF+zlmvlLUD3kbdQD4R6wPQpCIHFNKHW02mG7Yaa2nALxS5esQM1e3bTQ+PNQ2tYjIPwDGmPm9bgQf10fQk/IWEd0QnJTWPM+7Y3Jy0r+Yv+pp2LaktZ4BkKvBx25biht8HLyI9AHwq4dbauwMMyvrnZYP7FBjWhw9zWK/yWQyQ416R7raetisAhs7EfnXcZzpgYGB6fVamKyaS40xu4nILzA/YOO8WxhfJIAfiegnz/NO16sHW3/D3Qq6236sMtztoDrprye4k293I3D3MrwRstDJGDZdhv8DlW5RW1u+C9EAAAAASUVORK5CYII=');
}

.ydc-icon-record{
  margin-right: 8px;
  background-image:url('data:image/png;base64,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');
}
.ydc-icon-set{
  margin-right: 8px;
  background-image:url('data:image/png;base64,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');
}

.ydc-icon-customer{
  margin-right: 8px;
  background-image:url('data:image/png;base64,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');
}
</style>
