<template>
  <div>
    <!-- head YDC begin -->
    <header class="ydc-header">
      <div class="ydc-entered">
        <div class="ydc-header-content ydc-flex">
          <div class="ydc-column">
            <a href="#" class="ydc-column-ydc-logo">
              <img src="../assets/images/icon/ydc-logo.png">
            </a>
          </div>
          <div class="ydc-column">
            <div class="ydc-column-user">
              <div class="ydc-user-photo">
              </div>
              <div class="ydc-user-info">
                <div class="ydc-user-info-name"></div>
                <div class="ydc-user-info-func ydc-flex">
                  <a href="javascript:;">退出</a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </header>
    <!-- head YDC end -->
    <!-- content YDC begin -->
    <section>
      <div class="ydc-content-slide ydc-body">
        <div class="ydc-page-content" style="overflow:hidden">
          <div class="ydc-reg-title">
            <ul class="clearfix">
              <li v-for="(item, idx) of steps" :class="['ydc-reg-step', idx<=cur_step?'active': '']" :key="idx">
               <em></em>
               <h3>{{item}}</h3>
              </li>
            </ul>
          </div>
          <div class="ydc-reg-form clearfix">
            <form action="" v-if="cur_step==0">
              <div class="ydc-reg-form-group clearfix">
                <label>邮箱账号：</label>
                <div class="ydc-reg-form-input">
                  <input type="text" class="ydc-form-control" name="username" placeholder="账号通行证/邮箱">
                </div>
                <div class="ydc-reg-form-text">
                  <p>请填写账号邮箱，作为登录账号。<br>
                    没有邮箱账号？<a href="javascript:;" @click="cur_step++">立即注册</a></p>
                </div>
              </div>
              <div class="ydc-reg-form-group clearfix">
                <label>密码：</label>
                <div class="ydc-reg-form-input">
                  <input type="password" id="psd" name="username" class="ydc-form-control" autocomplete="off" placeholder="密码">
                </div>
                <div class="ydc-reg-form-text">
                  <p><a href="javascript:;">忘记密码？</a></p>
                </div>
              </div>
              <div class="ydc-reg-form-group">
                <div class="ydc-reg-form-button">
                  <a class="btn" type="submit" href="#">登录</a>
                </div>
              </div>
            </form>
            <!--cur_step==1-->
            <form action="" v-if="cur_step==1">
              <div class="ydc-reg-form-class">
                <div class="ydc-reg-text-center">
                  <div class="ydc-text-center-item" v-for="(item, idx) of types" :key="idx">
                    <div class="ydc-text-item-list">
                      <div class="ydc-text-item-list-title">
                        <div class="ydc-text-ab">
                          <label :class="['rdobox', account_type==idx?'checked': '']" @click="account_type=idx">
                            <span :class="account_type==idx?'checked-image':'check-image'"></span>
                            <span class="radiobox-content"></span>
                          </label>
                        </div>
                        <div class="ydc-text-item-list-mt1">
                          <img :src="item.icon">
                        </div>
                      </div>
                      <div class="ydc-text-item-list-text">
                        <h2>{{item.title}}</h2>
                        <p>{{item.desc}}</p>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="ydc-reg-form-group">
                <div class="ydc-reg-form-button clearfix">
                  <a class="btn" href="#" @click="toStep3()">下一步</a>
                </div>
              </div>
            </form>

            <form :action="SERVER+'api/reg'" v-if="cur_step==2" ref="form3" method="post" enctype="multipart/form-data">
              <input type="hidden" name="type" v-model="account_type">
              <div class="ydc-reg-form-class ydc-reg-form-reg">
                <div class="ydc-reg-form-group clearfix">
                  <label>账号名称：</label>
                  <div class="ydc-reg-form-input">
                    <input type="text" id="loginEmail" name="display_name" class="ydc-form-control" autocomplete="off" placeholder="" style="width:200px;" value="blue">
                    <div class="ydc-reg-form-text">
                      <p>请输入2至14字的帐号名称</p>
                    </div>
                  </div>
                </div>
                <!--1-->
                <div class="ydc-reg-form-group clearfix">
                  <label>密码：</label>
                  <div class="ydc-reg-form-input">
                    <input type="password" name="password" class="ydc-form-control" autocomplete="off" placeholder="" style="width:200px;" value="123456">
                    <div class="ydc-reg-form-text">
                      <p>请输入2至14字的账号密码</p>
                    </div>
                  </div>
                </div>
                <!--2-->
                <div class="ydc-reg-form-group clearfix">
                  <label>账号简介：</label>
                  <div class="ydc-reg-form-input">
                    <input type="text" id="psd" name="slogan" class="ydc-form-control" autocomplete="off" placeholder="" value="aaa">
                    <div class="ydc-reg-form-text">
                      <p>请输入2至14字的账号简介</p>
                    </div>
                  </div>
                </div>
                <!--3-->
                <div class="ydc-reg-form-group clearfix">
                  <label>账号分类：</label>
                  <div class="ydc-reg-form-input">
                    <select name="catalog">
                      <option v-for="(item, idx) of catalogs" :value="idx" :key="idx">{{item}}</option>
                    </select>
                  </div>
                  <div class="ydc-reg-form-text">
                    <p>请选择账号分类</p>
                  </div>
                </div>
                <!--3.1-->
                <div class="ydc-reg-form-group clearfix">
                  <label>帐号图标:</label>
                  <div class="ydc-reg-form-input">
                    <input type="file" id="" name="icon" class="" autocomplete="off" placeholder="">
                    <div class="ydc-reg-form-text">
                      <p>选取至少160*160尺寸的图片。请勿上传二维码或其他推广性质图片作为图标。</p>
                    </div>
                  </div>
                </div>
                <!--4-->
                <div class="ydc-reg-form-group clearfix">
                  <label>账号描述：</label>
                  <div class="ydc-reg-form-input ydc-reg-form-input-width">
                  <textarea name="description">请详细描述你的账号，30字至120字</textarea>
                  <div class="ydc-reg-form-text">
                    <p>请填写你的账号描述</p>
                  </div>
                  </div>
                </div>
                <!--5-->
                <div class="ydc-reg-form-group clearfix">
                  <label>已有内容渠道及连接：</label>
                  <div class="ydc-reg-form-input ydc-reg-form-input-width">
                  <textarea name="other_channels">请详细描述你的账号</textarea>
                  <div class="ydc-reg-form-text">
                    <p>例如已发布文章的网站地址、博客地址、微信号等，方便我们作为参考</p>
                  </div>
                  </div>
                </div>
                <!--6-->
                <div class="ydc-reg-form-group clearfix">
                  <label>姓名：</label>
                  <div class="ydc-reg-form-input">
                    <input type="text" id="user1" name="name" value="blue" class="ydc-form-control" autocomplete="off" placeholder="">
                  </div>
                </div>
                <!--7-->
                <div class="ydc-reg-form-group clearfix">
                  <label>身份证号：</label>
                  <div class="ydc-reg-form-input clearfix">
                    <input type="text" id="user2" name="identify_number" class="ydc-form-control" autocomplete="off" placeholder="" value="11111">
                    <div class="ydc-reg-form-text">
                      <p>账号信息填写需真是有效，如发现虚假以及非个人真是信息导致账号收益无法提取，责任由账号个人承担</p>
                    </div>
                    <div class="ydc-warning-default fl" style="height:auto; font-size:12px">
                      <p>提交本页信息后，使用当前账号登录客户端3.0版本<br>点击「我的」 - 「实名认证」进行姓名认证。 </p>
                    </div>
                  </div>
                </div>
                <!--8-->
                <div class="ydc-reg-form-group clearfix">
                  <label>所在城市</label>
                  <div class="ydc-reg-form-input">
                    <select v-model="cur_pro" name="province">
                      <option v-for="(item, idx) of province" :value="item.ID" :key="idx">{{item.name}}</option>
                    </select>
                    <select v-model="cur_city" v-if="city" name="city">
                      <option v-for="(item, idx) of city" :value="item.ID" :key="idx">{{item.name}}</option>
                    </select>
                  </div>
                </div>
                <!--9-->
                <div class="ydc-reg-form-group clearfix">
                  <label>联系手机：</label>
                  <div class="ydc-reg-form-input">
                    <input type="text" id="user4" name="" class="ydc-form-control" autocomplete="off" placeholder="">
                    <div class="ydc-reg-form-text">
                      <p>请输入手机号并验证</p>
                    </div>
                  </div>
                  <div class="ydc-reg-yzm">
                    <button>获取验证码</button>
                  </div>
                </div>
                <div class="ydc-reg-form-group clearfix">
                  <label>邮箱：</label>
                  <div class="ydc-reg-form-input">
                    <input type="text" id="user5" name="email" value="blue@124.com" class="ydc-form-control" autocomplete="" placeholder="">
                  </div>
                  <div class="ydc-reg-form-text">
                    <p>请使用自己日常使用邮箱便于接受相关信息</p>
                  </div>
                </div>
                <!--10-->
                <div class="ydc-reg-form-group clearfix">
                  <label>QQ/微信号：</label>
                  <div class="ydc-reg-form-input">
                    <input type="text" id="user6" name="qq_wx" value="8888" class="ydc-form-control" autocomplate="off" placeholder="">
                  </div>
                  <div class="ydc-reg-form-text">
                  <p>请输入常用QQ/微信号方便联系沟通</p>
                  </div>
                </div>
                <!--12-->
                <div class="ydc-reg-form-group clearfix">
                  <label>推荐人:</label>
                  <div class="ydc-reg-form-input">
                    <input type="text" id="user7" name="recommend_code" class="ydc-form-control" autocomplete="off" placeholder="">
                  </div>
                  <div class="ydc-reg-form-text">
                    <p>选填，若有网易员工推荐您入驻，请填写相应推荐码。</p>
                  </div>
                </div>
                <!--11-->
                <div class="ydc-reg-form-group clearfix">
                  <label></label>
                  <div class="ydc-reg-form-input ydc-reg-form-input-agreement">
                    <label><input type="checkbox" value="yes" id="agreement" checked="">我已经阅读并同意 <a href="#">《车讯号媒体开放平台注册协议》</a>。</label>
                  </div>
                </div>
              </div>
                <div class="ydc-reg-form-group">
                  <div class="ydc-reg-form-button" style="margin-left:255px;">
                  <a class="btn btn-border fl" href="#" @click="cur_step--">上一步</a>
                  <a class="btn fl" href="#" @click="submit_form()">提交申请</a>
                  </div>
                </div>
            </form>
          </div>
          <!---->
          <div class="ydc-right-banner" style="margin-top:80px;">
            <div class="slideshow-container">
              <a href="https://xihazahuopu.taobao.com/" target="_blank" class="mySlides fade; display:block">
                <img src="../assets/images/ad/ad1.jpg" style="width:100%;">
              </a>
              <a href="https://weibo.com/525135676" target="_blank" class="mySlides fad; display:blocke">
                <img src="../assets/images/ad/ad2.jpg" style="width:100%; display:none;">
              </a>
              <a href="http://www.a-ui.cn/" target="_blank" class="mySlides fade; display:block">
                <img src="../assets/images/ad/ad3.jpg" style="width:100%; display:none;">
              </a>
            </div>
          </div>
        </div>
      </div>
      <div class="ydc-footer">
        <div>
          <p>©2018 一点车版权所有About 公司简介  联系方法  招聘信息  客户服务  隐私政策  广告服务  网站地图  意见反馈  不良信息举报</p>
        </div>
      </div>
    </section>
    <!-- content YDC end -->
  </div>
</template>

<script>
import {SERVER} from '@/config.js'
import mt1 from '../assets/images/icon/mt1.png'
import mt2 from '../assets/images/icon/mt2.png'
import mt3 from '../assets/images/icon/mt3.png'
import mt4 from '../assets/images/icon/mt4.png'
import {fetchForm} from '@/lib/fetch.js'
export default {
  name: 'reg',
  data () {
    return {
      catalogs: [],
      SERVER,
      province: [],
      cur_pro: 0,
      cur_step: 0,
      city: null,
      cur_city: 1,
      steps: ['登录邮箱账号', '选择账号类别', '填写媒体信息'],
      account_type: -1,
      types: [{icon: mt1, title: '媒体', desc: '适合报纸、杂志、电视台、网站等以内容生产为主，有国家新闻出版广电总局认可资质的媒体机构申请。'},
        {icon: mt2, title: '自媒体', desc: '适合垂直领域专家、意见领袖、评论家等个人创作者或以内容生产为主的自媒体公司/机构申请。'},
        {icon: mt3, title: '组织机构', desc: '适合党政机关、事业单位和各类公共场馆、公益机构、学校/培训机构、民间组织等申请。'},
        {icon: mt4, title: '企业', desc: '适合企业、公司及其分支机构、旗下品牌等申请，品牌宣传，主要用于商业品牌推广等申请。'}]
    }
  },
  methods: {
    toStep3 () {
      if (this.account_type === -1) {
        alert('请选择账户类型')
      } else {
        this.cur_step++
      }
    },
    async submit_form () {
      let json = await fetchForm(this.$refs['form3'])

      console.log(json)
    }
  },
  async created () {
    {
      let res = await fetch(SERVER + 'api/account_catalog')
      let arr = await res.json()
      this.catalogs = arr
    }
    //  省份
    {
      let res = await fetch(SERVER + 'api/get_province')
      let arr = await res.json()
      this.province = arr
      this.cur_pro = this.province[0].ID
    }
    //  城市
    {
      let res = await fetch(SERVER + `api/get_city/${this.province[0].ID}`)
      let arr = await res.json()
      this.city = arr
    }
  },
  watch: {
    async cur_pro () {
      let res = await fetch(SERVER + `api/get_city/${this.cur_pro}`)
      let arr = await res.json()
      this.city = arr
      this.cur_city = arr[0].ID
    }
  }
}
</script>

<style scoped>
.ydc-entered {
  background-color:#2b2b2b;
}

.ydc-header-content {
  margin: 0 auto;
  width: 1180px;
  height: 70px;
}
.ydc-flex {
  display: flex;
}
.ydc-column {
  flex: 1 1 0%;
}

.ydc-column {
    -ms-flex: 1 1 0px;
    -webkit-box-flex: 1;
    flex: 1 1 0%;
    padding-left: 10px;
    padding-right: 10px;
    position: relative;
    max-width: 100%;
}

.ydc-column-ydc-logo {
    width: 130px;
    display: block;
    margin-top: 5px;
}

.ydc-column-ydc-logo img {
    width: 100%;
    height: auto;
    display: block;
    border: none;
}

.ydc-column-user {
  display: flex;
  color: #fff;
  margin-top: 15px;
  justify-content: flex-end;
}

.ydc-user-photo {
    width: 40px;
    height: 40px;
    margin-right: 25px;
}

.ydc-user-info {
  display: flex;
  justify-content: space-between;
  flex-direction: column;
}

.ydc-user-info-func {
    padding-top: 4px;
}

.ydc-user-info-func a {
  color:#fff;
  position: relative;
}

/**/
.ydc-content-slide {
  position: relative;
  width: 1180px;
  margin: 20px auto;
}

.ydc-page-content {
  background: #f4f4f4;
  min-height: 100%;
  width: 1000px;
  margin: 0 auto;
  padding: 40px 50px;
}

.ydc-reg-title {
  padding:40px 0;
}

.ydc-reg-title ul {
  width: 600px;
  margin: 0 auto;
}

.clearfix::after {
  clear: both;
  content: '.';
  display: block;
  height: 0;
  visibility: hidden;
}

.ydc-reg-title ul li {
    float: left;
    color: rgba(226,80,80,.3);
    position: relative;
    -webkit-transition: all 2s ease;
    transition: all 2s ease;
}

.ydc-reg-title ul li em {
    width: 30px;
    height: 30px;
    border-radius: 50%;
    display: block;
    margin: 0 auto;
    z-index: 99;
    position: relative;
    border: 5px solid #f4f4f4;
}

.ydc-reg-title ul li h3 {
    margin: 10px 0;
}

.ydc-reg-title ul li+li::before {
  content: "";
  position: absolute;
  height:15px;
  width:245px;
  top: 8px;
  background-color: #ffcacb;
  left: -190px;
  z-index:90;
}

.ydc-reg-title li.ydc-reg-step.active::before {
    background-color: rgba(226,80,80,.6);
}

.ydc-reg-step+li {
    margin-left: 135px;
}

.ydc-reg-title li.ydc-reg-step.active em {
    background-color: #ff6a81;
}

.ydc-reg-title li.ydc-reg-step em {
    background-color: rgba(226,80,80,.6);
}
.ydc-reg-title li.ydc-reg-step.active h3 {
    color: #ff6a81;
}
/*account_step==0*/
.ydc-reg-form-group{
  margin-bottom: 30px;
  padding: 0 10px;
  margin-left: -15px;
  margin-right: -15px;
}

.ydc-reg-form-group label {
    padding-right: 5px;
    font-size: 16px;
    color: #333;
    text-align: right;
    white-space: nowrap;
    width: 255px;
    float: left;
    margin-bottom: 0;
    padding-top: 9px;
    padding-left: 10px;
}

.ydc-reg-form-input {
    width: 350px;
    white-space: nowrap;
    float: left;
    padding-left: 15px;
    padding-right: 15px;
    position: relative;
    min-height: 1px;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
}

.ydc-reg-form-text {
    white-space: nowrap;
    /* width: 25%; */
    position: relative;
    min-height: 1px;
    /* padding-left: 15px; */
    padding-right: 15px;
    float: left;
}

.ydc-reg-form-input .ydc-form-control {
    width: 100%;
    height: 38px;
    padding: 8px 12px;
    background-color: #fff;
    border: 1px solid #ccc;
    box-shadow: none;
    height: 40px;
    font-size: 12px;
    color: #333;
}

.ydc-reg-form-text p a {
    color: #29adeb;
}

.ydc-reg-form-text p {
    margin: 0 0 10px;
    padding-bottom: 9px;
    margin-bottom: 0;
    font-size: 12px;
    padding-top: 0;
    color: #a1a1a1;
}

.ydc-reg-form-group {
    margin-bottom: 30px;
    padding: 0 10px;
    margin-left: -15px;
    margin-right: -15px;
}

.ydc-reg-form-button {
    margin-left: 355px;
    /* width: 83.33333333%; */
    float: left;
    position: relative;
    min-height: 1px;
    padding-left: 15px;
    padding-right: 15px;
}

.ydc-reg-form-button a {
    color: #fff;
    background-color: #ff6980;
    border-color: #ff6980;
    font-size: 14px;
    width: 101px;
    display: block;
    -webkit-box-sizing: content-box;
    box-sizing: content-box;
    -webkit-transition: all .2s;
    transition: all .2s;
    padding: 10px 12px;
    border-radius: 3px;
}

.btn {
    position: relative;
    text-align: center;
    line-height: 1;
    cursor: pointer;
    transition: all .2s ease-out;
    border: 1px solid transparent;
    margin: 0;
    background-color: #f2f2f2;
    border-color: #d7dde4;
    color: #324050;
    outline: 0;
}

/*account_step==1*/
.ydc-reg-text-center {
    text-align: center;
}

.ydc-text-center-item {
    width: 174px;
    text-align: center;
    vertical-align: top;
    padding: 0;
    margin: 0 15px 30px;
    display: inline-block;
}

.ydc-text-item-list {
    position: relative;
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
}

.ydc-text-item-list-title {
    padding-top: 20px;
    position: relative;
}

.ydc-text-ab {
    width: 100%;
    position: absolute;
}

.checked {
    color: #fff;
}

.checked-image {
    display: inline-block;
    width: 26px;
    height: 26px;
    margin-top: 46px;
    background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA8CAYAAAA6/NlyAAAAGXRFW…WtMR/6/qt4DEskDL5+VwAJvIpHXtJu7tGdVetVvP8EGACs39rtbiHKJAAAAABJRU5ErkJggg==);
    vertical-align: middle;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    margin-left: 70px;
}

.ydc-text-item-list:hover{
    background:#fbe4e6;
}

.rdobox, .chkbox {
    display: inline-block;
    padding: 10px;
    height: 86px;
    line-height: 16px;
    /* background: #eee; */
    border-radius: 3px;
    width: 100%;
    color: #666;
}

.check-image {
  display: inline-block;
  width: 26px;
  height: 26px;
  margin-top: 46px;
  background-image: url("../assets/images/icon/input-unchecked.png");
  vertical-align: middle;
  background-size: cover;
  background-position:center;
  background-repeat:no-repeat;
  margin-left: 70px;
}

.checked-image {
  display: inline-block;
  width: 26px;
  height: 26px;
  margin-top: 46px;
  background-image: url("../assets/images/icon/input-checked.png");
  vertical-align: middle;
  background-size: cover;
  background-position:center;
  background-repeat:no-repeat;
  margin-left: 70px;
}

.ydc-text-item-list-mt1 {
    width: 80px;
    height: 80px;
    margin: 0 auto;
}

.ydc-text-item-list-mt1 img {
    width: 100%;
    height: auto;
    display: block;
    border: none;
}

.ydc-text-item-list-text h2 {
    width: 100%;
    font-size: 16px;
    color: #636363;
    padding-top: 20px;
}

.ydc-text-item-list-text p {
    margin-top: 15px;
    color: #a1a1a1;
    font-size: 12px;
    padding: 0 10px 20px 10px;
}

/*cur_step==2*/
.ydc-reg-form-group {
    margin-bottom: 30px;
    padding: 0 10px;
    margin-left: -15px;
    margin-right: -15px;
}

.ydc-reg-form-group label {
    padding-right: 5px;
    font-size: 16px;
    color: #333;
    text-align: right;
    white-space: nowrap;
    width: 255px;
    float: left;
    margin-bottom: 0;
    padding-top: 9px;
    padding-left: 10px;
}

.ydc-reg-form-input {
    width: 350px;
    white-space: nowrap;
    float: left;
    padding-left: 15px;
    padding-right: 15px;
    position: relative;
    min-height: 1px;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
}

.ydc-reg-form-reg .ydc-reg-form-text p {
    height: 40px;
    line-height: 40px;
    font-size: 12px;
}

.ydc-reg-form-reg .ydc-reg-form-input select {
    height: 42px;
    line-height: 42px;
    width: 100px;
    border-radius: 0;
    border: 1px solid #ccc;
}

.ydc-reg-form-text {
    white-space: nowrap;
    /* width: 25%; */
    position: relative;
    min-height: 1px;
    /* padding-left: 15px; */
    padding-right: 15px;
    float: left;
}

.ydc-reg-form-input-width {
    width: 510px;
}

.ydc-reg-form-input textarea {
    width: 480px;
    border: 1px solid #ccc;
    padding: 10px;
    height: 160px;
    background: #fff;
}

.ydc-warning-default {
    display: block;
    background-color: #fceded;
    font-size: 14px;
    color: #666;
    width: 100%;
    height: 40px;
    line-height: 40px;
    margin-bottom: 20px;
}

.ydc-warning-default p {
    padding: 0 20px;
    color: #969696;
}

.ydc-reg-yzm button {
    background: #ff6464;
    border: none;
    font-size: 13px;
    padding: 11px 16px;
    color: #fff;
    border-radius: 3px;
}

.ydc-reg-form-input-agreement label {
    font-size: 12px;
    padding-left: 0;
    padding-right: 5px;
}

.ydc-reg-form-input-agreement label a {
    color: #ff6464;
}

.ydc-reg-form-button .btn-border {
    background-color: #fff;
    color: #ff6980;
    margin-right: 20px;
}

.ydc-reg-form-button a {
    color: #fff;
    background-color: #ff6980;
    border-color: #ff6980;
    font-size: 14px;
    width: 101px;
    display: block;
    padding: 10px 12px;
    border-radius: 3px;
}

.btn-border:hover {
  background:#ff6980;
}

/*footer*/
.ydc-footer {
    width: 900px;
    margin: 0 auto;
    text-align: center;
    padding: 20px 0;
}
</style>
