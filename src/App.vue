<template>
  <div>
    <div v-if="$route.name=='login' || $route.name=='reg'">
      <router-view/>
    </div>
    <div v-if="$route.name!='login' && $route.name!='reg'">
      <Header/>
        <div class="ydc-flex">
          <div class="ydc-column2"><Menu/></div>
          <div class="ydc-column8">
            <router-view/>
          </div>
        </div>
      <Footer/>
    </div>
  </div>
</template>

<script>
import Header from '@/components/header.vue'
import Footer from './components/footer.vue'
import Menu from '@/components/menu.vue'
export default {
  name: 'App',
  components: {
    Header, Footer, Menu
  },
  created () {
    if (!localStorage.token) {
      this.$router.push('/login')
    }
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
    padding: 0 10px;
  }
  .ydc-column8 {
    flex: 0 0 79.16667%;
  }
</style>
