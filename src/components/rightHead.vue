<template>
  <div class="ydc-right-head">
    <div class="ydc-right-head-info">
      <dl>
        <a href="#">
          <dt>总订阅</dt>
          <dd>14</dd>
        </a>
      </dl>
      <dl>
        <a href="#">
          <dt>总阅读</dt>
          <dd>24</dd>
        </a>
      </dl>
      <dl>
        <a href="#">
          <dt>昨日阅读</dt>
          <dd>14</dd>
        </a>
      </dl>
      <dl>
        <a href="#">
          <dt>总数据指数</dt>
          <dd>158</dd>
        </a>
      </dl>
    </div>
    <button class="btn ydc-ne-carousel" @click="$router.push({name:'release', params: {}})">
      <i class="ydc-icon-shu"></i>
      <span>发布</span>
    </button>
  </div>
</template>

<script>
export default {
}
</script>

<style scoped>
.ydc-right-head {
    display: -webkit-flex;
    display: -ms-flexbox;
    display: flex;
    -webkit-flex-direction: row;
    -ms-flex-direction: row;
    flex-direction: row;
}

.ydc-right-head-info {
    display: -webkit-flex;
    display: -ms-flexbox;
    display: flex;
    height: 140px;
    -webkit-flex: 1 1 780px;
    -ms-flex: 1 1 780px;
    flex: 1 1 780px;
    -webkit-align-items: center;
    -ms-flex-align: center;
    align-items: center;
    text-align: center;
    font-weight: 700;
    background-color: #f4f4f4;
    border-radius: 3px;
}

.ydc-right-head-info dl {
  flex: 1 1 0%
}

.ydc-right-head-info dl dt {
    color: #757575;
    line-height: 22px;
    font-size:  14px;
    font-weight: 200;
}

.ydc-right-head-info dl dd {
    margin: 8px 0 0;
    font-size: 26px;
    line-height: 37px;
    font-weight: 700;
}

.ydc-right-head-info dl a:hover {
    color: #ff5f5f;
}

.ydc-ne-carousel {
    padding: 8px 12px;
    font-size: 14px;
    min-width: 32px;
    background-color: #ff6565;
    border-color: #ff6565;
    border: 3px;
    color: #fff;
    width: 130px;
    height: 140px;
    margin-left: 20px;
    font-weight: normal;
}

.ydc-ne-carousel span {
    font-weight: 300;
}

.ydc-right-head-info dl+dl:before {
  content: " ";
  float:left;
  width:1px;
  height: 50px;
  margin-top: 8px;
  border-left: 1px solid #ddd;
}

.ydc-icon-shu{
  background-image:url('data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGQAAABkCAYAAABw4pVUAAAFd0lEQVR4Xu3dvcsdRRQG8OcBUQvRiKWVnZ1io4IISiSIH4UhmlQxEIhooTa2xr9ACxVMYQIiBlEUNQaNGBEhiqBgYyP4hSAiKkH81iPndS9uNnvvztfOzu6cLd93du7c87sze2bu3h3CjqIiwKJaY42BgRT2ITAQAyksAoU1x3qIgRQWgYHmiMglAO4HcH1T9AcALwF4luQ/qd+N9ZANERWR/QAeBXBBT7F3AdxG8nRKFANZE00ReQLAvQPB/lh7DsmfU6EYSE8kReQ+AI87BvkDANtToRhIJ+oicjeAw44Yq2KKciPJXzzPO6u4gbRCEoixquE9ADtiUQykCWckRhvlJpK/hfYUAwGQCGNl8DaAW0JRqgcRkW0AvgBwUeinuuc8RbmZ5B++dVYPogETkSsBvJMY5Q0At/uiVAsiIteR1Avx1jEiyq0k/3LtKVWCiMhOAEcBvApgF8m/R0R5BcBOV5TqQFoY5zSfWl2XyoFyxwp+U2+pCqQHYxWbHCgvANg9hFINyAaM3Ch3bVolrgLEASMnyiGSB9YNW4sH8cDIiXIVSV0prmstKwAjF8pBko9UBRKBkQPlKMk91YAkwBgb5QjJfVWAJMQYE+Uekk8tHmQEjDaKziG2Fgsjl1n0S6zLSH63aJARMVZxOwFA16ViUATAXpLPLDrtzYCRCuUxkg8ueukkI0YsygGSh4ZWfWc9MZwAIxRlH8kjQxj6/9mCTIjhi+KMMVuQAjBcUbwwZglSEMYQygOuw1R7KJvVkFUgxjqUbSR/crlmdMvMBqRgjF6UEIzZDFkNhn7jVvpxA0m9eyX4KL6HzKBnaPD1rhJdWnkxWKI5sWiQ2jCKHrJqxCgWpFaMIkFqxigOpHaMokAM4780q4gsyzD+T5YnBzGMM2cuk4IYxtnTyMlADKN/Tj8JiGGsX2DJDiIiOwC8BmD1+4zY5Z8xzk+2NuXbuKwgDcbLAM73bWjG8pNhZE17DcPtI5WlhxiGG0aWHmIY7hijgxiGH8aoIIbhjzEaiGGEYYwCYhjhGMlBDCMOIymIYcRjJAMxjDQYSUBERJ8z9RWAC9M1a5Sa9Hkmxd9sl2SmLiLbmwXD80YJZVylk65N+TY9GERELgfw2eqxQ4WizAojasgSEf1FkA5TdxaKMjuMYBAR0Z71NYBLm+egl4YyS4wYkGsAnGqNj/q8qVJQZosRA3IQwMOdC1Yfiv6t70H2vtc61/KzxogBeR/A1T1R6qJcC+DNTCizxwgCaeYdP264yW4KlEVghILsBvDcwBiSE2UxGKEgmu7udRjUc6AsCsMbpJPuOphsbQ3Uzr5SXlN0uyGtO/pnZC5vJFcZr5m6iHTTXZd2joGiGPtJ+u7z4dLeScv4gvSluy5vICXKYjFChqx16a4ryh6Sv2thEQkZvhaN4QXikO66oOhDwHRnsxCUxWP4griku2OhVIHhC+Ka7oaiHANwcc/J1WA4gwSkuyEoVwA42UGpCsMHJCTdjUWpDsMHJDTdDUHR7YfeAvAQyaddKlhSGad5iIjEpLsu8epmX8HPm3J5sZLLDIIkSnddYnAGissJSyzjArILwPMjv/lPAWiW9STJz0d+raKrdwFJme6ugvFrk1G9rrcPkfyy6ChlbNxGkMTprm7eqL1AEU6SVBQ7OhEYAolJd/8EoPsEKsAxkjos2TEQgSEQ33T3WwDHm55wguRpE/CLwBDIULqrk7cPW0PRRyR1BwA7AiOwFmRDuqs3OOg+rzoUHSf5feBr22k9EdgE0l7d/aTVC04NbY5okQ6PwCYQ3SPp3CYt/Sb8JexMnwgMzkN8KrOy8REwkPgYJq3BQJKGM74yA4mPYdIaDCRpOOMrM5D4GCat4V8eT/mDX5WgOQAAAABJRU5ErkJggg==');
  width: 35px;
  height: 35px;
  margin:0 auto;
  display: block;
  border: none;
  background-repeat: no-repeat;
  background-position: center;
  background-size: 35px;
  margin-bottom:10px;
}

</style>
