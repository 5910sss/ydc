<template>
  <div>
    <Header/>
      <div class="ydc-flex">
        <div class="ydc-column2">12112</div>
        <div class="ydc-column8">
          <router-view/>
        </div>
      </div>
    <Footer/>
  </div>
</template>

<script>
import Header from '@/components/header.vue'
import Footer from './components/footer.vue'
export default {
  name: 'App',
  components: {
    Header, Footer
  }
}
</script>

<style scoped>
  .ydc-flex{
    display: flex;
    width:1180px;
    margin:20px auto;
  }
  .ydc-column2 {
    flex: 0 0 20.83333%;
  }
  .ydc-column8 {
    flex: 0 0 79.16667%;
  }
</style>
