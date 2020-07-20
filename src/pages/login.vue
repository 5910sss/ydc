<template>
  <form :action="SERVER+'api/login'" ref="form1" method="post">
    <div class="ydc-body-login-box">
      <div class="ydc-user-img">
        <div class="ydc-user-img-img">
          <img src="../assets/images/icon/ph.png">
        </div>
      </div>
        <div class="ydc-user-border">
          <input type="email" name="email" data-type="email" placeholder="请输入邮箱账号">
        </div>
    </div>
    <!---->
    <div class="ydc-body-login-box">
      <div class="ydc-user-img">
        <div class="ydc-user-img-img">
          <img src="../assets/images/icon/pad.png">
        </div>
      </div>
        <div class="ydc-user-border">
          <input type="password" name="password" data-type="password" placeholder="密码">
        </div>
    </div>
    <div class="ydc-bod-aq">
      <p>为了您的账号安全，请勿在公共电脑登录</p>
    </div>
    <div class="clearfix">
      <div class="fl">
        <input type="checkbox" checked="checked">
        <label>十天内免登录</label>
      </div>
      <div class="fr">
        <a href="#">忘记密码</a>
      </div>
    </div>
      <div class="ydc-body-submit">
        <a href="#" @click="login()">登录</a>
      </div>

      <div class="ydc-login-box">
       <router-link :to="{name: 'reg', params: {}}">立即注册</router-link>
       <span>|</span>
       <a href="#">常见问题</a>
      </div>
  </form>
</template>

<script>
import {SERVER} from '@/config'
import {fetchForm} from '../lib/fetch.js'
export default {
  name: 'login',
  data () {
    return {
      SERVER
    }
  },
  methods: {
    async login () {
      let json = await fetchForm(this.$refs['form1'])
      if (json.err) {
        alert(json.msg)
      } else {
        localStorage.token = json.token
        alert('登录成功')
        this.$router.push('/index')
      }
    }
  }
}
</script>

<style scoped>
.ydc-body-login-box {
    z-index: 19;
    position: relative;
    height: 40px;
    margin-bottom: 15px;
    border: 1px solid #c5cddb;
    background: #fff;
    font-size: 12px;
    line-height: 30px;
}

.ydc-user-img {
    float: left;
    text-align: center;
    width: 40px;
    padding: 0 10px;
    height: 40px;
}

.ydc-user-img-img {
    width: 20px;
    height: 38px;
    padding-top: 10px;
}

.ydc-user-img-img img {
    width: 100%;
    height: auto;
    display: block;
    border: none;
}

.ydc-user-border {
    height: 39px;
    /* margin: 2px 0; */
    border-left: 1px solid #bdc4d6;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    float: left;
    width: 77%;
}

.ydc-user-border input {
    padding-left: 10px;
    height: 40px;
    line-height: 40px;
    font-size: 14px;
    font-weight: 400;
    border: none;
    background: none;
    width: 100%;
}

.ydc-bod-aq {
    text-align: left;
    padding-bottom: 20px;
}

.ydc-body-submit {
    margin-top: 16px;
    margin-bottom: 12px;
}

.ydc-body-submit a {
    display: block;
    width: 100%;
    height: 42px;
    cursor: pointer;
    text-align: center;
    color: #fff;
    font-size: 18px;
    line-height: 42px;
    background-color: #ff3c5b;
    color: #fff;
    border-radius: 3px;
}

.clearfix::after {
  clear: both;
  content: ".";
  display: block;
  height: 0;
  visibility: hidden;
}

.ydc-login-box {
    position: absolute;
    left: 50%;
    bottom: 30px;
    -webkit-transform: translate(-50%);
    transform: translate(-50%);
    font-size: 12px;
}

.ydc-login-box a {
    padding: 10px;
    color: #999;
}
</style>
