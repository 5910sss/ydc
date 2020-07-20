<template>
  <div class="ydc-release-content">
    <TabPanelRelease :tabs="tabs">
      <template slot="amount">
        <div class="ydc-release-amount">
          <span>
           今日发布数量：<em>0</em>
           /6 <a href="#">发文规范</a>
          </span>
        </div>
      </template>
      <!---->
      <template slot="tab1">
        <form :action="SERVER+'api/publish'" method="post" ref="form1">
          <input type="hidden" name="token" :value="token">
          <div class="ydc-release-form-group">
            <div class="ydc-warning-default">
              <p>标签字数需在11字到30字之间。</p>
            </div>
            <div class="ydc-release-form-group-input">
              <input type="text" name="title" class="ydc-form-control" placeholder="请输入标题，为了更好的展示效果，建议标题字数在30个汉字以内">
              <div class="ydc-form-group-jl">
                <span id="messageCount">0</span>/30
              </div>
            </div>
          </div>
          <!---->
          <div class="ydc-release-form-text">
            <textarea name="content" style="width: 100%">请输入内容</textarea>
          </div>
          <div class="ydc-form-city">
            <div class="aui-card-form-item">
             <label class="aui-card-form-label">分类：</label>
              <div class="aui-card-form-input">
                <select ref="catalog" v-for="(catalog, idx) of catalogs" :key="idx" name="catalogs" @change="catalog_change(idx)">
                  <option value="">===请选择===</option>
                  <option v-for="(item, index) in catalog" :value="item.ID" :key="index">{{item.title}}</option>}
                </select>
                </div>
              </div>
              <div class="aui-card-form-item preview aui-news">
                <label class="aui-card-form-label">封面：</label>
                <div class="aui-file-up-img" id="preview_0">
                <img class="" id="imghead_0" border="0" src="../assets/images/icon/noimg.gif">
                </div>

                <div class="aui-file-up-btn clearfix">
                  <div class="idPicFile aui-btn aui-file-new">
                    <input type="file" name="cover" class=" file_photo aui-file-new-up" style="margin:0;">
                    <a>上传图片</a>
                  </div>
                  <div class="aui-remarks">
                    <p>图片尺寸建议：800*400 图片大小不超过1MB</p>
                  </div>
                </div>
              </div>
              <div class="ydc-btn">
                <button type="button" @click="publish()" class="btn">发布</button>
                <button type="button" class="btn btn-default">保存草稿</button>
            </div>
          </div>
        </form>
      </template>
      <!---->
      <template slot="tab2">
        <div class="ydc-release-form-group ">
            <div class="ydc-warning-default">
                <p>标题字数需在11字到30字之间。</p>
            </div>
            <div class="ydc-release-form-group-input clearfix">
                <label class="ydc-form-group-label">标题</label>
                <input style="width:89.999%" type="text" class="ydc-form-control" title="" placeholder="请输入标题，为了更好的展示效果，建议标题字数在30个汉字以内" >
                <div class="ydc-form-group-jl">
                    <span id="messageCount1">0</span>/30
                </div>
            </div>
            <div class="ydc-release-form-group-input ydc-release-form-group-ms clearfix">
                <label class="ydc-form-group-label">描述</label>
                <input style="width:89.999%" type="text" class="ydc-form-control" title="" placeholder="请输入描述，统一描述" onkeyUp="">
                <div class="ydc-form-group-jl">
                    <span id="">0</span>/30
                </div>
            </div>
            <div class="aui-card-form-item preview  aui-news" style="margin-top:20px;">
                <label class="aui-card-form-label">封面:</label>
                <div class="aui-file-up-img" id="preview_0">
                    <img class="" id="imghead_0" border="0" src="../assets/images/icon/noimg.gif">
                </div>
                <div class="aui-file-up-btn clearfix ">
                    <div class="idPicFile aui-btn aui-file-new">
                        <input type="file" name="file" id="1" class="file_photo aui-file-new-up" style="margin:0;">
                        <a>上传图片</a>
                    </div>
                    <div class="aui-remarks">
                        <p>图片尺寸建议：800*400 图片大小不超过1MB</p>
                    </div>
                </div>
            </div>
            <div class="ydc-btn" style="margin-top:20px;">
                <button class="btn">发布</button>
                <button class="btn btn-default">保存草稿</button>
            </div>
        </div>
      </template>
      <!---->
      <template slot="tab3">
        dassdas
      </template>
    </TabPanelRelease>
  </div>
</template>

<script>
import {SERVER} from '@/config'
import {fetchForm} from '@/lib/fetch.js'
import TabPanelRelease from '@/components/tabPanelRelease.vue'
export default {
  data () {
    return {
      SERVER,
      catalogs: [],
      token: localStorage.token,
      tabs: [{title: '发布文章', slotName: 'tab1'},
        {title: '发布图集', slotName: 'tab2'},
        {title: '测试', slotName: 'tab3'}]
    }
  },
  components: {TabPanelRelease},
  async created () {
    let res = await fetch(SERVER + 'api/catalog/0')
    let catalogs = await res.json()
    this.catalogs = [catalogs]
  },
  methods: {
    async catalog_change (idx) {
      let parentID = this.$refs['catalog'][idx].value
      this.catalogs = this.catalogs.slice(0, idx + 1)

      let res = await fetch(SERVER + 'api/catalog/' + parentID)
      let result = await res.json()

      if (result.length > 0) {
        this.catalogs.push(result)
      }
    },
    async publish () {
      let json = await fetchForm(this.$refs['form1'])
      console.log(json)
    }
  }
}
</script>

<style scoped>
.ydc-release-amount {
    position: absolute;
    right: 0;
    top: 10px;
    font-size: 14px;
    color: #999;
}

.ydc-release-amount a {
    color: #ff5f5f;
    padding-left: 10px;
}

.ydc-release-amount span em {
    color: #ff5f5f;
}

.aui-card-form-label {
    float: left;
    display: block;
    padding: 9px 10px;
    width: 92px;
    font-weight: 400;
    line-height: 20px;
    text-align: left;
    color: #464545;
}

.ydc-warning-default {
    background-color: #fceded;
    font-size: 14px;
    color: #666;
    width: 100%;
    height: 40px;
    line-height: 40px;
    margin-bottom: 20px;
}

.ydc-form-group-jl {
    position: absolute;
    right: 10px;
    top: 10px;
    font-size: 14px;
    color: #999;
}

.ydc-release-form-group-input {
    position: relative;
}

.ydc-warning-default p {
    padding: 0 20px;
    color: #969696;
}

.ydc-form-control {
  width: 100%;
  height: 40px;
  padding: 8px 12px;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 0;
}

.ydc-release-form-group {
    margin-bottom: 20px;
    font-size: 14px;
}

.ydc-release-form-text {
    margin-bottom: 20px;
}

.aui-card-form-label {
    float: left;
    display: block;
    padding: 9px 10px;
    width: 92px;
    font-weight: 400;
    line-height: 20px;
    text-align: left;
    color: #464545;
}

.aui-card-form-input select {
    height: 38px;
    line-height: 38px;
    background-color: #fff;
    border-radius: 2px;
    display: block;
    border: 1px solid #e0e0e0;
    width: 120px;
    float: left;
    margin-right: 10px;
    text-align: center;
}

.aui-card-form-item {
    margin-bottom: 15px;
    clear: both;
}

.aui-card-form-input {
    margin-left: 95px;
    min-height: 36px;
    width: 630px;
    position: relative;
}

.aui-file-up-img {
    padding: 4px;
    line-height: 20px;
    border: 1px solid #ddd;
    overflow: hidden;
    display: inline-block;
    margin-bottom: 10px;
    vertical-align: middle;
    text-align: center;
    cursor: pointer;
    width: 200px;
    height: 152px;
    -webkit-transition: all 0.2s ease-in-out;
    transition: all 0.2s ease-in-out;
    border-radius: 4px;
    -webkit-box-shadow: 0 1px 3px rgba(0, 0, 0, 0.055);
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.055);
}

.aui-file-up-img img {
    width: 100%;
}

.aui-news .aui-file-new-up {
    position: absolute;
    top: 10px;
    right: 0;
    margin: 0;
    opacity: 0;
    filter: alpha(opacity=0);
    -webkit-transform: translate(-300px, 0) scale(4);
    transform: translate(-300px, 0) scale(4);
    font-size: 23px;
    direction: ltr;
    cursor: pointer;
    width: 35px;
    left: 290px;
    height: 10px;
}

.aui-btn {
    float: left;
    position: relative;
    display: inline-block;
    padding: 4px 12px;
    margin-bottom: 0;
    margin-left: .3em;
    font-size: 12px;
    line-height: 20px;
    color: #333333;
    text-align: center;
    cursor: pointer;
    background-color: #f5f5f5;
    background-color: #e6e6e6;
    background-image: linear-gradient(to bottom, #ffffff, #e6e6e6);
    border: 1px solid #cccccc;
    /* border: 0; */
    border-color: #e6e6e6 #e6e6e6 #bfbfbf;
    border-color: rgba(0, 0, 0, 0.1) rgba(0, 0, 0, 0.1) rgba(0, 0, 0, 0.25);
    border-radius: 4px;
}

.aui-file-up-btn {
    padding-left: 94px;
}

.aui-remarks {
    height: 35px;
    line-height: 35px;
    float: left;
    color: #999;
    padding-left: 10px;
}

.ydc-btn {
    padding-left: 75px;
    padding-top: 40px;
}

.clearfix::after {
    clear: both;
    content: ".";
    display: block;
    height: 0;
    visibility: hidden;
}

.ydc-btn button {
    margin-left: 20px;
    width: 140px;
    border-radius: 4px;
    font-size: 14px;
    padding: 8px 20px;
    color: #fff;
    background-color: #ff6464;
    border-color: #ff6464;
    text-decoration: none;
    -webkit-transition: all .2s;
    transition: all .2s;
    line-height: 1.3333333;
    border: 1px solid;
    cursor: pointer;
}

.ydc-btn .btn-default {
    background-color: transparent;
    border-color: #e25050;
    color: #e25050;
    cursor: pointer;
}
.ydc-release-form-group-input{
    margin-bottom: 20px;
}

.ydc-form-group-label {
    width: 90px;
    float: left;
    height: 40px;
    text-align: left;
    padding: 9px 10px;
}
</style>
