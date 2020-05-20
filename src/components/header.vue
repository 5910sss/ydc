<template>
  <div>
    <div class="ydc-header">
      <div class="ydc-header-content">
        <div class="ydc-column">
          <router-link to="/" class="ydc-column-ydc-logo">
            <img src="../assets/images/icon/ydc-logo.png">
          </router-link>
        </div>
        <div class="ydc-column">
          <div class="ydc-column-user">
            <div class="ydc-user-photo">
              <a href="javascript:;">
                <img src="../assets/images/icon/photo.png">
              </a>
            </div>
            <div class="ydc-user-info">
              <div class="ydc-user-info-name"><a href="javascript:;">一点车</a></div>
              <div class="ydc-user-info-func ydc-flex">
                <span class="ydc-tag">账号审核中</span>
                <span class="ydc-mal">
                  <i class="ydc-icon ydc-icon-mail fl"></i>
                  <em>12</em>
                </span>
                <span class="l"></span>
                <a href="javascript:;">退出</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
</script>

<style scoped>
  .ydc-header{
    height:70px;
    background:#111;
    color:#fff;
    width:100%;
  }
  .ydc-header-content{
    width:1180px;
    height:70px;
    margin: 0 auto;
    display: flex;
  }
  .ydc-column{
    flex:1;
    padding-left: 10px;
    padding-right: 10px;
  }
  .ydc-column-ydc-logo {
    width:100%;
    display: block;
    height:70px;
  }
  .ydc-column-ydc-logo img {
    height:65px;
    line-height: 70px;
    margin-top:5px;
  }
  .ydc-column-user{
    display: flex;
    color:#fff;
    display: flex;
    justify-content: flex-end;
    margin-top:15px;
  }
  .ydc-user-photo {
    width:40px;
    height:40px;
    margin-right:25px;
  }
  .ydc-user-photo img{
    height:40px;
    border-radius: 100%;
    width: 100%;
    display: block;
    height:auto;
  }
  .ydc-user-info a{
    color:#fff;
    font-size:16px;
  }
  .ydc-user-info {
  }
  .ydc-user-info-func {
    display:flex;
  }
  .ydc-user-info-func a{
    font-size:14px;
  }
  .ydc-tag{
    display:inline-block;
    font-size:12px;
    padding:0 8px;
    margin:0 5px;
    height:17px;
    line-height:18px;
    background:#ff6565;
    cursor:pointer;
  }
  .ydc-user-info-func{
    padding-top:4px;
  }
  .ydc-icon{
    width:18px;
    height: 18px;
    display: block;
    background-repeat: no-repeat;
    background-position: center;
    background-size: 18px;
  }
  .ydc-icon-mail{
    background-image:url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADwAAAA8CAYAAAA6/NlyAAADjUlEQVRoQ+2ZTahNURTHf8tnJE+KFMXAwETp9aSU0vOZRz1CTOUVgydlZIIyNUJJBgZ4ikTJV3j5piTJyMxAyoyXfGtpvfau845z7j33dPa59913zvCeffdev/Vfa+219xHG2CNjjJcKuN0VrxSuFG4zD1Qh3WaC/odTKVwp3GYeqEI6LqiqTgUOAPuBmS0q+A/ggdkoIu9q2VhXYVW9CvS2KGjcrDcisiQ3sKrOBj6NElhv5lwR+Zhmc02FVbULeDnKgLtE5FUF7DyQV+FfwEVgFTCv5Aj4ANwHdgKTEtYOonC/iJxU1enAPWBpSdCWXqtFZEhV+4HjZQHvE5ETtpiqTgPuAMsDQxtst4h8deuWCmyL2uLDBU1VpwAPAyodhzXnmpPN2fEnSEjbInHoDuAxsLhgpZ8B6yLKrgRuAubkpCcYsIc2Y8woU9o6safAooKgnwBrReS7m99gbwOTa8wfFNjWNWOskHjoWcCjAqBtPpvXw64BrteBNXuCA6dBm8ELcyqdBHsDmJhhvlKAk6DnuJxuFDoO2wNYP58FtjSFvePj4W3QL4D5GZSxIUmw14AJGf9fOnCS0taJPc/QkdnxbkMkZzcDlxqEbQqwh14mIm9ddV3gwjutDTXY9SLy0423ltX22fENKOuHlpbDUduswPSKyB//o6oa9IWEjuwc0OdhHbA1FIM5G5nSgUfAquoMEfnsQMa5m5MVwHtgwHdr7n10bF7oUoHjsJaHZ11uDu/TaY+q7gDOuK7K7+l5+vTSgJNgL7s8HFG949Cq2gechuHPtzbWipflte/T7USW9XBSCnAc1tQ6Hys6Q8AuEbkSyWsrSkeBgzEnWPGyIpYHOjhwEuyAUyspgm1ftpD9BmwE0i7d8kIHBbYOaLuvxi4Pa8E2usvkgQ4GbLDbROSvyzUL4yJhvXMahQ4CfAvYVAJsFNrWuxspZGkXDkGAt/riEyCM08L+N9ATgd4DnEoYHATYbg13A1uAYzUKVKM5W2+8Qe91523r2pIuD4MA1zOsme8r4Kj3613EdwKpny2aKWONtTtF5HXa+3rAdjP4pYHbhmb7wHK8w5+pk4zJ8rn0MHCk2SQZ1z8kItaqpj51gd2+Z9Wwu8ZdcEZ7gg2zA8dg9KiZK6SDmdfEiTMp3ET7Cl+6Ai7cpS02YaVwiwlSuDmVwoW7tMUmrBRuMUEKN6dSuHCXttiEY07hfzSyy0zsWwJCAAAAAElFTkSuQmCC');
  }
  .ydc-mal {
    height:22px;
    line-height: 18px;
  }
  .ydc-flex{
    margin-left: -10px;
    margin-right: -10px;
  }
  .l {
    height:10px;
    text-align: center;
    margin: 0 8px;
    border-left: 1px solid #707070;
    margin-top:4px;
  }
  /* .ydc-user-info-func a:not(:first-child):before {
      content: " ";
      border-left: 1px solid #707070;
      height: 10px;
      display: inline-block;
      vertical-align: middle;
      margin: 0 8px;
  } */
</style>
